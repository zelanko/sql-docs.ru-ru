---
title: Коллекция Members (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Level::Members
- Members
- Position::Members
helpviewer_keywords:
- Members collection [ADO MD]
ms.assetid: 3a647cde-efdc-4394-b1b9-8cbb1b9d689f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 79394abee5b12bb10f34a34e882d2ac0562722fe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67949435"
---
# <a name="members-collection-ado-md"></a>Коллекция Members (многомерные объекты ADO)
Содержит объекты- [члены](../../../ado/reference/ado-md-api/member-object-ado-md.md) уровня или расположения вдоль оси.  
  
## <a name="remarks"></a>Remarks  
 Коллекция **Members** используется для хранения следующих типов членов:  
  
-   Элементы, составляющие уровень в Кубе. Они содержатся в коллекции **Members** объекта [Level](../../../ado/reference/ado-md-api/level-object-ado-md.md) . Например, используя пример из [обзора многомерных схем и данных](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md), четыре элемента уровня «страны» — это Канада, США, Великобритания и Германия.  
  
-   Элементы, являющиеся дочерними элементами определенного элемента в иерархии. Эти члены возвращаются свойством [Children](../../../ado/reference/ado-md-api/children-property-ado-md.md) родительского объекта **member** . Например, при использовании одного и того же примера два дочерних элемента в Канаде — Канада-Восток и Канада-Запад.  
  
-   Элементы, определяющие определенную позицией вдоль оси набора [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md). Используя набор ячеек для [работы с многомерными данными](../../../ado/guide/multidimensional/working-with-multidimensional-data.md) в качестве примера, два элемента первой должности на оси x — любимая и Сиэтл. Эти элементы содержатся в коллекции **Members** объекта [позиционирования](../../../ado/reference/ado-md-api/position-object-ado-md.md) .  
  
 **Members** — это стандартная коллекция ADO. С помощью свойств и методов коллекции можно выполнять следующие действия.  
  
-   Получите количество объектов в коллекции со свойством [Count](../../../ado/reference/ado-api/count-property-ado.md) .  
  
-   Возврат объекта из коллекции со свойством [элемента](../../../ado/reference/ado-api/item-property-ado.md) по умолчанию.  
  
-   Обновите объекты в коллекции от поставщика с помощью метода [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) .  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/members-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример членов (VBScript)](../../../ado/reference/ado-md-api/members-example-vbscript.md)   
 [Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)
