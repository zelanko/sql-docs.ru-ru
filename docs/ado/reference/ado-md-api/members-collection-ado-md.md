---
title: Коллекция Members (многомерные Объекты ADO) | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 541e1098dfd18210e7c07a0718ecd3add758c8a4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62659567"
---
# <a name="members-collection-ado-md"></a>Коллекция Members (многомерные объекты ADO)
Содержит [член](../../../ado/reference/ado-md-api/member-object-ado-md.md) объекты уровня или положение вдоль оси.  
  
## <a name="remarks"></a>Примечания  
 Объект **члены** коллекция используется должен содержать следующие элементы:  
  
-   Элементы, которые составляют уровень в кубе. Они содержатся в **члены** коллекцию [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md) объекта. Например, с помощью образца из [Общие сведения о многомерных схемы и данные](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md), четыре элемента уровня странах, Канада, США, Соединенное Королевство и Германии.  
  
-   Элементы, являющиеся дочерними для конкретного элемента в пределах иерархии. Эти члены возвращаются [дочерние элементы](../../../ado/reference/ado-md-api/children-property-ado-md.md) свойство родительского объекта **член** объекта. Например два дочерних элементов элемента Canada снова с помощью одного примера, являются Восточная Канада и Западная часть Канады.  
  
-   Элементы, которые определяют заданное положение вдоль оси из [cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md). С помощью набора ячеек из [работа с многомерными данными](../../../ado/guide/multidimensional/working-with-multidimensional-data.md) в качестве примера два члена первой позиции по оси x являются святого и Сиэтл. Эти элементы, содержащиеся в **члены** коллекцию [позиции](../../../ado/reference/ado-md-api/position-object-ado-md.md) объекта.  
  
 **Члены** является стандартной коллекции ADO. С помощью свойства и методы коллекции сделайте следующее:  
  
-   Получить число объектов в коллекции с [число](../../../ado/reference/ado-api/count-property-ado.md) свойство.  
  
-   Вернуть объект из коллекции со значением по умолчанию [элемент](../../../ado/reference/ado-api/item-property-ado.md) свойство.  
  
-   Обновление объектов в коллекции от поставщика с [обновить](../../../ado/reference/ado-api/refresh-method-ado.md) метод.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/members-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример коллекции Members (VBScript)](../../../ado/reference/ado-md-api/members-example-vbscript.md)   
 [Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)
