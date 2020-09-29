---
title: Создание расширения Jupyter Notebook
description: Узнайте, как упаковать записные книжки в расширение с помощью генератора расширений.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.reviewer: alayu, maghan
ms.custom: ''
ms.date: 08/28/2020
ms.openlocfilehash: e2996b583cd1005e26e4334c9934fff79c321ee4
ms.sourcegitcommit: 63aef5a96905f0b026322abc9ccb862ee497eebe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2020
ms.locfileid: "91364051"
---
# <a name="create-a-jupyter-notebook-extension"></a>Создание расширения Jupyter Notebook

В этом руководстве показано, как создать расширение Jupyter Notebook в Azure Data Studio. Расширение поставляет пример Jupyter Notebook, который можно открыть и запустить в Azure Data Studio.

В этой статье раскрываются следующие темы:

> [!div class="checklist"]
> - Создание проекта расширения.
> - Установка генератора расширений.
> - Создание расширения записных книжек.
> - Запуск расширения.
> - Упакуйте расширение.
> - Опубликуйте расширение в Marketplace.

## <a name="apis-used"></a>Используемые API

- `azdata.nb.showNotebookDocument`

### <a name="extension-use-cases"></a>Варианты использования расширения

Есть несколько причин, чтобы создать расширение записных книжек:
- совместное использование интерактивной документации;
- сохранение этой записной книжки и постоянный доступ к ней;
- предоставление пользователям информации о проблемах написания кода;
- управление версиями и отслеживание обновлений записных книжек.

## <a name="prerequisites"></a>Предварительные требования

Средство Azure Data Studio основано на той же платформе, что и Visual Studio Code, поэтому расширения для Azure Data Studio создаются с помощью Visual Studio Code. Чтобы приступить к работе, вам потребуются следующие компоненты.

