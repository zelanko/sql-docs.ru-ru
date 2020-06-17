---
title: Свойство Description | Документация Майкрософт
description: Сведения о свойстве Description объекта Error в ADO, возвращающем строковое значение, содержащее описание ошибки.
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::Description
- Error::GetDescription
- Error::get_Description
helpviewer_keywords:
- Description property
ms.assetid: 4b5d6790-6c29-42aa-bf78-d9cfb8ad7965
author: rothja
ms.author: jroth
ms.openlocfilehash: 5bbaa998c419ba1a0af49ffa28e32fe91ffc96b9
ms.sourcegitcommit: 5c7634b007f6808c87094174b80376cb20545d5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84880543"
---
# <a name="description-property"></a>Свойство Description
Описывает объект [Error](../../../ado/reference/ado-api/error-object.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **строковое** значение, содержащее описание ошибки.  
  
## <a name="remarks"></a>Комментарии  
 Используйте свойство **Description** для получения краткого описания ошибки. Отобразить это свойство, чтобы предупредить пользователя об ошибке, которую нельзя или не требуется обменять. Строка будет поступать из ADO или поставщика.  
  
 Поставщики несут ответственность за передачу конкретного текста ошибок в ADO. ADO добавляет объект [Error](../../../ado/reference/ado-api/error-object.md) в коллекцию **Errors** для каждой ошибки поставщика или предупреждения, которое она получает. Перечислите коллекцию **Errors** , чтобы отслеживать ошибки, передаваемые поставщиком.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>См. также:  
 [Примеры свойств Description, HelpContext, HelpFile, NativeError, Number, Source и SQLState (Visual Basic)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Примеры свойств Description, HelpContext, HelpFile, NativeError, Number, Source и SQLState (Visual c++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Свойства HelpContext, HelpFile](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Свойство Number (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Свойство Source (объект Error ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)
