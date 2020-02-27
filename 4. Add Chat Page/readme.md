#### Шаг 4
1. Как и раньше — добавляем новый айди и экземпляр страницы в `app_routes`;
2. Модель `Message`: [link](https://github.com/iVirn/flutter_chat_app_steps/blob/master/4.%20Add%20Chat%20Page/models/message.dart);
3. Виджет `MessageItem`: [link](https://github.com/iVirn/flutter_chat_app_steps/blob/master/4.%20Add%20Chat%20Page/chat_page/ui/message_item.dart);
4. Прописываем в эффекте `MainPage` `_onOpenChat`: 
```
final peer = action.payload as Peer;
  print(peer?.nickname);

  Navigator.of(ctx.context)
      .pushNamed(AppPageName.chat, arguments: {'peer': peer});
```
5. Диспатчим экшен в `onTap` `MainPage` view: 
```
onTap: () =>
              dispatch(MainActionCreator.onOpenChat(state.peers[index])),
```
6. Добавляем ChatPage: [link](https://github.com/iVirn/flutter_chat_app_steps/tree/master/4.%20Add%20Chat%20Page).