---
title: Настройка свойств связи атрибутов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- flexible relationships (Analysis Services)
- attributes [Analysis Services], relationships
- relationships [Analysis Services], attributes
- properties [Analysis Services], attribute relationships
- rigid relationships (Analysis Services)
ms.assetid: fce511af-66d7-42fc-bb3a-6c516f16b10e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9a7cea5d2a08b31042ae3e2a07696cf63410d583
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66077117"
---
# <a name="configure-attribute-relationship-properties"></a>Настройка свойств связи атрибута
  В следующей таблице приведен список и описание свойств связи атрибутов.  
  
|Свойство|Description|  
|--------------|-----------------|  
|attribute|Содержит имя атрибута.|  
|Количество элементов|Указывает количество элементов связи. Значением является Many для связи типа «многие к одному» или One для связи «один к одному». Значение по умолчанию — Many. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] В [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]свойство кратности не оказывает никакого влияния — его использование зарезервировано для будущей реализации.|  
|Имя|Содержит понятное имя атрибута.|  
|RelationshipType|Указывает на изменение связей элементов со временем. Значением является Rigid, означающее, что связи между элементами со временем остаются неизменными, или Flexible, означающее, что связи между элементами со временем изменяются. Значение по умолчанию — Flexible. Если связь определена как гибкая, то агрегаты не сбрасываются, а после добавочного обновления выполняется их повторное вычисление (они не будут удаляться, если добавляются только новые элементы). Если связь определена как жесткая, агрегаты в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] сохраняются при добавочном обновлении измерения. Если же связь, определенная как жесткая, все-таки изменилась, то службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] во время добавочной обработки выдадут сообщение об ошибке. Указание подходящих связей и свойств связей повышает производительность запросов и производительность обработки.|  
|Visible|Определяет видимость связи атрибутов. Значениями являются True или False. Значение по умолчанию — True.|  
  
  
