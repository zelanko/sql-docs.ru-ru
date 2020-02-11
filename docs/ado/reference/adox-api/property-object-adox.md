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
ms.openlocfilehash: b7911608970e9860d7eddcf3e83156ac99645c3f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67965397"
---
# <a name="property-object-adox"></a>Объект Property (ADOX)
Представляет характеристику объекта ADOX.  
  
## <a name="remarks"></a>Remarks  
 Объекты ADOX имеют два типа свойств: встроенные и динамические.  
  
 Встроенные свойства — это свойства, которые немедленно доступны для любого нового объекта с помощью синтаксиса MyObject. Property. Они не отображаются как объекты свойств в [коллекции свойств](../../../ado/reference/ado-api/properties-collection-ado.md)объекта, поэтому, хотя их значения можно изменять, их характеристики изменить нельзя.  
  
 Динамические свойства определяются базовым поставщиком данных и отображаются в коллекции Properties для соответствующего объекта ADOX.  На динамические свойства можно ссылаться только через коллекцию с помощью синтаксиса MyObject. Properties (0) или MyObject. Properties ("имя").  
  
 Нельзя удалить оба типа свойств.  
  
 Объект динамического свойства имеет четыре встроенных свойства.  
  
 Свойство [Name](../../../ado/reference/ado-api/name-property-ado.md) — это строка, идентифицирующая свойство.  
  
 Свойство [Type](../../../ado/reference/ado-api/type-property-ado.md) — это целое число, указывающее тип данных свойства.  
  
 Свойство [value](../../../ado/reference/ado-api/value-property-ado.md) — это вариант, который содержит значение свойства. Value является свойством по умолчанию для объекта Property.  
  
 Свойство [Attributes](../../../ado/reference/ado-api/attributes-property-ado.md) является длинным значением, указывающим характеристики свойства, характерного для поставщика.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Property (ADOX)](../../../ado/reference/adox-api/adox-property-object-properties-methods-and-events.md)
