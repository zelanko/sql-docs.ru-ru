---
description: Свойство SQLState
title: Свойство SQLState | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: bbc849f19c91f7b2387df5e0e71b3455efa0db09
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988865"
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