---
title: Объект Property (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Property
helpviewer_keywords:
- Property object [ADO]
ms.assetid: b2a4767c-03c7-4935-a3bc-df3e1a38a009
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5abbc13ac3ba9690f341e365ee14b0b72fcc6ca8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47695652"
---
# <a name="property-object-ado"></a>Объект Property (ADO)
Представляет характеристику динамического объекта ADO, определенной поставщиком.  
  
## <a name="remarks"></a>Примечания  
 Объекты ADO имеют два типа свойств: встроенные и динамические.  
  
 Встроенные свойства являются те свойства, реализованного в ADO и сразу становятся доступными для любого new объекта используются `MyObject.Property` синтаксис. Они не отображаются как **свойство** объектов в объекта [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции, поэтому несмотря на то, что можно изменить их значения, вы не можете изменять их характеристик.  
  
 Динамические свойства определяются базового поставщика данных и отображаются в **свойства** коллекции на соответствующий объект ADO. Например, свойство поставщика может указывать, если [записей](../../../ado/reference/ado-api/recordset-object-ado.md) поддерживает объект транзакции или обновление. Эти дополнительные свойства будет отображаться как **свойство** объектов, в который **записей** объекта **свойства** коллекции. Динамические свойства можно ссылаться только с помощью коллекции, с помощью `MyObject.Properties(0)` или `MyObject.Properties("Name")` синтаксис.  
  
 Не удается удалить любой тип свойства.  
  
 Динамический **свойство** объект имеет четыре встроенных собственными свойствами:  
  
-   [Имя](../../../ado/reference/ado-api/name-property-ado.md) свойство является строка, определяющая свойство.  
  
-   [Тип](../../../ado/reference/ado-api/type-property-ado.md) свойство должно быть целым числом, которое указывает тип данных свойства.  
  
-   [Значение](../../../ado/reference/ado-api/value-property-ado.md) свойство является переменная типа variant, содержащий значение свойства. **Значение** является свойством по умолчанию для **свойство** объекта.  
  
-   [Атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md) свойства является значение типа long, указывающее характеристики поставщика свойства.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Объект свойства, методы и события](../../../ado/reference/ado-api/property-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Объект field](../../../ado/reference/ado-api/field-object.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
