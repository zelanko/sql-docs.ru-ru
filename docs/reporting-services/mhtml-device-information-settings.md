---
title: Настройки сведений об устройстве MHTML | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: reporting-services
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- device information settings [Reporting Services], MHTML rendering
- MHTML [Reporting Services]
ms.assetid: 60b85dd8-b4fb-4ad9-be6a-e7c89ac076fe
caps.latest.revision: 39
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 740bf5e3cfab88d8dfcdac986fd4a4d33c641795
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
  
