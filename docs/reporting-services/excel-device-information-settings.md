---
title: Настройки сведений об устройстве Excel | Документы Майкрософт
description: Узнайте о различных настройках сведений об устройстве, доступных для отрисовки в формате Microsoft Excel.
ms.date: 01/23/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], Excel rendering
- Excel [Reporting Services], rendering
ms.assetid: bb5f3566-f033-4470-be87-1f52fb7a4ab6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c4d84c98923a3cee94f64fed863e621821bd7a39
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87245133"
---
# <a name="excel-device-information-settings"></a>Настройки сведений об устройстве Excel
  В следующей таблице перечислены настройки сведений об устройстве для подготовки к просмотру в формате [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] .  
  
|Параметр|Значение|  
|-------------|-----------|  
|**OmitDocumentMap**|Показывает, нужно ли исключать схему документа из параметров отчетов, поддерживающих ее. Значение по умолчанию — **false**.|  
|**OmitFormulas**|Показывает, нужно ли исключать формулы из отчета, готового для просмотра. Значение по умолчанию — **false**.|  
|**SimplePageHeaders**|Показывает, преобразуется ли верхний колонтитул страницы отчетов в верхний колонтитул Excel при подготовке к просмотру. Значение **false** показывает, что верхний колонтитул страницы при подготовке к просмотру преобразуется в первую строку листа. Значение по умолчанию — **false**.|  
|**DynamicImageDpi**|Разрешение динамических изображений, таких как диаграммы, датчики и карты. Значение по умолчанию — **96**. (Доступно в решении "Сервер отчетов Power BI" (январь 2020 года) и более поздних версий)|  

  
## <a name="see-also"></a>См. также:  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Передача настроек сведений об устройстве модулям подготовки отчетов к просмотру](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Настройка параметров модулей подготовки отчетов в RSReportServer.Config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Технический справочник (службы SSRS)](../reporting-services/technical-reference-ssrs.md)  
  
  
