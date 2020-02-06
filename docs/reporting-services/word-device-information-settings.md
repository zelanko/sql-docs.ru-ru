---
title: Настройки сведений об устройстве Word | Документы Майкрософт
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- Word [Reporting Services]
- device information settings [Reporting Services], Word
ms.assetid: 28146498-fae7-4b13-b47f-6ec05aa8e057
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 776a825c480568be2640d1309c7c3a48970e2c54
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "65571133"
---
# <a name="word-device-information-settings"></a>Настройки сведений об устройстве Word
  В следующей таблице перечислены настройки сведений об устройстве для подготовки к просмотру в формате [!INCLUDE[ofprword](../includes/ofprword-md.md)] .  
  
|Параметр|Значение|  
|-------------|-----------|  
|**AutoFit**|**False**. Для автоподбора установлено значение **false** в какой-либо таблице Word.<br /><br /> **True**. Для автоподбора установлено значение **true** во всех таблицах Word.<br /><br /> **Never**. Значения автоподбора не установлены ни в одной из таблиц Word, производится возврат к поведению по умолчанию для Word.<br /><br /> **Default**. Автоподбор установлен для таблиц, более узких, чем физическая область отрисовки (ширина физической страницы, включая поля) на логической странице.|  
|**ExpandToggles**|Указывает, должны ли все переключаемые элементы отображаться в полностью раскрытом состоянии. Значение по умолчанию — **false**.|  
|**FixedPageWidth**|Указывает, будет ли ширина страницы, записанная в DOC-файл, увеличиваться, чтобы уместилась самая широкая страница в тексте отчета. Значение по умолчанию — **false**.|  
|**OmitHyperlinks**|Указывает, опускать ли действие гиперссылки для всех элементов, где оно установлено. Значение по умолчанию — **false**.|  
|**OmitDrillthroughs**|Указывает, опускать ли действие детализации для всех элементов, где оно установлено. Значение по умолчанию — **false**.|  
  
## <a name="see-also"></a>См. также:  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Передача настроек сведений об устройстве модулям подготовки отчетов к просмотру](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Настройка параметров модулей подготовки отчетов в RSReportServer.Config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Технический справочник (службы SSRS)](../reporting-services/technical-reference-ssrs.md)  
  
  
