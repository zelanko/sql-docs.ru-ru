---
title: Объект Hierarchy (многомерные Объекты ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Hierarchy
helpviewer_keywords:
- Hierarchy object [ADO MD]
ms.assetid: 034af340-ac79-494e-ba5e-2b57da1cb9de
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d4f1ccb441da92c19b15a7e84b0fc0e451844d0a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47851442"
---
# <a name="hierarchy-object-ado-md"></a>Объект Hierarchy (многомерные объекты ADO)
Представляет один из способов, в котором члены [измерения](../../../ado/reference/ado-md-api/dimension-object-ado-md.md) может быть статистическая обработка или «накоплены.» Измерение может быть статистически вычислена вдоль одной или нескольким иерархиям.  
  
## <a name="remarks"></a>Примечания  
 С помощью коллекций и свойств **иерархии** объекта, можно сделать следующее:  
  
-   Определить **иерархии** с [имя](../../../ado/reference/ado-md-api/name-property-ado-md.md) и [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) свойства.  
  
-   Возвращать осмысленные строку, описывающую **иерархии** с [описание](../../../ado/reference/ado-md-api/description-property-ado-md.md) свойство.  
  
-   Вернуть [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md) объекты, составляющие **иерархии** с [уровни](../../../ado/reference/ado-md-api/levels-collection-ado-md.md) коллекции.  
  
-   Используйте стандартные ADO [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции для получения дополнительных сведений о **иерархии** объекта.  
  
 **Свойства** коллекция содержит свойства, предоставляемые поставщиком. Ниже перечислены свойства, которые могут быть доступны. В списке свойств фактическое может различаться в зависимости от реализации поставщика. См. в документации поставщика более полный список доступных свойств.  
  
|Имя|Описание|  
|----------|-----------------|  
|AllMember|Элемент, на самом высоком уровне свертки в иерархии.|  
|CatalogName|Имя каталога, к которому принадлежит этот куб.|  
|CubeName|Имя куба.|  
|DefaultMember|Уникальное имя элемента по умолчанию для этой иерархии.|  
|Описание|Понятное описание иерархии.|  
|DimensionType|Тип измерения, к которому принадлежит эта иерархия.|  
|DimensionUniqueName|Однозначный имя измерения.|  
|HierarchyCaption|Метка или заголовок, связанный с иерархией.|  
|HierarchyCardinality|Количество элементов в иерархии.|  
|HierarchyGUID|Идентификатор GUID иерархии.|  
|HierarchyName|Имя иерархии.|  
|HierarchyUniqueName|Однозначный имя иерархии.|  
|SchemaName|Имя схемы, которой принадлежит этот куб.|  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/hierarchy-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример объекта CubeDef (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Объект Dimension (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [Коллекция hierarchies (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)   
 [Коллекция Levels (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
