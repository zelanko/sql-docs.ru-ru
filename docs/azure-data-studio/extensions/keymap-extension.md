---
title: Создание расширения раскладки клавиатуры
description: В этом учебнике показано, как создать расширение раскладки клавиатуры, чтобы добавить пользовательские функции для Azure Data Studio.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: how-to
author: markingmyname
ms.author: maghan
ms.reviewer: alayu
ms.custom: ''
ms.date: 08/28/2020
ms.openlocfilehash: b1e1b5fb4d21e153133e76ff612f54c8153e0772
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91111658"
---
# <a name="create-an-azure-data-studio-keymap-extension"></a>Создание расширения раскладки клавиатуры Azure Data Studio

В этом руководстве показано, как создать расширение Azure Data Studio. Расширение создает знакомые настраиваемые сочетания клавиш SSMS в Azure Data Studio.

В этом руководстве вы узнаете, как выполнять следующие задачи.
> [!div class="checklist"]
> - Создание проекта расширения
> - Установка генератора расширений
> - Создание расширения
> - Добавление пользовательских привязок клавиш в расширение
> - Тестирование расширения
> - Упаковка расширения
> - Публикация расширения в Marketplace

## <a name="prerequisites"></a>Предварительные требования

Средство Azure Data Studio основано на той же платформе, что и Visual Studio Code, поэтому расширения для Azure Data Studio создаются с помощью Visual Studio Code. Чтобы приступить к работе, вам потребуются следующие компоненты.

