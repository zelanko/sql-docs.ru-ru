---
title: "Настройка свойств связи атрибута | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
helpviewer_keywords:
- flexible relationships (Analysis Services)
- attributes [Analysis Services], relationships
- relationships [Analysis Services], attributes
- properties [Analysis Services], attribute relationships
- rigid relationships (Analysis Services)
ms.assetid: fce511af-66d7-42fc-bb3a-6c516f16b10e
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: cfd4e60e3ed8329e78b5de7242b3952601a87b11
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="attribute-relationships---configure-attribute-properties"></a>Связи атрибутов — Настройка свойств атрибутов
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]В следующей таблице перечислены и описаны свойства связи атрибутов.  
  
|Свойство|Description|  
|--------------|-----------------|  
|Attribute|Содержит имя атрибута.|  
|Количество элементов|Указывает количество элементов связи. Значением является Many для связи типа «многие к одному» или One для связи «один к одному». Значение по умолчанию — Many. В службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]свойство количества элементов не используется, оно зарезервировано для будущего использования.|  
|Название|Содержит понятное имя атрибута.|  
|RelationshipType|Указывает на изменение связей элементов со временем. Значением является Rigid, означающее, что связи между элементами со временем остаются неизменными, или Flexible, означающее, что связи между элементами со временем изменяются. Значение по умолчанию — Flexible. Если связь определена как гибкая, то агрегаты не сбрасываются, а после добавочного обновления выполняется их повторное вычисление (они не будут удаляться, если добавляются только новые элементы). Если связь определена как жесткая, агрегаты в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] сохраняются при добавочном обновлении измерения. Если же связь, определенная как жесткая, все-таки изменилась, то службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] во время добавочной обработки выдадут сообщение об ошибке. Указание подходящих связей и свойств связей повышает производительность запросов и производительность обработки.|  
|Visible|Определяет видимость связи атрибутов. Значениями являются True или False. Значение по умолчанию — True.|  
  
  
