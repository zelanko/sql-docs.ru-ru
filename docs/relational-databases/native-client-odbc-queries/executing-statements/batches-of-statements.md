---
title: Пакеты инструкций | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-queries
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- statements [ODBC], batches
- batches [ODBC]
- ODBC applications, statements
- multiple statements, batches
- SQLMoreResults function
- SQLExecDirect function
ms.assetid: 057d7c1c-1428-4780-9447-a002ea741188
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 0780b0d0eb57e051d478503e349d13c22acc2e82
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="batches-of-statements"></a>Пакеты инструкций
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Пакет [!INCLUDE[tsql](../../../includes/tsql-md.md)] инструкций содержит два или более инструкций, разделенных точкой с запятой (;), встроенные в одной строки, переданной в **SQLExecDirect** или [SQLPrepare, функция](http://go.microsoft.com/fwlink/?LinkId=59360). Например:  
  
```  
SQLExecDirect(hstmt,   
    "SELECT * FROM Authors; SELECT * FROM Titles",  
    SQL_NTS);  
```  
  
 Пакеты могут быть более эффективными, чем отправка инструкций по одной, так как они часто уменьшают требуемый сетевой трафик. Используйте [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md) для перехода к следующему результирующему набору после завершения текущего результирующего набора.  
  
 Пакеты инструкций всегда можно использовать, если атрибуты курсора ODBC установлены по умолчанию (однопроходный курсор только для чтения), а размер набора строк равен 1.  
  
 Если инструкция выполняется в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], с помощью серверных курсоров, то серверный курсор неявно преобразуется в результирующий набор по умолчанию. **SQLExecDirect** или **SQLExecute** возвращают значение SQL_SUCCESS_WITH_INFO, а вызов **SQLGetDiagRec** возвращает:  
  
```  
szSqlState = "01S02", pfNativeError = 0  
szErrorMsg = "[Microsoft][SQL Server Native Server Native Client]Cursor type changed."  
```  
  
## <a name="see-also"></a>См. также  
 [Выполнение инструкции & #40; ODBC & #41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
