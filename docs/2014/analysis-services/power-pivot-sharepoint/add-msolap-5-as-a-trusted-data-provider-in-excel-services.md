---
title: Добавление MSOLAP. 5 в качестве надежного поставщика данных в службах Excel | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c1f40fa4-de6d-41ee-8124-14b4d65988f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9e12c9b4001f0b07deafda8278ac634d595d807a
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547626"
---
# <a name="add-msolap5-as-a-trusted-data-provider-in-excel-services"></a>Добавление MSOLAP.5 в качестве надежного поставщика данных в службах Excel Services
  MSOLAP.5 относится к поставщику OLE DB служб Analysis Services для SQL Server 2012. Этот поставщик должен быть доверенным для служб Excel перед запросом на соединение, который обеспечивает доступность данных PowerPivot на сервере.  
  
 Если PowerPivot для SharePoint настроено с помощью средства настройки PowerPivot, то MSOLAP.5 уже может быть доверенным поставщиком, поскольку это средство содержит действие, удовлетворяющее данному требованию. Однако если используется PowerShell или центр администрирования либо доверенный поставщик не включен в средство конфигурации, то поставщик может отсутствовать и его нужно добавить на этом этапе как часть настройки фермы для доступа к данным PowerPivot.  
  
 Этот шаг нужно выполнить только один раз для каждого приложения служб Excel Services.  
  
 На каждом физическом сервере, обрабатывающем запросы к данным PowerPivot, например сервере PowerPivot для SharePoint или сервере служб Excel Services, должен быть установлен поставщик OLE DB. Установка PowerPivot для SharePoint всегда включает поставщик OLE DB, однако если службы Excel работают на компьютере без PowerPivot для SharePoint, то поставщик следует установить вручную. Дополнительные сведения см. в статье [Установка поставщика OLE DB служб Analysis Services на серверах SharePoint](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).  
  
## <a name="add-a-trusted-provider-to-excel-services"></a>Добавление надежного поставщика в службы Excel Services  
  
1.  В центре администрирования выберите **Управление приложениями служб**и щелкните приложение служб Excel Services.  
  
2.  Щелкните **Надежные поставщики данных**.  
  
3.  Убедитесь, что в списке отображается MSOLAP.5. MSOLAP.5 уже может быть надежным поставщиком, в зависимости от настройки PowerPivot для SharePoint.  
  
4.  Если его нет в списке, щелкните **Добавить надежный поставщик данных**.  
  
5.  В качестве идентификатора поставщика введите `MSOLAP.5`.  
  
6.  В качестве типа поставщика необходимо указать OLE DB.  
  
7.  В поле "Описание поставщика" введите **Поставщик Microsoft OLE DB для OLAP Services 11.0**.  
  
  
