---
title: "Свойства объекта (ADOX) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords: Property object [ADOX]
ms.assetid: 6a56def6-dbe6-4ccc-a491-8d076889f019
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 444fcb873db39f37aed1d7385027395d54cacffa
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="property-object-adox"></a>Свойства объекта (ADOX)
Представляет характеристику ADOX объекта.  
  
## <a name="remarks"></a>Замечания  
 ADOX объекты имеют два типа свойств: встроенные и динамические.  
  
 Встроенные свойства — это свойства, сразу становятся доступными для каждого нового объекта, используя синтаксис MyObject.Property. Они не отображаются как объекты свойств в объекте [коллекции свойств](../../../ado/reference/ado-api/properties-collection-ado.md), поэтому несмотря на то, что можно изменить их значения, вы не можете изменить их характеристики.  
  
 Динамические свойства определяются базового поставщика данных и отображаются в коллекции свойств на соответствующий объект ADOX.  Динамические свойства можно ссылаться только с помощью коллекции, используя синтаксис MyObject.Properties(0) или MyObject.Properties("Name").  
  
 Не удается удалить любой тип свойства.  
  
 Динамический объект свойств имеет четыре встроенных свойства свои собственные.  
  
 [Имя](../../../ado/reference/ado-api/name-property-ado.md) свойство является строка, определяющая свойство.  
  
 [Тип](../../../ado/reference/ado-api/type-property-ado.md) свойство является целое число, указывающее тип данных свойства.  
  
 [Значение](../../../ado/reference/ado-api/value-property-ado.md) свойство является вариантом, содержащий значение свойства. Значение является свойством по умолчанию для свойства объекта.  
  
 [Атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md) свойства является значение типа long, указывающее характеристики свойства, относящиеся к поставщику.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Property (ADOX)](../../../ado/reference/adox-api/adox-property-object-properties-methods-and-events.md)
