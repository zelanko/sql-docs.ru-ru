---
title: Свойства объекта (ADO) | Документы Microsoft
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
- Property
helpviewer_keywords:
- Property object [ADO]
ms.assetid: b2a4767c-03c7-4935-a3bc-df3e1a38a009
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 774ed0d33d3066f600c6af98ea89b91a2770ed3c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="property-object-ado"></a>Свойства объекта (ADO)
Представляет динамический характеристику объекта ADO, определенной поставщиком.  
  
## <a name="remarks"></a>Замечания  
 Объекты ADO, имеют два типа свойств: встроенные и динамические.  
  
 Встроенные свойства, эти свойства, реализованные в ADO и сразу становятся доступными для любого нового объекта используются `MyObject.Property` синтаксиса. Они не отображаются как **свойство** объектов в объекте [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции, несмотря на то, что можно изменить их значения, который нельзя изменять их характеристики.  
  
 Динамические свойства определяются базового поставщика данных и отображаются в **свойства** коллекции на соответствующий объект ADO. Например, свойства, относящиеся к поставщику может указывать, если [записей](../../../ado/reference/ado-api/recordset-object-ado.md) поддерживает объект транзакции или обновление. Эти дополнительные свойства будет отображаться как **свойство** объектов в том, что **записей** объекта **свойства** коллекции. Динамические свойства можно ссылаться только с помощью коллекции, используя `MyObject.Properties(0)` или `MyObject.Properties("Name")` синтаксиса.  
  
 Не удается удалить любой тип свойства.  
  
 Динамический **свойство** объект имеет четыре встроенных собственными свойствами:  
  
-   [Имя](../../../ado/reference/ado-api/name-property-ado.md) свойство является строка, определяющая свойство.  
  
-   [Тип](../../../ado/reference/ado-api/type-property-ado.md) свойство является целое число, указывающее тип данных свойства.  
  
-   [Значение](../../../ado/reference/ado-api/value-property-ado.md) свойство является вариантом, содержащий значение свойства. **Значение** является свойством по умолчанию для **свойство** объекта.  
  
-   [Атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md) свойства является значение типа long, указывающее характеристики свойства, относящиеся к поставщику.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства объекта свойства, методы и события](../../../ado/reference/ado-api/property-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Объект команды (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Объект field](../../../ado/reference/ado-api/field-object.md)   
 [Коллекция свойств (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
