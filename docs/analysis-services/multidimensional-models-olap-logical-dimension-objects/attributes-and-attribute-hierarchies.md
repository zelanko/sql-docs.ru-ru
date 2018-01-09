---
title: "Атрибуты и иерархии атрибутов | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- regular attributes [Analysis Services]
- parent attributes [Analysis Services]
- hierarchies [Analysis Services], attribute
- attributes [Analysis Services], about attributes
- account attributes [Analysis Services]
- dimensions [Analysis Services], attributes
- key attributes [Analysis Services]
- OLAP objects [Analysis Services], attributes
- attributes [Analysis Services], relationships
- attributes [Analysis Services]
- relationships [Analysis Services], attributes
ms.assetid: 59de1ea2-e7a9-4a53-9ee0-14be52e95643
caps.latest.revision: "49"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 012caa5210886a9c2f6e72a6c1b7338154358d1f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="attributes-and-attribute-hierarchies"></a>Атрибуты и иерархии атрибутов
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Измерения — это коллекции атрибутов, которые связаны с одного или нескольких столбцов таблицы или представления в представлении источника данных.  
  
## <a name="key-attribute"></a>Ключевой атрибут  
 Каждое измерение содержит ключевой атрибут. Каждый атрибут привязан к одному или нескольким столбцам в таблице измерения. Ключевой атрибут — это атрибут в измерении, который определяет столбцы в основной таблице измерения, используемые в связях внешнего ключа с таблицей фактов. Как правило, ключевой атрибут представляет первичный ключ столбца или столбцов в таблице измерения. Можно определить логический первичный ключ таблицы в представлении источника данных, не имеющей физического первичного ключа в базовом источнике данных. **Для получения дополнительной информации**, в разделе [определение логических первичных ключей в представлении источника данных &#40; Службы Analysis Services &#41; ](../../analysis-services/multidimensional-models/define-logical-primary-keys-in-a-data-source-view-analysis-services.md). При определении ключевых атрибутов мастер кубов и мастер измерений используют первичные ключевые столбцы таблицы измерения в представлении источника данных. Если таблица измерения не имеет определенного логического или физического первичного ключа, то мастера не смогут правильно определить ключевые атрибуты для измерения.  
  
## <a name="binding-an-attribute-to-columns-in-data-source-view-tables-or-views"></a>Привязка атрибута к столбцам таблиц и представлений в представлении источника данных  
 Атрибут привязан к одному или нескольким столбцам таблицы или представления в представлении источника данных. Атрибут всегда привязан к одному или нескольким ключевым столбцам, которые определяют содержащиеся в нем элементы. По умолчанию это единственный столбец, к которому привязан атрибут. Для некоторых целей атрибут также может быть связан с одним или несколькими дополнительными столбцами. Например, атрибута **NameColumn** свойство определяет имя, отображаемое для пользователя, для каждого элемента атрибута — это свойство атрибута могут быть привязаны к отдельным столбцом измерения через представление источника данных, или может быть привязан к вычисляемый столбец в представлении источника данных. Дополнительные сведения см. в разделе [Справочник по свойствам атрибута измерения](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md).  
  
## <a name="attribute-hierarchies"></a>Иерархии атрибутов  
 По умолчанию элементы атрибута организованы по двум уровням иерархии, состоящим из конечного уровня и уровня (Все). Уровень «Все» содержит статистическое значение элементов атрибута по мерам в каждой группе, элементом которой является измерение, к которому относится этот атрибут. Однако если **IsAggregatable** свойство имеет значение False, все уровень не создается. Дополнительные сведения см. в разделе [Справочник по свойствам атрибута измерения](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md).  
  
 Атрибуты могут быть и обычно бывают упорядочены в пользовательские иерархии, предоставляющие пути детализации, по которым пользователи могут просматривать данные в группах мер, с которыми связан атрибут. В клиентских приложениях атрибуты можно использовать для получения данных о группировании и ограничениях. Когда атрибуты организованы в пользовательские иерархии, пользователь определяет связи между уровнями иерархии, если уровни имеют связи в многие к одному или отношение (называется *естественное* связи). Например, в иерархии «Календарное время» уровень «День» должен быть связан с уровнем «Месяц», уровень «Месяц» — с уровнем «Квартал» и т.д. Определение связей между уровнями в пользовательской иерархии дает возможность службам Analysis Services определить большее количество полезных агрегатов в целях повышения производительности и экономии памяти, что может оказаться немаловажным для больших и сложных кубов. Дополнительные сведения см. в разделе [пользовательские иерархии](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md), [иерархий Create User-Defined](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md), и [определить связи атрибутов](../../analysis-services/multidimensional-models/attribute-relationships-define.md).  
  
## <a name="attribute-relationships-star-schemas-and-snowflake-schemas"></a>Связи атрибутов, схемы «звезда» и «снежинка»  
 По умолчанию в схеме «звезда» все атрибуты непосредственно связаны с ключевым атрибутом, который предоставляет пользователю возможность просматривать фактические данные в кубе на основе любой иерархии атрибута в измерении. В схеме «снежинка» атрибут либо непосредственно связан с ключевым атрибутом, если его базовая таблица непосредственно связана с таблицей фактов, либо связан косвенно через атрибут, привязанный к ключу в базовой таблице, которая связывает таблицу со схемой «снежинка» с непосредственно связанной таблицей.  
  
## <a name="see-also"></a>См. также:  
 [Создание пользовательских иерархий](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)   
 [Определение связей атрибутов](../../analysis-services/multidimensional-models/attribute-relationships-define.md)   
 [Справочник по свойствам атрибута измерения](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
