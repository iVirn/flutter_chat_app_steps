

#### Шаг 2. Добавляем логин. 
1. Обновляем app_routes.dart — указываем id новой страницы Login: 
```
class AppPageName {
  static const sample = 'sample';
  static const login = 'login'; <----------
}

// Объявляем и создаём возможные страницы в приложении, матчим с названиями
final pageRoutes = PageRoutes(
  pages: {
    AppPageName.sample: SamplePage(),
    AppPageName.login: LoginPage(), <----------
  },

...
```
2. Обновляем app.dart — указываем новую страницу как корень: 
```
home: pageRoutes.buildPage(AppPageName.login, null),
```
3. Добавляем login page — вью, экшены, вот это всё: [link](https://github.com/iVirn/flutter_chat_app_steps/tree/master/2.%20Add%20Login/login_page).

#### [Далее к шагу 3](https://github.com/iVirn/flutter_chat_app_steps/tree/master/3.%20Add%20Main%20Page/readme.md)