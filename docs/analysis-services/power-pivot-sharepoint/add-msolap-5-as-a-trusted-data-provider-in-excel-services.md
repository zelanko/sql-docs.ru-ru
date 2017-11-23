---
title: "Добавление MSOLAP.5 в качестве надежного поставщика данных в службах Excel Services | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: power-pivot-sharepoint
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1f40fa4-de6d-41ee-8124-14b4d65988f5
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 64b3ea1f946e73a3f56cd70b5e88d9752d74a238
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="add-msolap5-as-a-trusted-data-provider-in-excel-services"></a>Добавление MSOLAP.5 в качестве надежного поставщика данных в службах Excel Services
  MSOLAP.5 относится к поставщику OLE DB служб Analysis Services для SQL Server 2012. Этот поставщик должен быть доверенным для служб Excel перед запросом на подключение, который обеспечивает доступность данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] на сервере.  
  
 Если компонент [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint настроен с помощью средства настройки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , MSOLAP.5 может уже использоваться в качестве доверенного поставщика, так как это средство содержит действие, удовлетворяющее упомянутому требованию. Но если используется PowerShell или центр администрирования, или если доверенный поставщик не включен в средство настройки, поставщик может отсутствовать. В таком случае его нужно добавить на этом этапе как часть настройки фермы для доступа к данным [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
 Этот шаг нужно выполнить только один раз для каждого приложения служб Excel Services.  
  
 На каждом физическом сервере, обрабатывающем запросы к данным [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , например сервере [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint или сервере служб Excel Services, должен быть установлен поставщик OLE DB. Установка [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint всегда включает поставщик OLE DB, но если службы Excel работают на компьютере без [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint, поставщик следует установить вручную. Дополнительные сведения см. в статье [Установка поставщика OLE DB служб Analysis Services на серверах SharePoint](http://msdn.microsoft.com/en-us/2c62daf9-1f2d-4508-a497-af62360ee859).  
  
## <a name="add-a-trusted-provider-to-excel-services"></a>Добавление надежного поставщика в службы Excel Services  
  
1.  В центре администрирования выберите **Управление приложениями служб**и щелкните приложение служб Excel Services.  
  
2.  Щелкните **Надежные поставщики данных**.  
  
3.  Убедитесь, что в списке отображается MSOLAP.5. MSOLAP.5 может уже использоваться в качестве надежного поставщика в зависимости от настроек [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint.  
  
4.  Если его нет в списке, щелкните **Добавить надежный поставщик данных**.  
  
5.  В качестве идентификатора поставщика введите **MSOLAP.5**.  
  
6.  В качестве типа поставщика необходимо указать OLE DB.  
  
7.  В поле "Описание поставщика" введите **Поставщик Microsoft OLE DB для OLAP Services 11.0**.  
  
  
