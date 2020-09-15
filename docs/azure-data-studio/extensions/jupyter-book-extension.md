---
title: Создание расширения Jupyter Book
description: Узнайте, как упаковать Jupyter Book в расширение с помощью генератора расширений.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: how-to
author: yualan
ms.author: alayu
ms.reviewer: alayu, maghan
ms.custom: ''
ms.date: 08/28/2020
ms.openlocfilehash: af6cb013109d5d871c709f72cf5a564ae69940cb
ms.sourcegitcommit: b6ee0d434b3e42384b5d94f1585731fd7d0eff6f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "89288176"
---
# <a name="create-a-jupyter-book-extension"></a>Создание расширения Jupyter Book

В этом руководстве показано, как создать расширение Jupyter Book в Azure Data Studio. Расширение поставляет пример Jupyter Book, который можно открыть и запустить в Azure Data Studio. 

В этом руководстве вы узнаете, как выполнять следующие задачи.
> [!div class="checklist"]
> - Создание проекта расширения
> - Установка генератора расширений
> - Создание расширения Jupyter Book
> - Запуск расширения
> - Упаковка расширения
> - Публикация расширения в Marketplace

## <a name="apis-used"></a>Используемые API

- `bookTreeView.openBook`

### <a name="extension-use-cases"></a>Варианты использования расширения

Есть несколько причин, чтобы создать расширение Jupyter Book:

- совместное использование упорядоченной и разбитой на разделы интерактивной документации;
- совместное использование полной книги (аналогично электронной книге, но с распределением по Azure Data Studio);
- управление версиями и отслеживание обновлений Jupyter Book.

Основное различие между Jupyter Book и расширением записной книжки состоит в том, что Jupyter Book предоставляет организацию. Десятки записных книжек можно разделить на разные главы в книге, но расширение записных книжек предназначено для доставки небольшого количества отдельных записных книжек.

## <a name="prerequisites"></a>Предварительные требования

Средство Azure Data Studio основано на той же платформе, что и Visual Studio Code, поэтому расширения для Azure Data Studio создаются с помощью Visual Studio Code. Чтобы приступить к работе, вам потребуются следующие компоненты.

