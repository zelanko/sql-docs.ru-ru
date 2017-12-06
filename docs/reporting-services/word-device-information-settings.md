---
title: "Настройки сведений об устройстве Word | Документы Майкрософт"
ms.custom: 
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: reporting-services
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Word [Reporting Services]
- device information settings [Reporting Services], Word
ms.assetid: 28146498-fae7-4b13-b47f-6ec05aa8e057
caps.latest.revision: "7"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 7001097fb8dc92e82254b586f785a79fa193a548
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="word-device-information-settings"></a>Настройки сведений об устройстве Word
  В следующей таблице перечислены настройки сведений об устройстве для подготовки к просмотру в формате [!INCLUDE[ofprword](../includes/ofprword-md.md)] .  
  
|Настройка|Значение|  
|-------------|-----------|  
|**AutoFit**|**False**. Для автоподбора установлено значение **false** в какой-либо таблице Word.<br /><br /> **True**. Для автоподбора установлено значение **true** во всех таблицах Word.<br /><br /> **Never**. Значения автоподбора не установлены ни в одной из таблиц Word, производится возврат к поведению по умолчанию для Word.<br /><br /> **Default**. Автоподбор установлен для таблиц, более узких, чем физическая область отрисовки (ширина физической страницы, включая поля) на логической странице.|  
|**ExpandToggles**|Указывает, должны ли все переключаемые элементы отображаться в полностью раскрытом состоянии. Значение по умолчанию — **false**.|  
|**FixedPageWidth**|Указывает, будет ли ширина страницы, записанная в DOC-файл, увеличиваться, чтобы уместилась самая широкая страница в тексте отчета. Значение по умолчанию — **false**.|  
|**OmitHyperlinks**|Указывает, опускать ли действие гиперссылки для всех элементов, где оно установлено. Значение по умолчанию — **false**.|  
|**OmitDrillthroughs**|Указывает, опускать ли действие детализации для всех элементов, где оно установлено. Значение по умолчанию — **false**.|  
  
## <a name="see-also"></a>См. также  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Передача настроек сведений об устройстве модулям подготовки отчетов к просмотру](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Настройка параметров модулей подготовки отчетов в RSReportServer.Config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Технический справочник (службы SSRS)](../reporting-services/technical-reference-ssrs.md)  
  
  
