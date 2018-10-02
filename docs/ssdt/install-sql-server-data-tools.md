---
title: Установка SQL Server Data Tools (SSDT) | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.package.stub
ms.assetid: 6f8616cb-9119-42c3-a9b1-936e088763e7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3a847748b0f0025402da1feb794f5c441ea2a3f5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773572"
---
# <a name="install-sql-server-data-tools"></a>Установка базовой версии SQL Server Data Tools
В этом разделе описана установка SQL Server Data Tools. Обновления SQL Server Data Tools доступны на странице скачивания SQL Server Data Tools ([Скачивание и установка SQL Server Data Tools (SSDT) для Visual Studio](http://go.microsoft.com/fwlink/?LinkID=616714)).  
  
Вне зависимости от того, какую версию вы используете (Visual Studio 2012 или Visual Studio 2013), для доступа к новейшим функциональным возможностям нужно установить последние обновления SQL Server Data Tools.  
  
## <a name="sql-server-data-tools-for-visual-studio-2013"></a>SQL Server Data Tools для Visual Studio 2013  
SQL Server Data Tools поставляются в Visual Studio 2013 Express для Web, Visual Studio Express 2013 для Desktop, Visual Studio Community 2013 и во всех платных SKU, включая Professional SKU и более поздние версии. После установки Visual Studio 2013 можно перейти в раздел Сервис -> Расширения и обновления -> Обновления, чтобы узнать, имеется ли обновление для установки.  
  
## <a name="sql-server-data-tools-for-visual-studio-2012"></a>SQL Server Data Tools для Visual Studio 2012  
SQL Server Data Tools поставляется в составе SKU Professional или выше в Visual Studio 2012. После установки Visual Studio 2012 и обновления SQL Server Data Tools за ноябрь 2012 г. или более поздней версии, средство SQL Server Data Tools может сообщать о наличии новых обновлений. Дополнительные сведения см. в статье о [диалоговом окне "Проверка обновлений"](../ssdt/check-for-updates-dialog-box.md).  
  
Если среда Visual Studio 2012 не установлена, SQL Server Data Tools установит интегрированную оболочку Visual Studio 2012 и SQL Server Data Tools.  
  
## <a name="administrative-installation-point"></a>Административная точка установки  
Если необходимо установить SQL Server Data Tools на нескольких компьютерах или компьютерах без доступа к Интернету, можно создать административную структуру установки в сетевой папке или на физическом носителе, а затем выполнить установку из этой точки.  
  
Чтобы создать структуру установки, загрузите файл SSDTSetup.EXE и запустите его с параметром `/layout`*location* для создания структуры в *location*. После этого пользователи смогут запускать файл SSDTSetup.Exe из *location*.  
  
Перейдите на страницу [Установка последней версии SQL Server Data Tools](http://go.microsoft.com/fwlink/?LinkID=616714), щелкните ссылку для своей версии Visual Studio и скачайте файл SSDTSetup.exe для своего языка.  
  
