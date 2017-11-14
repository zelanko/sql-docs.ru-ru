---
title: "Объект иерархии (ADO MD) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Hierarchy
helpviewer_keywords:
- Hierarchy object [ADO MD]
ms.assetid: 034af340-ac79-494e-ba5e-2b57da1cb9de
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 46bb03c91b2305f0453676891d87676e784b03fa
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="hierarchy-object-ado-md"></a>Объект иерархии (ADO MD)
Представляет один способ, которым элементы [измерения](../../../ado/reference/ado-md-api/dimension-object-ado-md.md) статистическую обработку или «накоплены.» Измерение может быть статистически вычислена вдоль одной или нескольких иерархий.  
  
## <a name="remarks"></a>Замечания  
 С коллекциями и свойствами **иерархии** объекта, можно сделать следующее:  
  
-   Определить **иерархии** с [имя](../../../ado/reference/ado-md-api/name-property-ado-md.md) и [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) свойства.  
  
-   Возвращает осмысленное строку, описывающую **иерархии** с [описание](../../../ado/reference/ado-md-api/description-property-ado-md.md) свойство.  
  
-   Вернуть [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md) объекты, составляющие **иерархии** с [уровни](../../../ado/reference/ado-md-api/levels-collection-ado-md.md) коллекции.  
  
-   Используйте стандартные ADO [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции для получения дополнительных сведений о **иерархии** объекта.  
  
 **Свойства** коллекция содержит указанный поставщик свойства. В следующей таблице перечислены свойства, которые могут быть доступны. Фактическое свойство списка могут различаться в зависимости от реализации поставщика. См. в документации для поставщика более полный список доступных свойств.  
  
|Имя|Description|  
|----------|-----------------|  
|AllMember|Элемент, на самом высоком уровне свертки в иерархии.|  
|CatalogName|Имя каталога, к которому принадлежит этот куб.|  
|Имя куба|Имя куба.|  
|DefaultMember|Уникальное имя элемента по умолчанию для данной иерархии.|  
|Description|Понятное описание иерархии.|  
|DimensionType|Тип измерения, к которому принадлежит эта иерархия.|  
|DimensionUniqueName|Однозначная имя измерения.|  
|HierarchyCaption|Метка или заголовок, связанный с иерархией.|  
|HierarchyCardinality|Количество элементов в иерархии.|  
|HierarchyGUID|Идентификатор GUID для иерархии.|  
|HierarchyName|Имя иерархии.|  
|HierarchyUniqueName|Однозначная имя иерархии.|  
|SchemaName|Имя схемы, которой принадлежит этот куб.|  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/hierarchy-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример CubeDef (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Объект измерения (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [Коллекция hierarchies (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)   
 [Коллекция уровней (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)   
 [Коллекция свойств (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)

