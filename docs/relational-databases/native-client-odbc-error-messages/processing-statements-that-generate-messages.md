---
title: "Обработка инструкций, выдающих сообщения | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-error-messages
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- PRINT statement
- messages [ODBC], statements generating messages
- statements [ODBC], message generation
- errors [ODBC], statements generating messages
- SQL Server Native Client ODBC driver, errors
- STATISTICS IO option
- STATISTICS TIME option
- DBCC statements
- SQLExecute function
- RAISERROR statement
- SQLGetDiagRec function
- ODBC error handling, statements generating messages
- SQLExecDirect function
ms.assetid: 672ebdc5-7fa1-4ceb-8d52-fd25ef646654
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 80c8f0e6fff0ccabc4d46b91f41a38896ad21167
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="processing-statements-that-generate-messages"></a>Обработка инструкций, выдающих сообщения
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Параметры STATISTICS TIME и STATISTICS IO инструкции SET языка [!INCLUDE[tsql](../../includes/tsql-md.md)] используются для получения сведений, помогающих при диагностике долго выполняющихся запросов. Предыдущие версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] также поддерживают параметр SHOWPLAN для анализа планов запросов. Приложение ODBC может установить эти параметры с помощью следующих инструкций:  
  
```  
SQLExecDirect(hstmt, "SET SHOWPLAN ON", SQL_NTS);  
SQLExecDirect(hstmt, "SET STATISTICS TIME ON", SQL_NTS90  
);  
SQLExecDirect(hstmt, "SET STATISTICS IO ON", SQL_NTS);  
```  
  
 При выполнении или SET SHOWPLAN SET STATISTICS TIME ON, **SQLExecute** и **SQLExecDirect** возвращено значение SQL_SUCCESS_WITH_INFO, и в этот момент приложение может получить выходные данные SHOWPLAN или STATISTICS времени путем вызова **SQLGetDiagRec** пока не будет возвращено значение SQL_NO_DATA. Каждая строка данных SHOWPLAN возвращается в следующем формате.  
  
```  
szSqlState="01000", *pfNativeError=6223,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]   
              Table Scan"  
```  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 7.0 параметр SHOWPLAN заменен на SHOWPLAN_ALL и SHOWPLAN_TEXT, которые возвращают выходные данные в виде результирующего набора, а не набора сообщений.  
  
 Каждая строка STATISTICS TIME возвращается в следующем формате.  
  
```  
szSqlState="01000", *pfNativeError= 3613,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
   SQL Server Parse and Compile Time: cpu time = 0 ms."  
```  
  
 Выходные данные SET STATISTICS IO недоступны до завершения результирующего набора. Чтобы получить выходные данные STATISTICS IO, приложение вызывает **SQLGetDiagRec** во время **SQLFetch** или [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) не вернет значение SQL_NO_DATA. Выходные данные STATISTICS IO возвращаются в следующем формате.  
  
```  
szSqlState="01000", *pfNativeError= 3615,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Table: testshow  scan count 1,  logical reads: 1,  
   physical reads: 0."  
```  
  
## <a name="using-dbcc-statements"></a>Использование инструкций DBCC  
 Инструкции DBCC возвращают данные в виде сообщений, а не результирующих наборов. **SQLExecDirect** или **SQLExecute** возвращает SQL_SUCCESS_WITH_INFO, а приложение получает вывод вызывая **SQLGetDiagRec** пока не будет возвращено значение SQL_NO_DATA.  
  
 Например, следующая инструкция возвращает значение SQL_SUCCESS_WITH_INFO.  
  
```  
SQLExecDirect(hstmt, "DBCC CHECKTABLE(Authors)", SQL_NTS);  
```  
  
 Вызовы **SQLGetDiagRec** возврата:  
  
