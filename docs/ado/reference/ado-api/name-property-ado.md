---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a919bb377eee2da1c3c1a65e85ddfb9807ed8d50
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918033"
---
# <a name="name-property-ado"></a>Свойство Name (ADO)
Указывает имя объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает **строковое** значение, указывающее имя объекта.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **Name** , чтобы присвоить имя или получить имя **команды**, **Свойства**, **поля**или объекта **параметра** .  
  
 Значение доступно для чтения и записи в объекте **Command** и доступно только для чтения в объекте **Property** .  
  
 Для объекта **поля** **имя** обычно доступно только для чтения. Однако для новых объектов **field** , которые были добавлены в коллекцию [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) [записи](../../../ado/reference/ado-api/record-object-ado.md), **имя** доступно только для чтения и записи только после того, как свойство [value](../../../ado/reference/ado-api/value-property-ado.md) для **поля** было указано и поставщик данных успешно добавил новое **поле** путем вызова метода [Update](../../../ado/reference/ado-api/update-method.md) коллекции **Fields** .  
  
 Для объектов **параметров** , которые еще не добавлены в коллекцию [Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md) , свойство **Name** доступно для чтения и записи. Для добавленных объектов **параметров** и всех остальных объектов свойство **Name** доступно только для чтения. Имена не обязательно должны быть уникальными в пределах коллекции.  
  
 Свойство **Name** объекта можно получить по порядковому номеру, после чего можно будет ссылаться на объект непосредственно по имени. Например, если `rstMain.Properties(20).Name` возвращает `Updatability`, то в дальнейшем можно ссылаться на это свойство как `rstMain.Properties("Updatability")`на.  
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Объект Field](../../../ado/reference/ado-api/field-object.md)|  
|[Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)|[Объект Property (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>См. также:  
 [Пример атрибутов и свойств имени (Visual Basic)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vb.md)   
 [Пример атрибутов и свойств имени (Visual c++)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vc.md)   
