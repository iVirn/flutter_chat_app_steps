#### Шаг 1
1. Добавляем global base state: [link](https://github.com/iVirn/flutter_chat_app_steps/tree/master/1.%20Add%20Global%20State/global_state)
2. Удаляем `pageRoutes` из `app.dart`;
3. Добавляем `pageRoutes` с `visitor` и логгером в `app_routes.dart`: 
```
// Объявляем и создаём возможные страницы в приложении, матчим с названиями
final pageRoutes = PageRoutes(
  pages: {
    AppPageName.sample: SamplePage(),
  },
  visitor: (String path, Page<Object, dynamic> page) {
    if (page.isTypeof<GlobalBaseState>()) {
      page.connectExtraStore<GlobalState>(
        GlobalStore.store,
        (Object pagestate, GlobalState appState) {
          final GlobalBaseState p = pagestate;
          if (p.user != appState.user) {
            if (pagestate is Cloneable) {
              final Object copy = pagestate.clone();
              final GlobalBaseState newState = copy;
              newState.user = appState.user;
              return newState;
            }
          }
          return pagestate;
        },
      );
    }
    page.enhancer.append(
      /// Effect AOP
      effectMiddleware: [
        _pageAnalyticsMiddleware<dynamic>(),
      ],

      /// Store AOP
      middleware: <Middleware<dynamic>>[
        logMiddleware<dynamic>(tag: page.runtimeType.toString()),
      ],
    );
  },
);

EffectMiddleware<T> _pageAnalyticsMiddleware<T>({String tag = 'redux'}) {
  return (AbstractLogic<dynamic> logic, Store<T> store) {
    return (Effect<dynamic> effect) {
      return (Action action, Context<dynamic> ctx) {
        if (logic is Page<dynamic, dynamic>) {
          print('${logic.runtimeType} ${action.type.toString()} ');
        }
        return effect?.call(action, ctx);
      };
    };
  };
}
```

#### [Далее к шагу 2](https://github.com/iVirn/flutter_chat_app_steps/blob/master/2.%20Add%20Login/readme.md)