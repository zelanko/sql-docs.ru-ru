---
description: Свойство Name (ADO)
title: Свойство Name (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Name
- Field20::Name
helpviewer_keywords:
- Name property [ADO]
ms.assetid: cfd0e29c-8310-44ab-85c3-5761184b865d
author: rothja
ms.author: jroth
ms.openlocfilehash: da88b8e5a98e7d3ae105cc6e826804158f4bf7c8
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774173"
---
# <a name="name-property-ado"></a>Свойство Name (ADO)
Указывает имя объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает **строковое** значение, указывающее имя объекта.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **Name** , чтобы присвоить имя или получить имя **команды**, **Свойства**, **поля**или объекта **параметра** .  
  
 Значение доступно для чтения и записи в объекте **Command** и доступно только для чтения в объекте **Property** .  
  
 Для объекта **поля** **имя** обычно доступно только для чтения. Однако для новых объектов **field** , которые были добавлены в коллекцию [Fields](./fields-collection-ado.md) [записи](./record-object-ado.md), **имя** доступно только для чтения и записи только после того, как свойство [value](./value-property-ado.md) для **поля** было указано и поставщик данных успешно добавил новое **поле** путем вызова метода [Update](./update-method.md) коллекции **Fields** .  
  
 Для объектов **параметров** , которые еще не добавлены в коллекцию [Parameters](./parameters-collection-ado.md) , свойство **Name** доступно для чтения и записи. Для добавленных объектов **параметров** и всех остальных объектов свойство **Name** доступно только для чтения. Имена не обязательно должны быть уникальными в пределах коллекции.  
  
 Свойство **Name** объекта можно получить по порядковому номеру, после чего можно будет ссылаться на объект непосредственно по имени. Например, если `rstMain.Properties(20).Name` возвращает `Updatability` , то в дальнейшем можно ссылаться на это свойство как на `rstMain.Properties("Updatability")` .  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Command (ADO)](./command-object-ado.md)  
        [Объект Field](./field-object.md)  
    :::column-end:::
    :::column:::
        [Объект Parameter](./parameter-object.md)  
        [Объект Property (ADO)](./property-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также  
 [Пример атрибутов и свойств имени (Visual Basic)](./attributes-and-name-properties-example-vb.md)   
 [Пример атрибутов и свойств имени (Visual c++)](./attributes-and-name-properties-example-vc.md)