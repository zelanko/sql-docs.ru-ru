---
description: Свойство NativeError (ADO)
title: Свойство NativeError (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::GetNativeError
- Error::get_NativeError
- Error::NativeError
helpviewer_keywords:
- NativeError property [ADO]
ms.assetid: b9b47e57-18a4-4186-aef5-5bd18d7b1d74
author: rothja
ms.author: jroth
ms.openlocfilehash: f26e8ab07a5ac51307d3b3da374e982ea5b6f469
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443116"
---
# <a name="nativeerror-property-ado"></a>Свойство NativeError (ADO)
Указывает код ошибки конкретного поставщика для данного объекта [ошибки](../../../ado/reference/ado-api/error-object.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение **типа Long** , указывающее код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **NativeError** , чтобы получить сведения об ошибке конкретной базы данных для конкретного объекта **ошибки** . Например, при использовании поставщика Microsoft ODBC для OLE DB с базой данных Microsoft SQL Server, машинные коды ошибок, происходящие из SQL Server, проходят через ODBC и поставщик ODBC в свойство ADO **NativeError** .  
  
## <a name="applies-to"></a>Применение  
 [Объект Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>См. также:  
 [Примеры свойств Description, HelpContext, HelpFile, NativeError, Number, Source и SQLState (Visual Basic)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Примеры свойств Description, HelpContext, HelpFile, NativeError, Number, Source и SQLState (Visual c++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
