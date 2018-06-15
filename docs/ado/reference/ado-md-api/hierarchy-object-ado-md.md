---
title: Объект иерархии (ADO MD) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Hierarchy
helpviewer_keywords:
- Hierarchy object [ADO MD]
ms.assetid: 034af340-ac79-494e-ba5e-2b57da1cb9de
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f6853d2a3fcc0540f23a914e3e39c8720ce3a317
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35284063"
---
# <a name="hierarchy-object-ado-md"></a>Объект иерархии (ADO MD)
Представляет один способ, которым элементы [измерения](../../../ado/reference/ado-md-api/dimension-object-ado-md.md) статистическую обработку или «накоплены.» Измерение может быть статистически вычислена вдоль одной или нескольких иерархий.  
  
## <a name="remarks"></a>Примечания  
 С коллекциями и свойствами **иерархии** объекта, можно сделать следующее:  
  
-   Определить **иерархии** с [имя](../../../ado/reference/ado-md-api/name-property-ado-md.md) и [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) свойства.  
  
-   Возвращает осмысленное строку, описывающую **иерархии** с [описание](../../../ado/reference/ado-md-api/description-property-ado-md.md) свойство.  
  
-   Вернуть [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md) объекты, составляющие **иерархии** с [уровни](../../../ado/reference/ado-md-api/levels-collection-ado-md.md) коллекции.  
  
-   Используйте стандартные ADO [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции для получения дополнительных сведений о **иерархии** объекта.  
  
 **Свойства** коллекция содержит указанный поставщик свойства. В следующей таблице перечислены свойства, которые могут быть доступны. Фактическое свойство списка могут различаться в зависимости от реализации поставщика. См. в документации для поставщика более полный список доступных свойств.  
  
|Имя|Описание|  
|----------|-----------------|  
|AllMember|Элемент, на самом высоком уровне свертки в иерархии.|  
|CatalogName|Имя каталога, к которому принадлежит этот куб.|  
|CubeName|Имя куба.|  
|DefaultMember|Уникальное имя элемента по умолчанию для данной иерархии.|  
|Описание|Понятное описание иерархии.|  
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
  
## <a name="see-also"></a>См. также  
 [Пример CubeDef (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Объект измерения (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [Коллекция hierarchies (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)   
 [Коллекция уровней (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