```  
szSqlState = "01000", *pfNativeError = 2536,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Checking authors"  
szSqlState = "01000", *pfNativeError = 2579,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   The total number of data pages in this table is 1."  
szSqlState = "01000", *pfNativeError = 7929,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Table has 23 data rows."  
szSqlState = "01000", *pfNativeError = 2528  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   DBCC execution completed. If DBCC printed error messages,  
   see your System Administrator."  
```  
  
## <a name="using-print-and-raiserror-statements"></a>Использование инструкций PRINT и RAISERROR  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]Инструкций PRINT и RAISERROR также возвращают данные путем вызова **SQLGetDiagRec**. Инструкции PRINT вызывают выполнение инструкции SQL, возвращают значение SQL_SUCCESS_WITH_INFO, а в последующем вызове **SQLGetDiagRec** возвращает *SQLState* со значением 01000. Инструкция RAISERROR со степенью серьезности 10 или ниже работает так же, как PRINT. Инструкция RAISERROR с уровнем серьезности 11 и более, вызывает выполнение для возврата SQL_ERROR, а в последующем вызове **SQLGetDiagRec** возвращает *SQLState* 42000. Например, следующая инструкция возвращает значение SQL_SUCCESS_WITH_INFO.  
  
```  
SQLExecDirect (hstmt, "PRINT  'Some message' ", SQL_NTS);  
```  
  
 Вызов **SQLGetDiagRec** возвращает:  
  
```  
szSQLState = "01000", *pfNative Error = 0,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Some message"  
```  
  
 Следующая инструкция возвращает значение SQL_SUCCESS_WITH_INFO.  
  
```  
SQLExecDirect (hstmt, "RAISERROR ('Sample error 1.', 10, -1)",  
   SQL_NTS)  
```  
  
 Вызов **SQLGetDiagRec** возвращает:  
  
```  
szSQLState = "01000", *pfNative Error = 50000,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Sample error 1."  
```  
  
 Следующая инструкция возвращает значение SQL_ERROR.  
  
```  
SQLExecDirect (hstmt, "RAISERROR ('Sample error 2.', 11, -1)", SQL_NTS)  
```  
  
 Вызов **SQLGetDiagRec** возвращает:  
  
```  
szSQLState = "42000", *pfNative Error = 50000,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Sample error 2."  
```  
  
 Время вызова функции **SQLGetDiagRec** является критическим, если выходные данные инструкций PRINT или RAISERROR включены в результирующий набор. Вызов **SQLGetDiagRec** для получения инструкций PRINT или RAISERROR выходные данные должны выполняться сразу после инструкции, которая получает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO. Это просто в случае выполнения отдельной инструкции SQL, как показано в примере выше. В этих случаях вызов **SQLExecDirect** или **SQLExecute** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO и **SQLGetDiagRec** затем может быть вызван. При программировании циклов для обработки выходных данных пакета инструкций SQL или выполнении хранимых процедур [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возникают осложнения.  
  
 В этом случае [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает результирующий набор для каждой инструкции SELECT, выполненной в пакете или хранимой процедуре. Если пакет или процедура содержит инструкции PRINT или RAISERROR, то их выходные данные чередуются с результирующими наборами инструкций. Если первой инструкцией в пакете или процедуре PRINT или RAISERROR, **SQLExecute** или **SQLExecDirect** возвращает SQL_SUCCESS_WITH_INFO или SQL_ERROR, а также приложения должен вызывать **SQLGetDiagRec** пока не будет возвращено SQL_NO_DATA для получения сведений о PRINT или RAISERROR.  
  
 Если инструкции PRINT или RAISERROR следует после инструкции SQL (например, SELECT), то сведения PRINT или RAISERROR возвращается [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md)устанавливается на результирующем наборе, содержащем ошибку. **SQLMoreResults** возвращает SQL_SUCCESS_WITH_INFO или SQL_ERROR в зависимости от важности сообщения. Сообщения, полученного посредством обращения **SQLGetDiagRec** пока не будет возвращено значение SQL_NO_DATA.  
  
## <a name="see-also"></a>См. также:  
 [Обработка ошибок и сообщений](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
