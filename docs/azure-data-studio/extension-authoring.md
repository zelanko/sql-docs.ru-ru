---
title: Создание расширений
titleSuffix: Azure Data Studio
description: Дополнительные сведения о создании и добавлении расширения в студию данных Azure
ms.custom: seodec18
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 54036ccf8d8b47eedede1d2ddfe5d85b6dbee351
ms.sourcegitcommit: ca9b5cb6bccfdba4cdbe1697adf5c673b4713d6c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/18/2019
ms.locfileid: "56407524"
---
# <a name="extend-the-functionality-by-creating-azure-data-studio-extensions"></a>Расширить функциональные возможности путем создания расширений Studio данных Azure

Расширения в [!INCLUDE[name-sos](../includes/name-sos-short.md)] предоставляют простой способ для добавления дополнительных функций к базовому [!INCLUDE[name-sos](../includes/name-sos-short.md)] установки.

Расширения предоставляются team Studio данных Azure (Майкрософт), а также сторонние сообщества (вы!).


## <a name="author-an-extension"></a>Создать расширение

Если вы заинтересованы в расширении возможностей Azure Data Studio, можно создать собственное расширение и опубликовать его в коллекцию расширений.

**Создание расширения**

***Предварительные требования***

Чтобы разрабатывать расширения необходимо Node.js установлена и доступна в вашей $PATH. Node.js включает в себя npm, диспетчер пакетов Node.js, который будет использоваться для установки расширения генератора.

Чтобы начать новое расширение, можно использовать генератор Studio модуль обработки данных Azure. Yeoman [расширение генератора](https://www.npmjs.com/package/generator-azuredatastudio) позволяет легко создавать проекты простое расширение. Чтобы запустить генератор, введите следующую команду в командной строке:

`npm install -g yo generator-azuredatastudio`

`yo azuredatastudio`


**Ссылки на расширения**

Дополнительные сведения о расширении среды Studio данных Azure см. в разделе [Общие сведения о расширяемости](extensibility.md). Также вы увидите примеры использования API в существующих [примеры](https://github.com/Microsoft/azuredatastudio/tree/master/samples).


## <a name="debug-an-extension"></a>Отладка расширения

Можно отлаживать с помощью расширения Visual Studio Code новое расширение [Azure данных Studio отладку](https://github.com/kevcunnane/sqlops-debug).

Шаги
- Откройте расширения с помощью [Visual Studio Code](https://code.visualstudio.com/)
- Установка расширения отладки Studio данных Azure
- Нажмите клавишу **F5** или щелкните значок "Отладка" и нажмите кнопку **запустить**.
- Запускает новый экземпляр Azure Data Studio в специальном режиме (узел разработки расширения) и теперь этот новый экземпляр учитывает вашего расширения.


## <a name="create-an-extension-package"></a>Создать пакет расширения

После записи расширения, необходимо создать пакет VSIX, чтобы иметь возможность установить его в Studio данных Azure. Можно использовать [vsce](https://github.com/Microsoft/vscode-vsce) для создания пакета VSIX.

`npm install -g vsce`

`vsce package`


## <a name="publish-an-extension"></a>Публикация расширения

Чтобы опубликовать новое расширение для Azure Data Studio:

1. Добавить расширение https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json
2. В настоящее время у нас нет поддержки, чтобы сторонние расширения узла, поэтому вместо загрузки расширения, Azure Data Studio имеет параметр, чтобы перейти на страницу загрузки. Чтобы задать страницу загрузки для модуля, значение ресурса «Microsoft.AzureDataStudio.DownloadPage».
3. Создание запроса на Вытягивание от ветви выпуска или расширения.
4. Отправьте запрос на проверку команде.

Расширение будет проверяется и добавляется в коллекцию расширений.

**Публикация обновления расширений** процесс публикации обновлений аналогична публикации расширения. Убедитесь, что версия обновляется в package.json
