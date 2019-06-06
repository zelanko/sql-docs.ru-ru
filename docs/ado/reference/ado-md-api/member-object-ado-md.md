---
title: Объект-член (многомерные Объекты ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Member
helpviewer_keywords:
- Member object [ADO MD], members
ms.assetid: 3dedf755-0741-4c3f-8b4e-bff8ff8809c8
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f8d11e97fd31745752449c5649e1096d0bb667a8
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66709027"
---
# <a name="member-object-ado-md"></a>Объект Member (многомерные объекты ADO)
Представляет элемент уровня в кубе, дочерние элементы элемента уровня или членом положение вдоль оси набора ячеек.  
  
## <a name="remarks"></a>Примечания  
 Свойства **член** различаться в зависимости от контекста, в котором оно использовано. Объект **член** из [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md) в [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) имеет [дочерние элементы](../../../ado/reference/ado-md-api/children-property-ado-md.md) свойство, которое возвращает **члены** на следующий нижний уровень в иерархии из текущего **член**. Для **член** из [позиции](../../../ado/reference/ado-md-api/position-object-ado-md.md), **дочерние элементы** всегда возвращается пустая коллекция. Кроме того [тип](../../../ado/reference/ado-md-api/type-property-ado-md.md) свойство применяется только к **члены** из **уровень**.  
  
 Объект **член** из **позиции** имеет два свойства, которые полезны при отображении [набора ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md): [DrilledDown](../../../ado/reference/ado-md-api/drilleddown-property-ado-md.md) и [ParentSameAsPrev](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md). Произойдет ошибка, если эти свойства доступны на **член** из **уровень**.  
  
 С помощью коллекций и свойств **член** объект **уровень**, можно выполнять следующие:  
  
-   Определить **член** с [имя](../../../ado/reference/ado-md-api/name-property-ado-md.md) и [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) свойства.  
  
-   Возвращает строку, используемый при отображении **член** с [заголовок](../../../ado/reference/ado-md-api/caption-property-ado-md.md) свойство.  
  
-   Возвращать осмысленные строку, описывающую мера или формула **член** с [описание](../../../ado/reference/ado-md-api/description-property-ado-md.md) свойство.  
  
-   Определить характер **член** с [тип](../../../ado/reference/ado-md-api/type-property-ado-md.md) свойства.  
  
-   Получения сведений о **уровень** из **член** с [LevelDepth](../../../ado/reference/ado-md-api/leveldepth-property-ado-md.md) и [LevelName](../../../ado/reference/ado-md-api/levelname-property-ado-md.md) свойства.  
  
-   Получить связанные **члены** в [иерархии](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md) с [родительского](../../../ado/reference/ado-md-api/parent-property-ado-md.md) и [дочерние элементы](../../../ado/reference/ado-md-api/children-property-ado-md.md) свойства.  
  
-   Количество дочерних элементов **член** с [ChildCount](../../../ado/reference/ado-md-api/childcount-property-ado-md.md) свойство.  
  
-   Используйте стандартные ADO [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции для получения дополнительных сведений о **уровень** объекта.  
  
 С помощью коллекций и свойств **член** из **позиции** вдоль [оси](../../../ado/reference/ado-md-api/axis-object-ado-md.md), можно выполнять следующие:  
  
-   Определить **член** с [имя](../../../ado/reference/ado-md-api/name-property-ado-md.md) и [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) свойства.  
  
-   Возвращает строку, используемый при отображении **член** с [заголовок](../../../ado/reference/ado-md-api/caption-property-ado-md.md) свойство.  
  
-   Возвращать осмысленные строку, описывающую мера или формула **член** с [описание](../../../ado/reference/ado-md-api/description-property-ado-md.md) свойство.  
  
-   Получения сведений о **уровень** из **член** с [LevelDepth](../../../ado/reference/ado-md-api/leveldepth-property-ado-md.md) и [LevelName](../../../ado/reference/ado-md-api/levelname-property-ado-md.md) свойства.  
  
-   Количество дочерних элементов **член** с [ChildCount](../../../ado/reference/ado-md-api/childcount-property-ado-md.md) свойство.  
  
-   Используйте [DrilledDown](../../../ado/reference/ado-md-api/drilleddown-property-ado-md.md) свойства, чтобы определить, имеются ли хотя бы один дочерний элемент **оси** после этого сразу же **член**.  
  
-   Используйте [ParentSameAsPrev](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md) свойства, чтобы определить ли родительский элемент данного **член** совпадает с родительским для объекта непосредственно перед **член**.  
  
-   Используйте стандартные ADO [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции для получения дополнительных сведений о **уровень** объекта.  
  
 **Свойства** коллекция содержит свойства, предоставляемые поставщиком. Ниже перечислены свойства, которые могут быть доступны. В списке свойств фактическое может различаться в зависимости от реализации поставщика. См. в документации поставщика более полный список доступных свойств.  
  
|Имя|Описание|  
|----------|-----------------|  
|CatalogName|Имя каталога, к которому принадлежит этот куб.|  
|ChildrenCardinality|Количество потомков элемента.|  
|CubeName|Имя куба.|  
|Описание|Понятное описание элемента.|  
|DimensionUniqueName|Имя однозначно [измерения](../../../ado/reference/ado-md-api/dimension-object-ado-md.md).|  
|HierarchyUniqueName|Однозначный имя иерархии.|  
|LevelNumber|Расстояние между уровнем и корень иерархии.|  
|LevelUniqueName|Однозначный имя уровня.|  
|MemberCaption|Метка или заголовок, связанный с элементом.|  
|MemberGUID|Идентификатор GUID элемента.|  
|MemberName|Имя элемента.|  
|MemberOrdinal|Порядковый номер элемента.|  
|Тип элемента|Тип элемента.|  
|MemberUniqueName|Однозначный имя члена.|  
|ParentCount|Число количество родительских элементов данного элемента.|  
|ParentLevel|Номер уровня родительского элемента.|  
|ParentUniqueName|Однозначный имя родительского элемента данного элемента.|  
|SchemaName|Имя схемы, которой принадлежит этот куб.|  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/member-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример каталога (Visual Basic)](../../../ado/reference/ado-md-api/catalog-example-vb.md)   
 [Коллекция Members (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
