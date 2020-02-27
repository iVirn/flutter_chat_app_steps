#### Шаг 3. Добавляем главный экран с пирами. 
1. Добавляем `onGenerateRoute` в `app.dart`: 
```
...
home: pageRoutes.buildPage(AppPageName.login, null),
==========
onGenerateRoute: (RouteSettings settings) => MaterialPageRoute<Object>(
          builder: (BuildContext context) =>
              pageRoutes.buildPage(settings.name, settings.arguments),
        ),
==========
```
2. Добавляем адрес идентификатор страницы и создаём экземпляр в `app_routes.dart`: 
```
class AppPageName {
  static const sample = 'sample';
  static const login = 'login';
  static const main = 'main'; <----------

// Объявляем и создаём возможные страницы в приложении, матчим с названиями
final pageRoutes = PageRoutes(
  pages: {
    AppPageName.sample: SamplePage(),
    AppPageName.login: LoginPage(),
    AppPageName.main: MainPage(), <----------
  },
}
```
3. Добавляем модель Peer: [link](https://github.com/iVirn/flutter_chat_app_steps/blob/master/3.%20Add%20Main%20Page/models/user.dart);
4. Добавляем экшен `onPushMainPage` в `LoginAction`;
5. Эффект к новому экшену, а диспатчим его в эффекте логина.
6. Добавляем Main Page: [link](https://github.com/iVirn/flutter_chat_app_steps/tree/master/3.%20Add%20Main%20Page/main_page).

#### [Далее к шагу 4](https://github.com/iVirn/flutter_chat_app_steps/tree/master/4.%20Add%20Chat%20Page/readme.md)