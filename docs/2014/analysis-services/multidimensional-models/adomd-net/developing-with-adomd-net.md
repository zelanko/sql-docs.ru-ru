---
title: Разработка с использованием ADOMD.NET | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ADOMD.NET
ms.assetid: abaf33aa-db55-43bf-8f30-15547559be1d
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1dfdd10ae488633812b61e2a0220f7c22e65e575
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36109816"
---
# <a name="developing-with-adomdnet"></a>Разработка с использованием ADOMD.NET
  ADOMD.NET — [!INCLUDE[msCoName](../../../includes/msconame-md.md)] поставщика данных .NET Framework, предназначенных для связи с [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. В компоненте ADOMD.NET используется протокол XML для аналитики в целях обеспечения связи с источниками аналитических данных при помощи соединений по протоколу TCP/IP или HTTP, что позволяет передавать и принимать SOAP-запросы и ответы, совместимые со спецификацией XML для аналитики. Команды могут передаваться на языке MDX, языке DMX, языке ASSL или даже с использованием ограниченного синтаксиса SQL и могут не возвращать результат. При помощи модели объектов ADOMD.NET можно выполнять запросы к аналитическим данным, ключевым показателям эффективности и моделям интеллектуального анализа данных, а также управлять ими. Компонент ADOMD.NET позволяет также просматривать и работать с метаданными путем извлечения соответствующих OLE DB наборов строк схемы либо при помощи модели объектов ADOMD.NET.  
  
 Поставщик данных ADOMD.NET представлен пространством `Microsoft.AnalysisServices.AdomdClient` пространства имен.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Программирование клиента ADOMD.NET](../../multidimensional-models-adomd-net-client/adomd-net-client-programming.md)|Описывает использование клиентских объектов ADOMD.NET для извлечения данных и метаданных из источников аналитических данных.|  
|[Программирование сервера ADOMD.NET](../../multidimensional-models-adomd-net-server/adomd-net-server-programming.md)|Описывает использование серверных объектов ADOMD.NET для создания хранимых процедур и определяемых пользователем функций.|  
|[Распространение ADOMD.NET](redistributing-adomd-net.md)|Описывает процесс распространения компонента ADOMD.NET.|  
|<xref:Microsoft.AnalysisServices.AdomdClient>|Подробно описывает объекты, содержащиеся в пространстве имен `Microsoft.AnalysisServices.AdomdClient`.|  
  
## <a name="see-also"></a>См. также  
 [Многомерные выражения &#40;многомерных Выражений&#41; ссылки](/sql/mdx/multidimensional-expressions-mdx-reference)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; ссылки](/sql/dmx/data-mining-extensions-dmx-reference)   
 [Службы Analysis Services наборы строк схемы](../../schema-rowsets/analysis-services-schema-rowsets.md)   
 [Развертывание с помощью функций анализа служб языка сценариев &#40;ASSL&#41;](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Доступ к данным многомерной модели &#40;службы Analysis Services — многомерные данные&#41;](../mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)  
  
  