- Установленный [Node.js](https://nodejs.org), доступный в вашей переменной `$PATH`. Node.js включает в себя [npm](https://www.npmjs.com/), диспетчер пакетов Node.js, который будет использоваться для установки генератора расширений.
- [Visual Studio Code](https://code.visualstudio.com) для внесения изменений в расширение и отладки расширения.
- Убедитесь, что `azuredatastudio` указан в вашем пути. Для Windows выберите параметр `Add to Path` в setup.exe. Для Mac или Linux выберите параметр *Установить путь к команде azuredatastudio в PATH*.

## <a name="install-the-extension-generator"></a>Установка генератора расширений

Чтобы упростить процесс создания расширений, мы создали [генератор расширений](https://www.npmjs.com/package/generator-azuredatastudio) с помощью Yeoman. Для его установки выполните следующую команду в командной строке:

```console
`npm install -g yo generator-azuredatastudio`
```

## <a name="create-your-extension"></a>Создание расширения

Для создания расширения сделайте следующее.

1. Запустите генератор расширений с помощью следующей команды.

   `yo azuredatastudio`

2. Выберите **Создать Jupyter Book** в списке типов расширений:

   :::image type="content" source="media/jupyter-book-extension/jupyter-book-extension-generator.png" alt-text="Генератор расширений":::

3. Следуйте инструкциям, чтобы указать имя расширения (в этом учебнике используйте **Test Book**), имя издателя (в этом учебнике — **Microsoft**) и описание.

Вы хотите предоставить существующую книгу Jupyter Book, использовать предоставленный образец книги или создать новую книгу Jupyter Book. Все три варианта описаны ниже.

### <a name="providing-an-existing-book"></a>Предоставление существующей книги

Если вы хотите предоставить уже созданную книгу, укажите абсолютный путь к папке, в которой находится содержимое вашей книги. После этого вы сможете перейти к изучению расширения и его отправке.

:::image type="content" source="media/jupyter-book-extension/jupyter-book-existing-book.png" alt-text="Существующая книга":::

### <a name="using-the-sample-book"></a>Использование образца книги

Если у вас нет книги или записных книжек, можно использовать предоставленный образец в генераторе.

:::image type="content" source="media/jupyter-book-extension/jupyter-book-sample-path.png" alt-text="Образец книги Jupyter":::

В образце книги показано, как выглядит простая книга Jupyter Book. Если вы хотите узнать о настройке книги Jupyter Book, см. следующий раздел о создании новой книги с существующими записными книжками.

### <a name="creating-a-new-book"></a>Создание новой книги

Если у вас есть записные книжки, которые вы хотите упаковать в книгу Jupyter Book, вы можете это сделать. Генератор спрашивает, должны ли в книге быть главы и, если да, сколько их будет и как они будут называться. Ниже показано, как выглядит процесс выбора. С помощью клавиши пробела выберите, какие записные книжки нужно поместить в каждую главу.

:::image type="content" source="media/jupyter-book-extension/jupyter-book-create-book.png" alt-text="Создание книги Jupyter":::

При выполнении предыдущих шагов создается папка с новой книгой Jupyter Book. Откройте ее в Visual Studio Code, чтобы предоставить расширение Jupyter Book.

## <a name="understanding-your-extension"></a>Изучение расширения

В настоящее время ваш проект должен выглядеть следующим образом:

   :::image type="content" source="media/jupyter-book-extension/jupyter-book-file-structure-generator.png" alt-text="Структура файла расширения":::

`vsc-extension-quickstart.md` предоставляет ссылку на важные файлы. В `README.md` можно предоставить документацию для нового расширения. Обратите внимание на файлы `package.json`, `jupyter-book.ts`, `content` и `toc.yml`. Папка `content` содержит все файлы записных книжек или Markdown. `toc.yml` структурирует книгу Jupyter Book и формируется автоматически, если вы решили создать настраиваемую книгу Jupyter Book с помощью генератора расширений.

Если вы создали книгу с помощью генератора и выбрали главы в книге, структура папок будет выглядеть немного иначе. Вместо файлов Markdown и Jupyter Notebook, которые находятся в папке `content`, у вас будут вложенные папки, соответствующие заголовкам, выбранным для глав. 

Если у вас есть файлы или папки, которые не нужно публиковать, включите их имена в файл `.vscodeignore`.

Давайте взглянем на `jupyter-book.ts`, чтобы понять, что делает новое расширение.

```javascript
// This function is called when you run the command `Launch Book: Test Book` from
// command palette in Azure Data Studio. If you would like any additional functionality
// to occur when you launch the book, add to the activate function.
export function activate(context: vscode.ExtensionContext) {
    context.subscriptions.push(vscode.commands.registerCommand('launchBook.test-book', () => {
        processNotebooks();
    }));

    // Add other code here if you want to register another command
}
```

Функция `activate` является основным действием вашего расширения. Все команды, которые необходимо зарегистрировать, должны отображаться внутри функции `activate` аналогично команде `launchBook.test-book`. В функции `processNotebooks` находится папка расширения, которая содержит нашу книгу Jupyter Book. Мы вызываем `bookTreeView.openBook`, используя папку расширения в качестве параметра. 

Файл `package.json` также играет важную роль при регистрации команды расширения:

```json
"activationEvents": [
        "onCommand:launchBook.test-book"
    ],
    "main": "./out/notebook.js",
    "contributes": {
        "commands": [
            {
                "command": "launchBook.test-book",
                "title": "Launch Book: Test Book"
            }
        ]
    }
```

Событие активации, `onCommand`, активирует функцию, зарегистрированную при вызове команды. Для дополнительной настройки существует еще несколько событий активации. Дополнительные сведения см. в разделе [События активации](https://code.visualstudio.com/api/references/activation-events).

## <a name="package-your-extension"></a>Упаковка расширения

Чтобы предоставить общий доступ другим пользователям, нужно упаковать расширение в один файл. Его можно опубликовать в магазине Marketplace расширений Azure Data Studio или предоставить для общего доступа другим участникам команды или сообщества. Для этого нужно установить другой пакет npm из командной строки.

```console
`npm install -g vsce`
```

Измените `README.md` по желанию, перейдите к базовому каталогу расширения и выполните команду `vsce package`. При необходимости можно связать репозиторий с расширением или продолжить работу без него. Чтобы добавить его, добавьте аналогичную строку в файл `package.json`.

```json
"repository": {
    "type": "git",
    "url": "https://github.com/laurajjiang/testbook.git"
}
```

После добавления этих строк создается файл my test-book-0.0.1.vsix, готовый для установки в Azure Data Studio.

## <a name="run-your-extension"></a>Запуск расширения

Чтобы запустить и проверить расширение, перейдите в Azure Data Studio и откройте палитру команд (`Ctrl + Shift + P`). Найдите команду **Расширения: установка из VSIX** и перейдите к папке, содержащей новое расширение. Расширение должно отображаться на панели расширения в Azure Data Studio.

   :::image type="content" source="media/jupyter-book-extension/install-vsix.png" alt-text="Установка VSIX":::

Снова откройте палитру команд и найдите команду, которую мы зарегистрировали, — **Запустить книгу: Test Notebook**. После запуска откроется книга Jupyter Book, упакованная с нашим расширением.

   :::image type="content" source="media/jupyter-book-extension/jupyter-book-launch-ads.png" alt-text="Записная книжка — команда":::

Поздравляем! Вы создали свое первое расширение Jupyter Book и теперь можете предоставить его. Дополнительные сведения о книгах Jupyter Book см. в разделе [Книги с Jupyter](https://jupyterbook.org/intro.html).

## <a name="publish-your-extension-to-the-marketplace"></a>Публикация расширения в Marketplace

Магазин Marketplace расширений Azure Data Studio еще не полностью реализован. Для публикации разместите VSIX-файл расширения в любом месте (например, на странице выпуска GitHub) и отправьте запрос на вытягивание, чтобы добавить в [этот JSON-файл](https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json) сведения о расширении.

## <a name="next-steps"></a>Дальнейшие действия

В этом руководстве вы узнали, как выполнять следующие задачи:
> [!div class="checklist"]
> - Создание проекта расширения
> - Установка генератора расширений
> - Создание расширения Jupyter Book
> - Упаковка расширения
> - Публикация расширения в Marketplace

Мы надеемся, что при прочтении этой статьи у вас появились идеи о том, какими книгами Jupyter Book вы хотели бы поделиться с сообществом Azure Data Studio. 

Если у вас появилась идея, но вы не знаете, с чего начать, откройте вопрос или отправьте твит нашей команде: [azuredatastudio](https://twitter.com/azuredatastudio).

Вы всегда можете обратиться к [руководству по расширениям Visual Studio Code](https://code.visualstudio.com/docs/extensions/overview), так как оно охватывает все существующие API и шаблоны.
