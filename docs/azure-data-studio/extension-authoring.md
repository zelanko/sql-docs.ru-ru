---
title: Создание расширений
description: С помощью расширения вы можете добавить функциональные возможности в Azure Data Studio. Узнайте, как создать расширение и опубликовать его в коллекции расширений.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu
ms.custom: seodec18
ms.date: 08/26/2020
ms.openlocfilehash: 477e93dc272c4a26e40333b02728c643299161ce
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/01/2020
ms.locfileid: "89283721"
---
# <a name="extend-the-functionality-by-creating-azure-data-studio-extensions"></a>Расширение функциональных возможностей путем создания расширений Azure Data Studio

Расширения в Azure Data Studio позволяют легко добавлять дополнительные функциональные возможности в базовую установку Azure Data Studio.

Расширения предоставляются командой Azure Data Studio (Майкрософт), а также сторонним сообществом (в том числе вами).

## <a name="author-an-extension"></a>Создание расширения

Если вы хотите расширить возможности Azure Data Studio, то можете создать собственное расширение и опубликовать его в коллекции расширений.

**Написание расширения**

***Предварительные требования***

Для разработки расширения необходимо установить [Node.js](https://nodejs.org/) и указать его расположение в переменной `$PATH`. Node.js включает в себя npm, диспетчер пакетов Node.js, который будет использоваться для установки генератора расширений.

Создать расширение можно с помощью генератора расширений Azure Data Studio. [Генератор расширений](https://www.npmjs.com/package/generator-azuredatastudio) Yeoman позволяет очень легко создавать проекты расширений. Чтобы запустить генератор, введите следующую команду в командной строке:

```console
npm install -g yo generator-azuredatastudio # Install the generator
yo azuredatastudio
```

Подробное руководство по началу работы с шаблоном расширения см. в разделе [Создание расширения](./tutorial-create-extension.md?view=sql-server-ver15), подробно описывающем создание расширения раскладки клавиатуры.

**Справочные материалы по расширяемости**

Сведения о расширяемости Azure Data Studio см. в [обзоре расширяемости](extensibility.md). Кроме того, [здесь](https://github.com/Microsoft/azuredatastudio/tree/main/samples) можно просмотреть примеры использования API.

## <a name="debug-an-extension"></a>Отладка расширения

Для отладки нового расширения можно использовать расширение Visual Studio Code [Отладка Azure Data Studio](https://github.com/kevcunnane/sqlops-debug).

Шаги:

1. Откройте расширение в [Visual Studio Code](https://code.visualstudio.com/).
2. Установите расширение "Отладка Azure Data Studio".
3. Нажмите клавишу **F5** или щелкните значок "Отладка" и выберите пункт **Запуск**.
4. Новый экземпляр Azure Data Studio запустится в особом режиме (узел разработки расширения) и будет поддерживать ваше расширение.

## <a name="create-an-extension-package"></a>Создание пакета расширения

После написания расширения необходимо создать пакет VSIX, чтобы расширение можно было установить в Azure Data Studio. Создать пакет VSIX можно с помощью [vsce](https://github.com/Microsoft/vscode-vsce) (Visual Studio Code Extensions).

```console
npm install -g vsce
cd myExtensionName
vsce package
# The myExtensionName.vsix file has now been generated
```

С помощью пакета VSIX можно предоставить общий доступ к своему расширению в локальной среде и в частном порядке, поделившись файлом `.vsix` и используя команду **Расширения: установить из файла VSIX** из палитры команд, чтобы установить расширение в Azure Data Studio.

## <a name="publish-an-extension"></a>Публикация расширения

Чтобы опубликовать новое расширение в Azure Data Studio, выполните указанное ниже действие.

1. Добавьте расширение в https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json.
2. В настоящее время мы не поддерживаем размещение расширений сторонних разработчиков, поэтому вместо скачивания расширения в Azure Data Studio есть возможность перехода на страницу скачивания. Чтобы открыть страницу скачивания расширения, задайте значение ресурса "Microsoft.AzureDataStudio.DownloadPage".
3. Создайте запрос на вытягивание к ветви release/extensions.
4. Отправьте команде запрос на проверку.

Расширение будет проверено и добавлено в коллекцию расширений.

**Публикация обновлений расширения**

Процесс публикации обновлений аналогичен процессу публикации расширения. Не забудьте обновить версию в файле package.json.

## <a name="next-steps"></a>Next Steps

Пошаговые инструкции по началу работы см. в одном из следующих руководств по созданию расширений:

- [Учебник по расширению раскладки клавиатуры](extensions/keymap-extension.md)
- [Учебник по расширению панели мониторинга](extensions/dashboard-extension.md)
- [Учебник по расширению записной книжки](extensions/notebook-extension.md)
- [Учебник по расширению Jupyter Book](extensions/jupyter-book-extension.md)
- [Учебник по расширению мастера](extensions/wizard-extension.md)