- Установленный [Node.js](https://nodejs.org), доступный в вашей переменной `$PATH`. Node.js включает в себя [npm](https://www.npmjs.com/), диспетчер пакетов Node.js, который будет использоваться для установки генератора расширений.
- [Visual Studio Code](https://code.visualstudio.com) для отладки расширения.
- Убедитесь, что `azuredatastudio` указан в вашем пути. Для Windows выберите параметр **Добавить в PATH** в setup.exe. Для Mac или Linux выберите параметр **Установить путь к команде azuredatastudio в PATH**.

## <a name="install-the-extension-generator"></a>Установка генератора расширений

Чтобы упростить процесс создания расширений, мы создали [генератор расширений](https://www.npmjs.com/package/generator-azuredatastudio) с помощью Yeoman. Для его установки выполните следующую команду в командной строке:

```console
`npm install -g yo generator-azuredatastudio`
```

## <a name="create-your-extension"></a>Создание расширения

Для создания расширения сделайте следующее.

1. Запустите генератор расширений с помощью следующей команды:

   `yo azuredatastudio`

2. Выберите **Новые записные книжки (отдельные)** в списке типов расширений.

   :::image type="content" source="media/notebook-extension/notebook-extension-generator.png" alt-text="Генератор расширений записных книжек":::

3. Выполните инструкции, чтобы ввести имя расширения. Мы будем использовать имя **Test Notebook**. Затем введите имя издателя. Здесь мы используем имя **Microsoft**. В последнюю очередь добавьте описание.

Теперь здесь есть несколько ветвей. Можно добавить уже созданные записные книжки Jupyter Notebook или использовать образцы записных книжек, предоставленные в генераторе.

В этом учебнике мы будем использовать пример записной книжки Python:

   :::image type="content" source="media/notebook-extension/notebook-sample-generator.png" alt-text="Генератор расширений записных книжек":::

Если у вас есть записные книжки, которые вы хотите отправить, укажите это в ответе. Укажите абсолютный путь к файлу, где находятся все записные книжки или файлы Markdown.

При выполнении предыдущих шагов создается папка с примером записной книжки. Откройте ее в Visual Studio Code, чтобы предоставить расширение записных книжек.

## <a name="understand-your-extension"></a>Изучение расширения

В настоящее время ваш проект должен выглядеть следующим образом:

   :::image type="content" source="media/notebook-extension/notebook-file-structure-generator.png" alt-text="Генератор расширений записных книжек":::

Файл `vsc-extension-quickstart.md` предоставляет ссылку на важные файлы. В файле `README.md` можно предоставить документацию для нового расширения. Обратите внимание на файлы `package.json`, `notebook.ts` и `pySample.ipynb`.

Если у вас есть файлы или папки, которые не нужно публиковать, включите их имена в файл `.vscodeignore`.

Давайте взглянем на `notebook.ts`, чтобы понять, что делает новое расширение.

```javascript
// This function is called when you run the command `Launch Notebooks: Test Notebook` from the
// command palette in Azure Data Studio. If you want any additional functionality
// to occur when you launch the book, add it to the activate function.
export function activate(context: vscode.ExtensionContext) {
    context.subscriptions.push(vscode.commands.registerCommand('launchNotebooks.test-notebook', () => {
        let notebooksToDisplay: Array<string> = processNotebooks();
        notebooksToDisplay.forEach(name => {
            azdata.nb.showNotebookDocument(vscode.Uri.file(name));
        });
    }));

    // Add other code here if you want to register another command.
}
```

Это главная функция в `notebook.ts`, которая вызывается при каждом запуске расширения с помощью команды **Запуск записных книжек: Test Notebook**. Мы создаем новую команду с помощью API `vscode.commands.registerCommand`. Следующее определение внутри фигурных скобок — это код, который выполняется при каждом вызове команды. Каждую записную книжку, найденную функцией `processNotebooks`, можно открыть в Azure Data Studio с помощью `azdata.nb.showNotebookDocument`.

Файл `package.json` также играет важную роль при регистрации команды **"Запуск записных книжек": Test Notebook**.

```json
"activationEvents": [
        "onCommand:launchNotebooks.test-notebook"
    ],
    "main": "./out/notebook.js",
    "contributes": {
        "commands": [
            {
                "command": "launchNotebooks.test-notebook",
                "title": "Launch Notebooks: Test Notebook"
            }
        ]
    }
```

У нас есть событие активации для команды, и мы добавили определенные точки вклада. Они отображаются в разделе вашего расширения в Marketplace, где публикуются расширения. Если вы хотите добавить дополнительные команды, укажите их в поле `activationEvents`. Дополнительные параметры см. в разделе [События активации](https://code.visualstudio.com/api/references/activation-events).

## <a name="package-your-extension"></a>Упаковка расширения

Чтобы предоставить общий доступ другим пользователям, нужно упаковать расширение в один файл. Его можно опубликовать в магазине Marketplace расширений Azure Data Studio или предоставить для общего доступа другим участникам команды или сообщества. Для этого нужно установить другой пакет npm из командной строки.

```console
`npm install -g vsce`
```

Внесите в файл `README.md` желаемые изменения. Затем перейдите к базовому каталогу расширения и выполните команду `vsce package`. При необходимости можно связать репозиторий с расширением или продолжить работу без него. Чтобы добавить его, добавьте аналогичную строку в файл `package.json`.

```json
"repository": {
    "type": "git",
    "url": "https://github.com/laurajjiang/testnotebook.git"
}
```

После добавления этих строк создается файл `my test-notebook-0.0.1.vsix`, готовый для установки и публикации.

## <a name="run-your-extension"></a>Запуск расширения

Чтобы запустить и проверить расширение, перейдите в Azure Data Studio и откройте палитру команд, нажав клавиши **Ctrl+Shift+P**. Найдите команду **Расширения: установка из VSIX** и перейдите к папке, содержащей новое расширение.

   :::image type="content" source="media/notebook-extension/install-vsix.png" alt-text="Генератор расширений записных книжек":::

Расширение должно отображаться на панели расширения в Azure Data Studio. Снова откройте палитру команд, и вы увидите новую команду, созданную с помощью нашего расширения, **Запуск книги: Test Book**. После запуска откроется книга Jupyter Book, упакованная с нашим расширением.

   :::image type="content" source="media/notebook-extension/notebook-launch-ads.png" alt-text="Генератор расширений записных книжек":::

Поздравляем! Вы создали свое первое расширение Jupyter Notebook и теперь можете предоставить его.

## <a name="publish-your-extension-to-the-marketplace"></a>Публикация расширения в Marketplace

Магазин Marketplace расширений Azure Data Studio пока находится в стадии разработки. Для публикации разместите VSIX-файл расширения в любом расположении, например на странице выпуска GitHub. Затем следует отправить запрос на вытягивание, который обновляет [этот JSON-файл](https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json), добавляя в него сведения о расширении.

## <a name="next-steps"></a>Дальнейшие действия

В этом руководстве вы узнали, как выполнять следующие задачи:
> [!div class="checklist"]
> - Создание проекта расширения.
> - Установка генератора расширений.
> - Создание расширения записных книжек.
> - Создание расширения.
> - Упаковка расширения.
> - Публикация расширения в Marketplace.

Мы надеемся, что после ознакомления с этой статьей вы захотите создать собственное расширение для Azure Data Studio.

Если у вас появилась идея, но вы не знаете, с чего начать, откройте вопрос или отправьте твит нашей команде: [azuredatastudio](https://twitter.com/azuredatastudio).

Для получения дополнительных сведений можно обратиться к [руководству по расширениям Visual Studio Code](https://code.visualstudio.com/docs/extensions/overview), которое охватывает все существующие API и шаблоны.