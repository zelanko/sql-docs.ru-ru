---
title: "Настройки сведений об устройстве MHTML | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- device information settings [Reporting Services], MHTML rendering
- MHTML [Reporting Services]
ms.assetid: 60b85dd8-b4fb-4ad9-be6a-e7c89ac076fe
caps.latest.revision: 39
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c80135a9fa4f9cec547ffa3f837e7af37f4bf89a
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="mhtml-device-information-settings"></a>Настройки сведений об устройстве MHTML
  В следующей таблице перечислены настройки сведений об устройстве, предназначенные для подготовки отчетов к просмотру в формате веб-архива (MHTML).  
  
|Настройка|Значение|  
|-------------|-----------|  
|**JavaScript**|Указывает, поддерживается ли JavaScript в отчете, готовом для просмотра.|  
|**OutlookCompat**|Указывает, нужно ли использовать при подготовке к просмотру дополнительные метаданные для улучшения отображения отчета в Outlook. Значение по умолчанию — **true**|  
|**Фрагмент MHTML**|Показывает, создается ли MHTML-фрагмент вместо полного MHTML-документа. MHTML-фрагмент включает содержимое отчета в элементе TABLE и не содержит элементы MHTML и BODY. Значение по умолчанию — **false**.|  
|**DataVisualizationFitSizing**|Указывает поведение визуализации данных при ее использовании в табликсе. Сюда входят: диаграмма, датчик и карта.<br /><br /> Возможные значения: **Приблизительно** и **Точно**.<br /><br /> Значение по умолчанию ― **Приблизительно**. Если параметр удаляется из файла **rsreportserver.config** , то по умолчанию будет использоваться поведение **Точно**.<br /><br /> Выбор значения **Точно** может негативно сказаться на производительности, поскольку на обработку для определения точного размера может уйти больше времени.|  
  
## <a name="see-also"></a>См. также  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Передача настроек сведений об устройстве для модулей подготовки отчетов](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Настройка параметров модуля подготовки отчетов в RSReportServer.Config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Технический справочник по &#40; Службы SSRS &#41;](../reporting-services/technical-reference-ssrs.md)  
  
  
