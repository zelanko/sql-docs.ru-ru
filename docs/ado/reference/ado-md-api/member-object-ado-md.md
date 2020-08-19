---
description: Объект Member (многомерные объекты ADO)
title: Объект Member (объекты данных ActiveX (MD)) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 6e0797a4d273c51b950e3973d1864480755a20d1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440926"
---
# <a name="member-object-ado-md"></a>Объект Member (многомерные объекты ADO)
Представляет элемент уровня в Кубе, дочерние элементы элемента уровня или элемента в положении вдоль оси набора ячеек.  
  
## <a name="remarks"></a>Комментарии  
 Свойства **элемента** различаются в зависимости от контекста, в котором он используется. **Элемент** [уровня](../../../ado/reference/ado-md-api/level-object-ado-md.md) в [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) имеет [дочернее](../../../ado/reference/ado-md-api/children-property-ado-md.md) свойство, возвращающее **элементы** следующего нижнего уровня иерархии из текущего **элемента**. Для **элемента** в [положении](../../../ado/reference/ado-md-api/position-object-ado-md.md)коллекция **Children** всегда пуста. Кроме того, свойство [Type](../../../ado/reference/ado-md-api/type-property-ado-md.md) применяется только к **элементам** **уровня**.  
  
 **Элемент** в **положении** имеет два свойства, которые полезны при отображении набора [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md): [дрилледдовн](../../../ado/reference/ado-md-api/drilleddown-property-ado-md.md) и [парентсамеаспрев](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md). Если доступ к этим свойствам осуществляется на **члене** **уровня**, возникнет ошибка.  
  
 С помощью коллекций и свойств объекта- **члена** **уровня**можно выполнить следующие действия.  
  
-   Найдите **элемент** с помощью свойств [Name](../../../ado/reference/ado-md-api/name-property-ado-md.md) и [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) .  
  
-   Возвращает строку, используемую при отображении **элемента** со свойством [Caption](../../../ado/reference/ado-md-api/caption-property-ado-md.md) .  
  
-   Возвращает осмысленную строку, описывающую **элемент** меры или формулы со свойством [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md) .  
  
-   Определите природу **элемента** с помощью свойства [Type](../../../ado/reference/ado-md-api/type-property-ado-md.md) .  
  
-   Получение сведений о **уровне** **элемента** с помощью свойств [LevelDepth](../../../ado/reference/ado-md-api/leveldepth-property-ado-md.md) и [LevelName](../../../ado/reference/ado-md-api/levelname-property-ado-md.md) .  
  
-   Получение связанных **элементов** в [иерархии](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md) с [родительскими](../../../ado/reference/ado-md-api/parent-property-ado-md.md) и [дочерними](../../../ado/reference/ado-md-api/children-property-ado-md.md) свойствами.  
  
-   Подсчитайте, что дочерние **элементы элемента имеют свойство** [ChildCount](../../../ado/reference/ado-md-api/childcount-property-ado-md.md) .  
  
-   Используйте стандартную коллекцию [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) ADO для получения дополнительных сведений об объекте **Level** .  
  
 С помощью коллекций и свойств **элемента** в **положении** вдоль [оси](../../../ado/reference/ado-md-api/axis-object-ado-md.md)можно выполнить следующие действия.  
  
-   Найдите **элемент** с помощью свойств [Name](../../../ado/reference/ado-md-api/name-property-ado-md.md) и [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) .  
  
-   Возвращает строку, используемую при отображении **элемента** со свойством [Caption](../../../ado/reference/ado-md-api/caption-property-ado-md.md) .  
  
-   Возвращает осмысленную строку, описывающую **элемент** меры или формулы со свойством [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md) .  
  
-   Получение сведений о **уровне** **элемента** с помощью свойств [LevelDepth](../../../ado/reference/ado-md-api/leveldepth-property-ado-md.md) и [LevelName](../../../ado/reference/ado-md-api/levelname-property-ado-md.md) .  
  
-   Подсчитайте, что дочерние **элементы элемента имеют свойство** [ChildCount](../../../ado/reference/ado-md-api/childcount-property-ado-md.md) .  
  
-   Используйте свойство [дрилледдовн](../../../ado/reference/ado-md-api/drilleddown-property-ado-md.md) , чтобы определить, имеется ли по крайней мере один дочерний элемент на **оси** , которая сразу после этого **элемента**.  
  
-   Используйте свойство [парентсамеаспрев](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md) , чтобы определить, совпадает ли родительский элемент этого **элемента** со родителем непосредственно предшествующего ему **члена**.  
  
-   Используйте стандартную коллекцию [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) ADO для получения дополнительных сведений об объекте **Level** .  
  
 Коллекция **Properties** содержит свойства, предоставляемые поставщиком. В следующей таблице перечислены свойства, которые могут быть доступны. Фактический список свойств может отличаться в зависимости от реализации поставщика. Более полный список доступных свойств см. в документации поставщика.  
  
|Имя|Описание|  
|----------|-----------------|  
|CatalogName|Имя каталога, которому принадлежит куб.|  
|чилдренкардиналити|Количество потомков элемента.|  
|CubeName|Имя куба.|  
|Описание|Понятное описание элемента.|  
|дименсионуникуенаме|Однозначное имя [измерения](../../../ado/reference/ado-md-api/dimension-object-ado-md.md).|  
|хиерарчюникуенаме|Однозначное имя иерархии.|  
|LevelNumber|Расстояние между уровнем и корнем иерархии.|  
|LevelUniqueName|Однозначное имя уровня.|  
|мемберкаптион|Метка или заголовок, связанный с элементом.|  
|мембергуид|Идентификатор GUID элемента.|  
|MemberName|Имя элемента.|  
|мемберординал|Порядковый номер элемента.|  
|MemberType|Тип элемента.|  
|мемберуникуенаме|Однозначное имя элемента.|  
|паренткаунт|Количество родительских элементов данного элемента.|  
|ParentLevel|Номер уровня родителя элемента.|  
|ParentUniqueName|Однозначное имя родителя элемента.|  
|SchemaName|Имя схемы, к которой принадлежит куб.|  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/member-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример каталога (VB)](../../../ado/reference/ado-md-api/catalog-example-vb.md)   
 [Коллекция Members (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/members-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
