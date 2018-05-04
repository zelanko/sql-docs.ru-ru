---
title: Объект члена (ADO MD) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Member
helpviewer_keywords:
- Member object [ADO MD], members
ms.assetid: 3dedf755-0741-4c3f-8b4e-bff8ff8809c8
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9650c6c34d426004f30e22ce7b265bf26bfec77c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="member-object-ado-md"></a>Объект члена (ADO MD)
Представляет элемент в кубе, уровня дочерних элементов элемента уровня или членом положение вдоль оси набора ячеек.  
  
## <a name="remarks"></a>Замечания  
 Свойства **член** различаются в зависимости от контекста, в котором он используется. Объект **член** из [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md) в [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) имеет [дочерних](../../../ado/reference/ado-md-api/children-property-ado-md.md) свойство, которое возвращает **члены** на уровень ниже по иерархии из текущего **член**. Для **член** из [позиции](../../../ado/reference/ado-md-api/position-object-ado-md.md), **дочерних** всегда возвращается пустая коллекция. Кроме того [тип](../../../ado/reference/ado-md-api/type-property-ado-md.md) свойство применяется только к **элементы** из **уровень**.  
  
 Объект **член** из **позиции** имеет два свойства, которые могут быть полезны при отображении [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md): [DrilledDown](../../../ado/reference/ado-md-api/drilleddown-property-ado-md.md) и [ ParentSameAsPrev](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md). Ошибка возникает в том случае, если эти свойства доступны на **член** из **уровень**.  
  
 С коллекциями и свойствами **член** объект **уровень**, можно сделать следующее:  
  
-   Определить **член** с [имя](../../../ado/reference/ado-md-api/name-property-ado-md.md) и [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) свойства.  
  
-   Возвращает строку, используемую при отображении **член** с [заголовок](../../../ado/reference/ado-md-api/caption-property-ado-md.md) свойство.  
  
-   Возвращать значимое строку, описывающую мера или формулу **член** с [описание](../../../ado/reference/ado-md-api/description-property-ado-md.md) свойство.  
  
-   Определить природу **член** с [тип](../../../ado/reference/ado-md-api/type-property-ado-md.md) свойства.  
  
-   Получить сведения о **уровень** из **член** с [LevelDepth](../../../ado/reference/ado-md-api/leveldepth-property-ado-md.md) и [LevelName](../../../ado/reference/ado-md-api/levelname-property-ado-md.md) свойства.  
  
-   Получить связанные **элементы** в [иерархии](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md) с [родительского](../../../ado/reference/ado-md-api/parent-property-ado-md.md) и [дочерних](../../../ado/reference/ado-md-api/children-property-ado-md.md) свойства.  
  
-   Число дочерних элементов **член** с [ChildCount](../../../ado/reference/ado-md-api/childcount-property-ado-md.md) свойство.  
  
-   Используйте стандартные ADO [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции для получения дополнительных сведений о **уровень** объекта.  
  
 С коллекциями и свойствами **член** из **позиции** вдоль [оси](../../../ado/reference/ado-md-api/axis-object-ado-md.md), можно выполнять следующие:  
  
-   Определить **член** с [имя](../../../ado/reference/ado-md-api/name-property-ado-md.md) и [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) свойства.  
  
-   Возвращает строку, используемую при отображении **член** с [заголовок](../../../ado/reference/ado-md-api/caption-property-ado-md.md) свойство.  
  
-   Возвращать значимое строку, описывающую мера или формулу **член** с [описание](../../../ado/reference/ado-md-api/description-property-ado-md.md) свойство.  
  
-   Получить сведения о **уровень** из **член** с [LevelDepth](../../../ado/reference/ado-md-api/leveldepth-property-ado-md.md) и [LevelName](../../../ado/reference/ado-md-api/levelname-property-ado-md.md) свойства.  
  
-   Число дочерних элементов **член** с [ChildCount](../../../ado/reference/ado-md-api/childcount-property-ado-md.md) свойство.  
  
-   Используйте [DrilledDown](../../../ado/reference/ado-md-api/drilleddown-property-ado-md.md) свойства, чтобы определить, имеются ли хотя бы один дочерний **оси** сразу после этого **член**.  
  
-   Используйте [ParentSameAsPrev](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md) свойства, чтобы определить ли родительским для данного **член** совпадает со значением родительского элемента, непосредственно предшествующего **член**.  
  
-   Используйте стандартные ADO [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции для получения дополнительных сведений о **уровень** объекта.  
  
 **Свойства** коллекция содержит указанный поставщик свойства. В следующей таблице перечислены свойства, которые могут быть доступны. Фактическое свойство списка могут различаться в зависимости от реализации поставщика. См. в документации для поставщика более полный список доступных свойств.  
  
|Название|Описание|  
|----------|-----------------|  
|CatalogName|Имя каталога, к которому принадлежит этот куб.|  
|ChildrenCardinality|Количество потомков элемента.|  
|CubeName|Имя куба.|  
|Описание|Понятное описание элемента.|  
|DimensionUniqueName|Однозначная имя [измерения](../../../ado/reference/ado-md-api/dimension-object-ado-md.md).|  
|HierarchyUniqueName|Однозначная имя иерархии.|  
|LevelNumber|Расстояние между уровнем и корневого элемента иерархии.|  
|LevelUniqueName|Однозначная имя уровня.|  
|MemberCaption|Метка или заголовок, связанный с элементом.|  
|MemberGUID|Идентификатор GUID элемента.|  
|MemberName|Имя элемента.|  
|MemberOrdinal|Порядковый номер элемента.|  
|Тип элемента|Тип элемента.|  
|MemberUniqueName|Однозначная имя элемента.|  
|ParentCount|Счетчик количество родительских элементов данного элемента.|  
|ParentLevel|Номер уровня родительского элемента данного элемента.|  
|ParentUniqueName|Однозначная имя родительского элемента данного элемента.|  
|SchemaName|Имя схемы, которой принадлежит этот куб.|  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/member-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример каталога (Visual Basic)](../../../ado/reference/ado-md-api/catalog-example-vb.md)   
 [Члены коллекции (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
