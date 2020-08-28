---
description: Объект Member (многомерные объекты ADO)
title: Объект Member (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 784dd3e842547c97f26107beaec67767363ce4ea
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88986465"
---
# <a name="member-object-ado-md"></a>Объект Member (многомерные объекты ADO)
Представляет элемент уровня в Кубе, дочерние элементы элемента уровня или элемента в положении вдоль оси набора ячеек.  
  
## <a name="remarks"></a>Remarks  
 Свойства **элемента** различаются в зависимости от контекста, в котором он используется. **Элемент** [уровня](./level-object-ado-md.md) в [CubeDef](./cubedef-object-ado-md.md) имеет [дочернее](./children-property-ado-md.md) свойство, возвращающее **элементы** следующего нижнего уровня иерархии из текущего **элемента**. Для **элемента** в [положении](./position-object-ado-md.md)коллекция **Children** всегда пуста. Кроме того, свойство [Type](./type-property-ado-md.md) применяется только к **элементам** **уровня**.  
  
 **Элемент** в **положении** имеет два свойства, которые полезны при отображении набора [ячеек](./cellset-object-ado-md.md): [дрилледдовн](./drilleddown-property-ado-md.md) и [парентсамеаспрев](./parentsameasprev-property-ado-md.md). Если доступ к этим свойствам осуществляется на **члене** **уровня**, возникнет ошибка.  
  
 С помощью коллекций и свойств объекта- **члена** **уровня**можно выполнить следующие действия.  
  
-   Найдите **элемент** с помощью свойств [Name](./name-property-ado-md.md) и [UniqueName](./uniquename-property-ado-md.md) .  
  
-   Возвращает строку, используемую при отображении **элемента** со свойством [Caption](./caption-property-ado-md.md) .  
  
-   Возвращает осмысленную строку, описывающую **элемент** меры или формулы со свойством [Description](./description-property-ado-md.md) .  
  
-   Определите природу **элемента** с помощью свойства [Type](./type-property-ado-md.md) .  
  
-   Получение сведений о **уровне** **элемента** с помощью свойств [LevelDepth](./leveldepth-property-ado-md.md) и [LevelName](./levelname-property-ado-md.md) .  
  
-   Получение связанных **элементов** в [иерархии](./hierarchy-object-ado-md.md) с [родительскими](./parent-property-ado-md.md) и [дочерними](./children-property-ado-md.md) свойствами.  
  
-   Подсчитайте, что дочерние **элементы элемента имеют свойство** [ChildCount](./childcount-property-ado-md.md) .  
  
-   Используйте стандартную коллекцию [свойств](../ado-api/properties-collection-ado.md) ADO для получения дополнительных сведений об объекте **Level** .  
  
 С помощью коллекций и свойств **элемента** в **положении** вдоль [оси](./axis-object-ado-md.md)можно выполнить следующие действия.  
  
-   Найдите **элемент** с помощью свойств [Name](./name-property-ado-md.md) и [UniqueName](./uniquename-property-ado-md.md) .  
  
-   Возвращает строку, используемую при отображении **элемента** со свойством [Caption](./caption-property-ado-md.md) .  
  
-   Возвращает осмысленную строку, описывающую **элемент** меры или формулы со свойством [Description](./description-property-ado-md.md) .  
  
-   Получение сведений о **уровне** **элемента** с помощью свойств [LevelDepth](./leveldepth-property-ado-md.md) и [LevelName](./levelname-property-ado-md.md) .  
  
-   Подсчитайте, что дочерние **элементы элемента имеют свойство** [ChildCount](./childcount-property-ado-md.md) .  
  
-   Используйте свойство [дрилледдовн](./drilleddown-property-ado-md.md) , чтобы определить, имеется ли по крайней мере один дочерний элемент на **оси** , которая сразу после этого **элемента**.  
  
-   Используйте свойство [парентсамеаспрев](./parentsameasprev-property-ado-md.md) , чтобы определить, совпадает ли родительский элемент этого **элемента** со родителем непосредственно предшествующего ему **члена**.  
  
-   Используйте стандартную коллекцию [свойств](../ado-api/properties-collection-ado.md) ADO для получения дополнительных сведений об объекте **Level** .  
  
 Коллекция **Properties** содержит свойства, предоставляемые поставщиком. В следующей таблице перечислены свойства, которые могут быть доступны. Фактический список свойств может отличаться в зависимости от реализации поставщика. Более полный список доступных свойств см. в документации поставщика.  
  
|Имя|Описание|  
|----------|-----------------|  
|CatalogName|Имя каталога, которому принадлежит куб.|  
|чилдренкардиналити|Количество потомков элемента.|  
|CubeName|Имя куба.|  
|Описание|Понятное описание элемента.|  
|дименсионуникуенаме|Однозначное имя [измерения](./dimension-object-ado-md.md).|  
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
  
-   [Свойства, методы и события](./member-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример каталога (VB)](./catalog-example-vb.md)   
 [Коллекция Members (объекты данных ActiveX (MD))](./members-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../ado-api/properties-collection-ado.md)