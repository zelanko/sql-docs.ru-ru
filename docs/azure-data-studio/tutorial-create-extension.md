---
title: Руководство По созданию расширения для студии данных Azure | Документация Майкрософт
description: Этот учебник демонстрирует создание расширения для Azure Data Studio.
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: tutorial
author: kevcunnane
ms.author: kcunnane
manager: craigg
ms.openlocfilehash: ae1605f1c99e4fa2a74c7f728f191baf5a8b9bf8
ms.sourcegitcommit: 35e4c71bfbf2c330a9688f95de784ce9ca5d7547
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356555"
---
# <a name="tutorial-create-an-azure-data-studio-extension"></a>Руководство По созданию расширения Studio данных Azure

Этот учебник демонстрирует создание нового расширения Studio данных Azure. Модуль создает знакомы сочетания клавиш SSMS в Azure Data Studio.

С помощью этого учебника вы узнаете, как:
> [!div class="checklist"]
> * Создайте проект расширения
> * Установите генератор расширения
> * Создать расширения
> * Протестируйте расширение
> * Пакет расширения
> * Публикация расширения в marketplace

## <a name="prerequisites"></a>предварительные требования

Azure Data Studio лежит та же платформа, как Visual Studio Code, чтобы расширения для Azure Data Studio строятся с использованием Visual Studio Code. Чтобы начать работу, необходимы следующие компоненты:

