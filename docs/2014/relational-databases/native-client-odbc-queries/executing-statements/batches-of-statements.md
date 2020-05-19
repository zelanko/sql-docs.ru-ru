---
title: Пакеты инструкций | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statements [ODBC], batches
- batches [ODBC]
- ODBC applications, statements
- multiple statements, batches
- SQLMoreResults function
- SQLExecDirect function
ms.assetid: 057d7c1c-1428-4780-9447-a002ea741188
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 013a8e8ab09b192a2ff7a04a9d7ddc5be1395636
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82710751"
---
# <a name="batches-of-statements"></a>Пакеты инструкций
  Пакет [!INCLUDE[tsql](../../../includes/tsql-md.md)] инструкций содержит две или более инструкции, разделенные точкой с запятой (;), встроенными в одну строку, переданную в функцию **SQLExecDirect** или [SQLPrepare](https://go.microsoft.com/fwlink/?LinkId=59360). Пример:  
  
```  
SQLExecDirect(hstmt,   
    "SELECT * FROM Authors; SELECT * FROM Titles",  
    SQL_NTS);  
```  
  
 Пакеты могут быть более эффективными, чем отправка инструкций по одной, так как они часто уменьшают требуемый сетевой трафик. Используйте [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) , чтобы перейти к следующему результирующему набору по завершении текущего результирующего набора.  
  
 Пакеты инструкций всегда можно использовать, если атрибуты курсора ODBC установлены по умолчанию (однопроходный курсор только для чтения), а размер набора строк равен 1.  
  
 Если инструкция выполняется в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], с помощью серверных курсоров, то серверный курсор неявно преобразуется в результирующий набор по умолчанию. **SQLExecDirect** или **SQLExecute** возвращают SQL_SUCCESS_WITH_INFO, а вызов **SQLGetDiagRec** возвращает:  
  
```  
szSqlState = "01S02", pfNativeError = 0  
szErrorMsg = "[Microsoft][SQL Server Native Server Native Client]Cursor type changed."  
```  
  
## <a name="see-also"></a>См. также  
 [Исполнение инструкций &#40;ODBC&#41;](executing-statements-odbc.md)  
  
  
