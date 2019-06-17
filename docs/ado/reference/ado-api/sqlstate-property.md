---
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9e4804b5cbdec4008e1c967b81620ea96eead924
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711312"
---
# <a name="sqlstate-property"></a>Свойство SQLState
Указывает состояние SQL для заданного [ошибка](../../../ado/reference/ado-api/error-object.md) объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает из пяти символов **строка** значение, которое соответствует стандарту ANSI SQL и указывающее код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Используйте **SQLState** свойство для чтения код ошибки пяти символов, который поставщик возвращает при возникновении ошибки во время обработки инструкции SQL. Например при использовании поставщика Microsoft OLE DB для ODBC с базой данных Microsoft SQL Server, кодах ошибок состояния SQL создаются из ODBC, либо ошибках, относящихся к ODBC либо об ошибках, возникших в Microsoft SQL Server и затем сопоставляются с ODBC ошибки. Эти коды ошибок описаны в стандарте SQL ANSI, но может быть по-разному реализован различных источников данных.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>См. также  
 [Description, HelpContext, HelpFile, NativeError, номер, источника и SQLState свойства пример (Visual Basic)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Описание, HelpContext, HelpFile, NativeError, номер, источника и пример свойства SQLState (Visual C++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
