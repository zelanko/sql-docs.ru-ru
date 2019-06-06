---
title: Измерение объекта (многомерные Объекты ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Dimension
helpviewer_keywords:
- Dimension object [ADO MD]
ms.assetid: 66adbbd2-23a3-4c19-a91b-84c31309aa1b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f69acfa84272e73bcafb370eb85c6a14614a367c
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66709433"
---
# <a name="dimension-object-ado-md"></a>Объект Dimension (многомерные объекты ADO)
Представляет одно из измерений многомерного куба, содержащего один или несколько иерархии элементов.  
  
## <a name="remarks"></a>Примечания  
 С помощью коллекций и свойств **измерения** объекта, можно выполнять следующие:  
  
-   Определить **измерения** с [имя](../../../ado/reference/ado-md-api/name-property-ado-md.md) и [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) свойства.  
  
-   Возвращать осмысленные строку, описывающую **измерения** с [описание](../../../ado/reference/ado-md-api/description-property-ado-md.md) свойство.  
  
-   Вернуть [иерархии](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md) объекты, составляющие **измерения** с [иерархий](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md) коллекции.  
  
-   Используйте стандартные ADO [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции для получения дополнительных сведений о **измерения** объекта.  
  
 **Свойства** коллекция содержит свойства, предоставляемые поставщиком. Ниже перечислены свойства, которые могут быть доступны. В списке свойств фактическое может различаться в зависимости от реализации поставщика. См. в документации поставщика более полный список доступных свойств.  
  
|Имя|Описание|  
|----------|-----------------|  
|CatalogName|Имя каталога, к которому принадлежит этот куб.|  
|CubeName|Имя куба.|  
|DefaultHierarchy|Уникальное имя иерархии по умолчанию.|  
|Описание|Понятное описание куба.|  
|DimensionCaption|Метка или заголовок, связанный с выбранным измерением.|  
|DimensionCardinality|Количество элементов в измерении.|  
|DimensionGUID|Идентификатор GUID измерения.|  
|Имя измерения|Имя измерения.|  
|DimensionOrdinal|Порядковый номер измерения между группе измерений, которые образуют куба.|  
|DimensionType|Тип измерения.|  
|DimensionUniqueName|Однозначный имя измерения.|  
|SchemaName|Имя схемы, которой принадлежит этот куб.|  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/dimension-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример объекта CubeDef (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Объект CubeDef (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)   
 [Коллекция Dimensions (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)   
 [Коллекция hierarchies (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
