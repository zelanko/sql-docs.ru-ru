---
title: Разработка с использованием ADOMD.NET | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 49bfcc651b00f9d6afc5d2028e174062b0916515
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="developing-with-adomdnet"></a>Разработка с использованием ADOMD.NET
  ADOMD.NET — [!INCLUDE[msCoName](../../../includes/msconame-md.md)] поставщика данных .NET Framework, предназначенных для связи с [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. В компоненте ADOMD.NET используется протокол XML для аналитики в целях обеспечения связи с источниками аналитических данных при помощи соединений по протоколу TCP/IP или HTTP, что позволяет передавать и принимать SOAP-запросы и ответы, совместимые со спецификацией XML для аналитики. Команды могут передаваться на языке MDX, языке DMX, языке ASSL или даже с использованием ограниченного синтаксиса SQL и могут не возвращать результат. При помощи модели объектов ADOMD.NET можно выполнять запросы к аналитическим данным, ключевым показателям эффективности и моделям интеллектуального анализа данных, а также управлять ими. Компонент ADOMD.NET позволяет также просматривать и работать с метаданными путем извлечения совместимых с OLE DB наборов строк схемы либо при помощи модели объектов ADOMD.NET.  
  
 Поставщик данных ADOMD.NET представлен пространством имен **Microsoft.AnalysisServices.AdomdClient** .  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Программирование клиента ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)|Описывает использование клиентских объектов ADOMD.NET для извлечения данных и метаданных из источников аналитических данных.|  
|[Программирование сервера ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)|Описывает использование серверных объектов ADOMD.NET для создания хранимых процедур и определяемых пользователем функций.|  
|[Распространение ADOMD.NET](../../../analysis-services/multidimensional-models/adomd-net/redistributing-adomd-net.md)|Описывает процесс распространения компонента ADOMD.NET.|  
|<xref:Microsoft.AnalysisServices.AdomdClient>|Подробно описывает объекты, содержащиеся в пространстве имен **Microsoft.AnalysisServices.AdomdClient** .|  
  
## <a name="see-also"></a>См. также  
 [Многомерные выражения & #40; Многомерные Выражения & #41; Ссылка](../../../mdx/multidimensional-expressions-mdx-reference.md)   
 [Расширения интеллектуального анализа данных & #40; расширений интеллектуального анализа данных & #41; Ссылка](../../../dmx/data-mining-extensions-dmx-reference.md)   
 [Службы Analysis Services наборы строк схемы](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)   
 [Развертывание с помощью функций анализа служб языка сценариев &#40;ASSL&#41;](../../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Доступ к данным многомерной модели &#40;службы Analysis Services — многомерные данные&#41;](../../../analysis-services/multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)  
  
  
