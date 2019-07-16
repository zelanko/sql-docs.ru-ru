---
title: Уровень объекта (многомерные Объекты ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Level
helpviewer_keywords:
- Level object [ADO MD]
ms.assetid: 37815869-ed30-45fd-9aea-0a986c1b305c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4a44060ae4ffd9399c34d4cd8133f5ad7404ed5a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67949605"
---
# <a name="level-object-ado-md"></a>Объект Level (многомерные объекты ADO)
Содержит набор элементов, каждый из которых имеет один и тот же ранг в иерархии.  
  
## <a name="remarks"></a>Примечания  
 С помощью коллекций и свойств **уровень** объекта, можно сделать следующее:  
  
-   Определить **уровень** с [имя](../../../ado/reference/ado-md-api/name-property-ado-md.md) и [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) свойства.  
  
-   Возвращает строку, используемый при отображении **уровень** с [заголовок](../../../ado/reference/ado-md-api/caption-property-ado-md.md) свойство.  
  
-   Возвращать осмысленные строку, описывающую **уровень** с [описание](../../../ado/reference/ado-md-api/description-property-ado-md.md) свойство.  
  
-   Вернуть [член](../../../ado/reference/ado-md-api/member-object-ado-md.md) объекты, составляющие **уровень** с [члены](../../../ado/reference/ado-md-api/members-collection-ado-md.md) коллекции.  
  
-   Возвращает количество уровней из корня **уровень** с [глубина](../../../ado/reference/ado-md-api/depth-property-ado-md.md) свойство.  
  
-   Используйте стандартные ADO [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции для получения дополнительных сведений о **уровень** объекта.  
  
 **Свойства** коллекция содержит свойства, предоставляемые поставщиком. Ниже перечислены свойства, которые могут быть доступны. В списке свойств фактическое может различаться в зависимости от реализации поставщика. См. в документации поставщика более полный список доступных свойств.  
  
|Name|Описание|  
|----------|-----------------|  
|CatalogName|Имя каталога, к которому принадлежит этот куб.|  
|CubeName|Имя куба.|  
|Описание|Понятное описание уровня.|  
|DimensionUniqueName|Имя однозначно [измерения](../../../ado/reference/ado-md-api/dimension-object-ado-md.md).|  
|HierarchyUniqueName|Однозначный имя иерархии.|  
|LevelCaption|Метка или заголовок, связанный с уровнем.|  
|LevelCardinality|Число элементов уровня.|  
|LevelGUID|Идентификатор GUID уровня.|  
|LevelName|Имя уровня.|  
|LevelNumber|Расстояние между уровнем и корень иерархии.|  
|LevelType|Тип уровня.|  
|LevelUniqueName|Однозначный имя уровня.|  
|SchemaName|Имя схемы, которой принадлежит этот куб.|  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/level-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример объекта CubeDef (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Объект Hierarchy (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)   
 [Коллекция Levels (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)   
 [Коллекция Members (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