- [Node.js](https://nodejs.org) установлена и доступна в вашей `$PATH`. Node.js включает [npm](https://www.npmjs.com/), диспетчер пакетов Node.js, который используется для установки расширения генератора.
- [Visual Studio Code](https://code.visualstudio.com) отладка расширения.
- Azure Data Studio [отладка расширение](https://marketplace.visualstudio.com/items?itemName=ms-mssql.sqlops-debug).
- Убедитесь, что sqlops указан в пути. Для Windows, убедитесь, что `Add to Path` параметр в setup.exe. Для Mac или Linux, выполните *установить команду «sqlops» в пути* параметр.
- Отладка SQL Operations Studio расширение (необязательно). Это позволяет протестировать свое расширение без необходимости пакет и установите его в студию данных Azure.


## <a name="install-the-extension-generator"></a>Установите генератор расширения

Чтобы упростить процесс создания расширения, мы создали [генератор расширения](https://code.visualstudio.com/docs/extensions/yocode) с помощью Yeoman. Чтобы установить его, выполните следующую команду из командной строки:

`npm install -g yo generator-sqlops`

## <a name="create-your-extension"></a>Создать расширения

Для создания расширения:

1. Запустите генератор расширения с помощью следующей команды:

   `yo sqlops`

2. Выберите **новых клавиатурах** из списка типов расширений:

   ![расширение генератора](./media/tutorial-create-extension/extension-generator.png)

3. Выполните действия, чтобы заполнить имя расширения (в этом руководстве используйте **ssmskeymap**) и добавьте описание.

Завершения предыдущих шагов создана новая папка. Откройте папку, в Visual Studio Code и вы готовы создать свое собственное расширение сочетание клавиш.


### <a name="add-a-keyboard-shortcut"></a>Добавить сочетание клавиш

**Шаг 1: Поиск сочетания клавиш для замены**

Теперь, когда у нас есть расширения готова к работе, добавьте некоторые SSMS сочетания клавиш (или сочетания клавиш) в студию данных Azure. Я использовал [Памятка Энди Mallon](https://am2.co/2018/02/updated-cheat-sheet/) и RedGate списка клавиш клавиатуры для вдохновения.

Были главных достоинств, я увидел, что отсутствует:

- Выполните запрос с фактический план выполнения включен. Это **Ctrl + M** в среде SSMS и не имеет привязки в студии данных Azure.
- Наличие **CTRL + SHIFT + E** как второй способ выполнения запроса. Отзывы пользователей указано, что это отсутствует.
- Наличие **ALT + F1** запуска `sp_help`. Мы добавили в Azure Data Studio, но так как эта привязка уже использовался ранее, мы его сопоставления для **ALT + F2** вместо этого.
- Переключиться в полноэкранный режим (**SHIFT + ALT + ВВОД**).
- **F8** Показать **обозревателя объектов** / **представление серверы**.

Его можно легко найти и заменить эти сочетания клавиш. Запустите *откройте сочетания клавиш* Показать **сочетания клавиш** вкладке студии данных Azure, поиск *запроса* и нажмите кнопку **сочетание клавиш изменения**. После завершения изменения сочетание клавиш вы сможете просмотреть обновленного сопоставления в файле keybindings.json (запустите *откройте сочетания клавиш* чтобы увидеть ее).

![сочетания клавиш](./media/tutorial-create-extension/keyboard-shortcuts.png)

![расширение keybindings.JSON](./media/tutorial-create-extension/keybindings-json.png)


**Шаг 2: Добавление ярлыков в расширение**

Чтобы добавить ярлыки в расширение, откройте *package.json* (в расширении) и заменить `contributes` раздел со следующими:

```json
"contributes": {
  "keybindings": [
    {
      "key": "shift+cmd+e",
      "command": "runQueryKeyboardAction"
    },
    {
      "key": "ctrl+cmd+e",
      "command": "workbench.view.explorer"
    },
    {
      "key": "alt+f1",
      "command": "workbench.action.query.shortcut1"
    },
    {
      "key": "shift+alt+enter",
      "command": "workbench.action.toggleFullScreen"
    },
    {
      "key": "f8",
      "command": "workbench.view.connections"
    },
    {
      "key": "ctrl+m",
      "command": "runCurrentQueryWithActualPlanKeyboardAction"
    }
  ]
}
```

## <a name="test-your-extension"></a>Протестируйте расширение

Убедитесь, `azuredatastudio` указан в пути с помощью команды установки azuredatastudio в путь к команде в студии данных Azure.

Убедитесь, что установлено расширение Azure данных Studio отладку в Visual Studio Code.

Выберите **F5** для запуска Azure данных Studio в режиме отладки с расширением запущено:

![Установка расширения](./media/tutorial-create-extension/install-extension.png)

![расширение теста](./media/tutorial-create-extension/test-extension.png)

Keymaps являются одним из самых быстрых расширений для создания, поэтому новое расширение должно равняться успешно работает и готов к публикации.

## <a name="package-your-extension"></a>Пакет расширения

Для совместного использования с другими пользователями, необходимо упаковать расширение в один файл. Это можно опубликовать в marketplace Azure Data Studio расширение или просто совместно вашей команды или сообщества. Чтобы сделать это, необходимо установить другой пакет npm из командной строки:

`npm install -g vsce`

Перейдите к базовому каталогу, расширения и запустите `vsce package`. Мне пришлось добавить несколько дополнительных строк, чтобы остановить *vsce* средство с жалобой на:

```json
"repository": {
    "type": "git",
    "url": "https://github.com/kevcunnane/ssmskeymap.git"
},
"bugs": {
    "url": "https://github.com/kevcunnane/ssmskeymap/issues"
},
```

Когда это было сделано, мой файл ssmskeymap 0.1.0.vsix был создан и готов к установке и со всего мира!

![Установка расширения](./media/tutorial-create-extension/extensions.png)


## <a name="publish-your-extension-to-the-marketplace"></a>Публикация расширения в marketplace

В Azure Data Studio расширение marketplace еще не реализован полностью, но текущий процесс для размещения расширение VSIX где-нибудь (например, страница, выпуск GitHub) отправьте запрос на Вытягивание идет обновление [этот JSON-файл](https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json) с вашей Информация о расширении.


## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы узнали, как:
> [!div class="checklist"]
> * Создайте проект расширения
> * Установите генератор расширения
> * Создать расширения
> * Протестируйте расширение
> * Пакет расширения
> * Публикация расширения в marketplace


Мы надеемся, что после прочтения этого вы сможете вдохновлены на создание собственное расширение для Azure Data Studio. У нас есть поддержка восприятие информационной панели (довольно графы, выполняемых к серверу SQL Server), ряд API-интерфейсам конкретной SQL и огромным существующий набор точек расширения, унаследованные от Visual Studio Code.

Если вы поняли, но не уверены, как приступить к работе, создайте службу информацию о проблеме или твита в группе: [azuredatastudio](https://twitter.com/azuredatastudio).

Вы всегда можете обратиться к [руководстве по расширению Visual Studio Code](https://code.visualstudio.com/docs/extensions/overview) так как он охватывает все существующие API-интерфейсы и шаблоны.


Дополнительные сведения о работе с T-SQL в Azure Data Studio, работы с руководством редактор T-SQL:

> [!div class="nextstepaction"]
> [Используйте редактор Transact-SQL для создания объектов базы данных](tutorial-sql-editor.md).