- Установленный [Node.js](https://nodejs.org), доступный в вашей переменной `$PATH`. Node.js включает в себя [npm](https://www.npmjs.com/), диспетчер пакетов Node.js, который будет использоваться для установки генератора расширений.
- [Visual Studio Code](https://code.visualstudio.com) для отладки расширения.
- [Расширение отладки](https://marketplace.visualstudio.com/items?itemName=ms-mssql.sqlops-debug) Azure Data Studio (необязательно). Оно позволяет протестировать расширение без необходимости упаковывать и устанавливать его в Azure Data Studio.
- Убедитесь, что `azuredatastudio` указан в вашем пути. Для Windows выберите параметр `Add to Path` в setup.exe. Для Mac или Linux выберите параметр *Установить путь к команде azuredatastudio в PATH*.

## <a name="install-the-extension-generator"></a>Установка генератора расширений

Чтобы упростить процесс создания расширений, мы создали [генератор расширений](https://code.visualstudio.com/docs/extensions/yocode) с помощью Yeoman. Для его установки выполните следующую команду в командной строке.

```console
`npm install -g yo generator-azuredatastudio`
```

## <a name="create-your-keymap-extension"></a>Создание расширения раскладки клавиатуры

Для создания расширения сделайте следующее.

1. Запустите генератор расширений с помощью следующей команды.

   `yo azuredatastudio`

2. Выберите **Новое сопоставление клавиш** в списке типов расширений:

   :::image type="content" source="media/keymap-extension/extension-generator.png" alt-text="Генератор расширений":::

3. Выполните инструкции по заполнению имени расширения (в этом руководстве используйте **ssmskeymap2**) и добавьте описание.

При выполнении предыдущих шагов создается папка. Откройте ее в Visual Studio Code, после чего вы сможете создать собственное расширение настраиваемых сочетаний клавиш.

### <a name="add-a-keyboard-shortcut"></a>Добавление сочетания клавиш

**Шаг 1. Поиск сочетаний клавиш для замены**

Теперь, когда наше расширение готово к работе, добавьте несколько сочетаний клавиш SSMS (или настраиваемых сочетаний клавиш) в Azure Data Studio. В качестве примера использовались [памятка Энди Мэллона (Andy Mallon)](https://am2.co/2018/02/updated-cheat-sheet/) и список сочетаний клавиш RedGate.

Основные элементы, которых, на мой взгляд, не хватало.

- Выполнение запроса с включенным действительным планом выполнения. Для этого в SSMS используется сочетание клавиш **CTRL+M**, а в Azure Data Studio соответствующее сочетание отсутствует.
- Использование сочетания клавиш **CTRL+SHIFT+E** в качестве второго способа запуска запроса. Отзывы пользователей указывали, что этот элемент отсутствовал.
- Использование **ALT+F1** для выполнения `sp_help`. Мы добавили его в Azure Data Studio, но, так как это настраиваемое сочетание уже используется, мы назначили вместо этого **ALT+F2**.
- Переключение в полноэкранный режим (**SHIFT+ALT+ВВОД**).
- **F8** для отображения **Обозреватель объектов** / **Представление серверов**.

Эти настраиваемые сочетания клавиш можно легко найти и заменить. Выберите *Открыть сочетания клавиш*, чтобы отобразить вкладку **Сочетания клавиш** в Azure Data Studio, выполните поиск строки *запрос* и выберите **Изменить настраиваемое сочетание клавиш**. Закончив изменять настраиваемое сочетание клавиш, вы можете просмотреть обновленное сочетание в файле keybindings.json (чтобы увидеть его, выберите *Открыть сочетания клавиш*).

:::image type="content" source="media/keymap-extension/keyboard-shortcuts.png" alt-text="сочетанием клавиш":::;

:::image type="content" source="media/keymap-extension/key-bindings-json.png" alt-text="Расширение Keybindings.json":::

**Шаг 2. Добавление сочетаний клавиш в расширение**

Чтобы добавить сочетания клавиш в расширение, откройте файл *package.json* (в расширении) и замените раздел `contributes` следующим кодом.

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

## <a name="test-your-extension"></a>Тестирование расширения

Убедитесь, что `azuredatastudio` указан в вашей переменной PATH, выполнив команду "Установить путь к команде azuredatastudio в PATH" в Azure Data Studio.

Убедитесь, что в Visual Studio Code установлено расширение отладки Azure Data Studio.

Нажмите клавишу **F5**, чтобы запустить Azure Data Studio в режиме отладки с запущенным расширением.

:::image type="content" source="media/keymap-extension/install-extension.png" alt-text="Установка расширения":::

:::image type="content" source="media/keymap-extension/test-extension.png" alt-text="тестирование расширения":::

Сочетания клавиш — это одно из самых быстрых для создания расширений, поэтому ваше новое расширение должно работать и быть готовым к совместному использованию.

## <a name="package-your-extension"></a>Упаковка расширения

Чтобы предоставить общий доступ другим пользователям, нужно упаковать расширение в один файл. Его можно опубликовать в магазине расширений Azure Data Studio или предоставить для общего доступа другим участникам команды или сообщества. Для этого нужно установить другой пакет npm из командной строки.

```console
`npm install -g vsce`
```

Перейдите к базовому каталогу расширения и выполните команду `vsce package`. Мне пришлось добавить несколько дополнительных строк кода, чтобы средство *vsce* перестало выдавать предупреждения.

```json
"repository": {
    "type": "git",
    "url": "https://github.com/kevcunnane/ssmskeymap.git"
},
"bugs": {
    "url": "https://github.com/kevcunnane/ssmskeymap/issues"
},
```

После этого был создан файл ssmskeymap-0.1.0.vsix, готовый к установке и совместному использованию.

:::image type="content" source="media/keymap-extension/extensions.png" alt-text="Установка":::

## <a name="publish-your-extension-to-the-marketplace"></a>Публикация расширения в Marketplace

Магазин расширений Azure Data Studio пока реализован не полностью, но текущая процедура заключается в размещении VSIX расширения где-либо (например, на странице выпуска GitHub) и последующей отправке запроса на вытягивание для обновления [этого JSON-файла](https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json) с использованием сведений о расширении.

## <a name="next-steps"></a>Дальнейшие действия

В этом руководстве вы узнали, как выполнять следующие задачи:
> [!div class="checklist"]
> - Создание проекта расширения
> - Установка генератора расширений
> - Создание расширения
> - Добавление пользовательских привязок клавиш в расширение
> - Тестирование расширения
> - Упаковка расширения
> - Публикация расширения в Marketplace

Мы надеемся, что после ознакомления с этим материалом вы захотите создать собственное расширение для Azure Data Studio. Мы обеспечиваем поддержку Dashboard Insights (симпатичное графическое решение, предназначенное для SQL Server), нескольких SQL-ориентированных API, а также обширного набора точек расширений, унаследованных от Visual Studio Code.

Если у вас появилась идея, но вы не знаете, с чего начать, откройте вопрос или отправьте твит нашей команде: [azuredatastudio](https://twitter.com/azuredatastudio).

Вы всегда можете обратиться к [руководству по расширениям Visual Studio Code](https://code.visualstudio.com/docs/extensions/overview), так как оно охватывает все существующие API и шаблоны.

Чтобы узнать, как работать с T-SQL в Azure Data Studio, изучите руководство по редактору T-SQL:

> [!div class="nextstepaction"]
> [Создание объектов базы данных с помощью редактора Transact-SQL](../tutorial-sql-editor.md)
