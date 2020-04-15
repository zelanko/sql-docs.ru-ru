---
title: Пакеты заявлений Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c6054ea09c297bc0d8521d0bc3e509585012e8ff
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297994"
---
# <a name="batches-of-statements"></a>Пакеты инструкций
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Пакет заявлений [!INCLUDE[tsql](../../../includes/tsql-md.md)] содержит два или более инструкций, разделенных запятой (;), встроенной в одну строку, передаваемую в функцию **S'LExecDirect** или [S'LPrepare.](https://go.microsoft.com/fwlink/?LinkId=59360) Пример:  
  
```  
SQLExecDirect(hstmt,   
    "SELECT * FROM Authors; SELECT * FROM Titles",  
    SQL_NTS);  
```  
  
 Пакеты могут быть более эффективными, чем отправка инструкций по одной, так как они часто уменьшают требуемый сетевой трафик. Используйте [S'LMoreResults,](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md) чтобы получить место на следующем наборе результатов, когда он закончит с текущим набором результатов.  
  
 Пакеты инструкций всегда можно использовать, если атрибуты курсора ODBC установлены по умолчанию (однопроходный курсор только для чтения), а размер набора строк равен 1.  
  
 Если инструкция выполняется в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], с помощью серверных курсоров, то серверный курсор неявно преобразуется в результирующий набор по умолчанию. **SLExecDirect** или **S'LExecute** возвращение SQL_SUCCESS_WITH_INFO, и звонок в **S'LGetDiagRec** возвращается:  
  
```  
szSqlState = "01S02", pfNativeError = 0  
szErrorMsg = "[Microsoft][SQL Server Native Server Native Client]Cursor type changed."  
```  
  
## <a name="see-also"></a>См. также:  
 [Выполнение заявлений &#40;&#41;ODBC](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
