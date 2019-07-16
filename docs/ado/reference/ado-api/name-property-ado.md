---
title: Имя свойства (ADO) | Документация Майкрософт
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67918033"
---
# <a name="name-property-ado"></a>Свойство Name (ADO)
Указывает имя объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение, указывающее имя объекта.  
  
## <a name="remarks"></a>Примечания  
 Используйте **имя** присвоить имя или извлечения имени свойства **команда**, **свойство**, **поле**, или **параметр**  объекта.  
  
 Значение доступно для чтения/записи на **команда** объект и только для чтения на **свойство** объекта.  
  
 Для **поле** объекта, **имя** обычно предназначены только для чтения. Тем не менее, для новых **поле** объекты, добавленные [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекцию [записи](../../../ado/reference/ado-api/record-object-ado.md), **имя** чтение и запись только после того, как [значение](../../../ado/reference/ado-api/value-property-ado.md) свойство для **поле** была определена и успешно добавил новый поставщик данных **поле** путем вызова [ Обновление](../../../ado/reference/ado-api/update-method.md) метод **поля** коллекции.  
  
 Для **параметр** объекты еще не добавляются к [параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекции, **имя** свойство доступно для чтения/записи. Для добавляется **параметр** объекты и все другие объекты **имя** свойство доступно только для чтения. Имена не обязательно должны быть уникальными в пределах коллекции.  
  
 Вы можете получить **имя** свойства объекта с порядковым номером, после чего можно ссылаться на объект непосредственно по имени. Например если `rstMain.Properties(20).Name` дает `Updatability`, впоследствии можно ссылаться на это свойство как `rstMain.Properties("Updatability")`.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Объект Field](../../../ado/reference/ado-api/field-object.md)|  
|[Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)|[Объект Property (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>См. также  
 [Примеры Attributes и Name свойства (Visual Basic)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vb.md)   
 [Примеры Attributes и Name свойства (Visual C++)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vc.md)   
