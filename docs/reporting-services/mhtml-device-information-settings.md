---
title: Настройки сведений об устройстве MHTML | Документы Майкрософт
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], MHTML rendering
- MHTML [Reporting Services]
ms.assetid: 60b85dd8-b4fb-4ad9-be6a-e7c89ac076fe
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 170c97c2f01f58972fbcba1d8dc9e63045a1095f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47659322"
---
# <a name="mhtml-device-information-settings"></a>Настройки сведений об устройстве MHTML
  В следующей таблице перечислены настройки сведений об устройстве, предназначенные для подготовки отчетов к просмотру в формате веб-архива (MHTML).  
  
|Настройка|Значение|  
|-------------|-----------|  
|**JavaScript**|Указывает, поддерживается ли JavaScript в отчете, готовом для просмотра.|  
|**OutlookCompat**|Указывает, нужно ли использовать при подготовке к просмотру дополнительные метаданные для улучшения отображения отчета в Outlook. Значение по умолчанию — **true**|  
|**Фрагмент MHTML**|Показывает, создается ли MHTML-фрагмент вместо полного MHTML-документа. MHTML-фрагмент включает содержимое отчета в элементе TABLE и не содержит элементы MHTML и BODY. Значение по умолчанию — **false**.|  
|**DataVisualizationFitSizing**|Указывает поведение визуализации данных при ее использовании в табликсе. Сюда входят: диаграмма, датчик и карта.<br /><br /> Возможные значения: **Приблизительно** и **Точно**.<br /><br /> Значение по умолчанию ― **Приблизительно**. Если параметр удаляется из файла **rsreportserver.config** , то по умолчанию будет использоваться поведение **Точно**.<br /><br /> Выбор значения **Точно** может негативно сказаться на производительности, поскольку на обработку для определения точного размера может уйти больше времени.|  
  
## <a name="see-also"></a>См. также:  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Передача настроек сведений об устройстве модулям подготовки отчетов к просмотру](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Настройка параметров модулей подготовки отчетов в RSReportServer.Config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Технический справочник (службы SSRS)](../reporting-services/technical-reference-ssrs.md)  
  
  
