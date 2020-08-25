---
description: Свойство SQLState
title: Свойство SQLState | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::GetSQLState
- Error::SQLState
- Error::get_SQLState
helpviewer_keywords:
- SQLState property
ms.assetid: f9e25967-54b0-444d-af2a-0d2c75365d3e
author: rothja
ms.author: jroth
ms.openlocfilehash: 65d72fed54723f525f4e1426ed04886e9d474985
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777373"
---
# <a name="sqlstate-property"></a>Свойство SQLState
Указывает состояние SQL для данного объекта [ошибки](./error-object.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **строковое** значение из пяти символов, следующее за стандартом ANSI SQL, и указывает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **SQLSTATE** для чтения кода ошибки из пяти символов, возвращаемого поставщиком при возникновении ошибки во время обработки инструкции SQL. Например, при использовании поставщика Microsoft OLE DB для ODBC с базой данных Microsoft SQL Server коды ошибок состояния SQL исходят из ODBC, основываясь на ошибках ODBC или об ошибках, происходящих в Microsoft SQL Server, а затем сопоставленных ошибкам ODBC. Эти коды ошибок описаны в стандарте ANSI SQL, но могут быть реализованы по-разному в разных источниках данных.  
  
## <a name="applies-to"></a>Применение  
 [Объект Error](./error-object.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры свойств Description, HelpContext, HelpFile, NativeError, Number, Source и SQLState (Visual Basic)](./description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Примеры свойств Description, HelpContext, HelpFile, NativeError, Number, Source и SQLState (Visual c++)](./description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)