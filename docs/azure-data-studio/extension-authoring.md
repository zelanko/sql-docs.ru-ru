---
title: Создание расширений
description: Сведения о создании и добавлении расширений в Azure Data Studio
ms.prod: azure-data-studio
ms.technology: ''
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, maghan, sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: adfff7f2aa0fbda1b5e8bdacaddfaef36d16342f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774635"
---
# <a name="extend-the-functionality-by-creating-azure-data-studio-extensions"></a>Расширение функциональных возможностей путем создания расширений Azure Data Studio

Расширения в Azure Data Studio позволяют легко добавлять дополнительные функциональные возможности в базовую установку Azure Data Studio.

Расширения предоставляются командой Azure Data Studio (Майкрософт), а также сторонним сообществом (в том числе вами).


## <a name="author-an-extension"></a>Создание расширения

Если вы хотите расширить возможности Azure Data Studio, то можете создать собственное расширение и опубликовать его в коллекции расширений.

**Написание расширения**

***Предварительные требования***

Для разработки расширения необходимо установить Node.js и указать его расположение в переменной $PATH. Node.js включает в себя npm, диспетчер пакетов Node.js, который будет использоваться для установки генератора расширений.

Запустить новое расширение можно с помощью генератора расширений Azure Data Studio. [Генератор расширений](https://www.npmjs.com/package/generator-azuredatastudio) Yeoman позволяет очень легко создавать простые проекты расширений. Чтобы запустить генератор, введите следующую команду в командной строке:

`npm install -g yo generator-azuredatastudio`

`yo azuredatastudio`


**Справочные материалы по расширяемости**

Сведения о расширяемости Azure Data Studio см. в [обзоре расширяемости](extensibility.md). Кроме того, [здесь](https://github.com/Microsoft/azuredatastudio/tree/main/samples) можно просмотреть примеры использования API.


## <a name="debug-an-extension"></a>Отладка расширения

Для отладки нового расширения можно использовать расширение Visual Studio Code [Отладка Azure Data Studio](https://github.com/kevcunnane/sqlops-debug).

Шаги
- Откройте расширение в [Visual Studio Code](https://code.visualstudio.com/).
- Установите расширение "Отладка Azure Data Studio".
- Нажмите клавишу **F5** или щелкните значок "Отладка" и выберите пункт **Запуск**.
- Новый экземпляр Azure Data Studio запустится в особом режиме (узел разработки расширения) и будет поддерживать ваше расширение.


## <a name="create-an-extension-package"></a>Создание пакета расширения

После написания расширения необходимо создать пакет VSIX, чтобы расширение можно было установить в Azure Data Studio. Создать пакет VSIX можно с помощью [vsce](https://github.com/Microsoft/vscode-vsce).

`npm install -g vsce`

`vsce package`


## <a name="publish-an-extension"></a>Публикация расширения

Чтобы опубликовать новое расширение в Azure Data Studio, выполните указанное ниже действие.

1. Добавьте расширение в https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json.
2. В настоящее время мы не поддерживаем размещение расширений сторонних разработчиков, поэтому вместо скачивания расширения в Azure Data Studio есть возможность перехода на страницу скачивания. Чтобы открыть страницу скачивания расширения, задайте значение ресурса "Microsoft.AzureDataStudio.DownloadPage".
3. Создайте запрос на вытягивание к ветви release/extensions.
4. Отправьте команде запрос на проверку.

Расширение будет проверено и добавлено в коллекцию расширений.

**Публикация обновлений расширения**. Процесс публикации обновлений аналогичен процессу публикации расширения. Не забудьте обновить версию в файле package.json.
