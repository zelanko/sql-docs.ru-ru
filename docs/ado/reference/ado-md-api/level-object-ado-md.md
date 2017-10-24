---
title: "Уровень объекта (ADO MD) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Level
helpviewer_keywords:
- Level object [ADO MD]
ms.assetid: 37815869-ed30-45fd-9aea-0a986c1b305c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 73258b69ee6a341098365443f388c6944eb2dd51
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="level-object-ado-md"></a>Объект уровня (ADO MD)
Содержит набор элементов, каждый из которых имеет один и тот же ранг в иерархии.  
  
## <a name="remarks"></a>Замечания  
 С коллекциями и свойствами **уровень** объекта, можно сделать следующее:  
  
-   Определить **уровень** с [имя](../../../ado/reference/ado-md-api/name-property-ado-md.md) и [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) свойства.  
  
-   Возвращает строку, используемую при отображении **уровень** с [заголовок](../../../ado/reference/ado-md-api/caption-property-ado-md.md) свойство.  
  
-   Возвращает осмысленное строку, описывающую **уровень** с [описание](../../../ado/reference/ado-md-api/description-property-ado-md.md) свойство.  
  
-   Вернуть [член](../../../ado/reference/ado-md-api/member-object-ado-md.md) объекты, составляющие **уровень** с [члены](../../../ado/reference/ado-md-api/members-collection-ado-md.md) коллекции.  
  
-   Возвращает количество уровней от корня **уровень** с [глубина](../../../ado/reference/ado-md-api/depth-property-ado-md.md) свойство.  
  
-   Используйте стандартные ADO [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции для получения дополнительных сведений о **уровень** объекта.  
  
 **Свойства** коллекция содержит указанный поставщик свойства. В следующей таблице перечислены свойства, которые могут быть доступны. Фактическое свойство списка могут различаться в зависимости от реализации поставщика. См. в документации для поставщика более полный список доступных свойств.  
  
|Имя|Description|  
|----------|-----------------|  
|CatalogName|Имя каталога, к которому принадлежит этот куб.|  
|Имя куба|Имя куба.|  
|Description|Понятное описание уровня.|  
|DimensionUniqueName|Однозначная имя [измерения](../../../ado/reference/ado-md-api/dimension-object-ado-md.md).|  
|HierarchyUniqueName|Однозначная имя иерархии.|  
|LevelCaption|Метка или заголовок, связанный с уровнем.|  
|LevelCardinality|Число элементов уровня.|  
|LevelGUID|Идентификатор GUID уровня.|  
|LevelName|Имя уровня.|  
|LevelNumber|Расстояние между уровнем и корневого элемента иерархии.|  
|LevelType|Тип уровня.|  
|LevelUniqueName|Однозначная имя уровня.|  
|SchemaName|Имя схемы, которой принадлежит этот куб.|  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/level-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример CubeDef (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Объект иерархии (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)   
 [Коллекция уровней (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)   
 [Члены коллекции (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)   
 [Коллекция свойств (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)

