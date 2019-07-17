---
title: Настройка свойств связи атрибута | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9a7270dd698dfb8d3d3002c302186e97b912044f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68179294"
---
# <a name="attribute-relationships---configure-attribute-properties"></a>Связи атрибутов — настройка свойств атрибута
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  В следующей таблице приведен список и описание свойств связи атрибутов.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|attribute|Содержит имя атрибута.|  
|Количество элементов|Указывает количество элементов связи. Значением является Many для связи типа «многие к одному» или One для связи «один к одному». Значение по умолчанию — Many. В службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]свойство количества элементов не используется, оно зарезервировано для будущего использования.|  
|Name|Содержит понятное имя атрибута.|  
|RelationshipType|Указывает на изменение связей элементов со временем. Значением является Rigid, означающее, что связи между элементами со временем остаются неизменными, или Flexible, означающее, что связи между элементами со временем изменяются. Значение по умолчанию — Flexible. Если связь определена как гибкая, то агрегаты не сбрасываются, а после добавочного обновления выполняется их повторное вычисление (они не будут удаляться, если добавляются только новые элементы). Если связь определена как жесткая, агрегаты в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] сохраняются при добавочном обновлении измерения. Если же связь, определенная как жесткая, все-таки изменилась, то службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] во время добавочной обработки выдадут сообщение об ошибке. Указание подходящих связей и свойств связей повышает производительность запросов и производительность обработки.|  
|Видимый|Определяет видимость связи атрибутов. Значениями являются True или False. Значение по умолчанию — True.|  
  
  
