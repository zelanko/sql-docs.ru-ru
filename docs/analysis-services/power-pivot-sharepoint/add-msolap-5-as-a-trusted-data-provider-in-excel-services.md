---
title: "Добавление MSOLAP.5 в качестве надежного поставщика данных в службах Excel Services | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
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
ms.openlocfilehash: 146b61a544dfc91585cde88bbdb54d2f43375b0f
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="add-msolap5-as-a-trusted-data-provider-in-excel-services"></a>Добавление MSOLAP.5 в качестве надежного поставщика данных в службах Excel Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]MSOLAP.5 относится к поставщику OLE DB служб Analysis Services для SQL Server 2012. Этот поставщик должен быть доверенным для служб Excel перед запросом на подключение, который обеспечивает доступность данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] на сервере.  
  
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
  
  
