---
title: Объект Property (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Property object [ADOX]
ms.assetid: 6a56def6-dbe6-4ccc-a491-8d076889f019
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2502dcdab170102f526aa1ea0fe67235e6bf3048
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63281912"
---
# <a name="property-object-adox"></a>Объект Property (ADOX)
Представляет характеристику ADOX объекта.  
  
## <a name="remarks"></a>Примечания  
 Объекты ADOX имеют два типа свойств: встроенные и динамические.  
  
 Встроенные свойства — это свойства, сразу становятся доступными для каждого нового объекта, используя синтаксис MyObject.Property. Они не отображаются свойства в виде объектов объекта [коллекции свойств](../../../ado/reference/ado-api/properties-collection-ado.md), несмотря на то, что можно изменить их значения, который не может изменять их характеристик.  
  
 Динамические свойства определяются базового поставщика данных и отображаются в коллекции свойства для соответствующего объекта ADOX.  Динамические свойства можно ссылаться только с помощью коллекции, используя синтаксис MyObject.Properties(0) или MyObject.Properties("Name").  
  
 Не удается удалить любой тип свойства.  
  
 Динамический объект свойств имеет четыре встроенных собственными свойствами.  
  
 [Имя](../../../ado/reference/ado-api/name-property-ado.md) свойство является строка, определяющая свойство.  
  
 [Тип](../../../ado/reference/ado-api/type-property-ado.md) свойство должно быть целым числом, которое указывает тип данных свойства.  
  
 [Значение](../../../ado/reference/ado-api/value-property-ado.md) свойство является переменная типа variant, содержащий значение свойства. Значение является свойством по умолчанию для объекта свойства.  
  
 [Атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md) свойства является значение типа long, указывающее характеристики поставщика свойства.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события объекта Property (ADOX)](../../../ado/reference/adox-api/adox-property-object-properties-methods-and-events.md)
