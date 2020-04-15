---
title: Обработка отчетов, генерющих сообщения Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9820e202f5032423292c4306aa63b175bce550b6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304705"
---
# <a name="processing-statements-that-generate-messages"></a>Обработка инструкций, выдающих сообщения
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Параметры STATISTICS TIME и STATISTICS IO инструкции SET языка [!INCLUDE[tsql](../../includes/tsql-md.md)] используются для получения сведений, помогающих при диагностике долго выполняющихся запросов. Предыдущие версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] также поддерживают параметр SHOWPLAN для анализа планов запросов. Приложение ODBC может установить эти параметры с помощью следующих инструкций:  
  
```  
SQLExecDirect(hstmt, "SET SHOWPLAN ON", SQL_NTS);  
SQLExecDirect(hstmt, "SET STATISTICS TIME ON", SQL_NTS90  
);  
SQLExecDirect(hstmt, "SET STATISTICS IO ON", SQL_NTS);  
```  
  
 Когда SET STATISTICS ВРЕМЯ или SET SHOWPLAN являются ON, **S'LExecute** и **S'LExecDirect** возвращения SQL_SUCCESS_WITH_INFO, и, в этот момент, приложение может получить SHOWPLAN или STATISTICS ВРЕМЯ выход, позвонив **s'LGetDiagRec,** пока он не вернется SQL_NO_DATA. Каждая строка данных SHOWPLAN возвращается в следующем формате.  
  
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
  
 Выходные данные SET STATISTICS IO недоступны до завершения результирующего набора. Чтобы получить выход STATISTICS IO, приложение вызывает **s'LGetDiagRec** в момент возвращения **SQL_NO_DATA s'LFetchFetch** или [S'LFetchScroll.](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) Выходные данные STATISTICS IO возвращаются в следующем формате.  
  
```  
szSqlState="01000", *pfNativeError= 3615,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Table: testshow  scan count 1,  logical reads: 1,  
   physical reads: 0."  
```  
  
## <a name="using-dbcc-statements"></a>Использование инструкций DBCC  
 Инструкции DBCC возвращают данные в виде сообщений, а не результирующих наборов. **SLExecDirect** или **S'LExecute** возвращаются SQL_SUCCESS_WITH_INFO, и приложение получает выход, позвонив в **S'LGetDiagRec** до тех пор, пока он не вернется SQL_NO_DATA.  
  
 Например, следующая инструкция возвращает значение SQL_SUCCESS_WITH_INFO.  
  
```  
SQLExecDirect(hstmt, "DBCC CHECKTABLE(Authors)", SQL_NTS);  
```  
  
 Вызовы на **возвращение s'LGetDiagRec:**  
  
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
 [!INCLUDE[tsql](../../includes/tsql-md.md)]Заявления PRINT и RAISERROR также возвращают данные, позвонив по **s'LGetDiagRec**. Заявления PRINT приводят к тому, что выполнение оператора S'L возвращается SQL_SUCCESS_WITH_INFO, а последующий вызов в **S'LGetDiagRec** возвращает *S'LState* 01000. Инструкция RAISERROR со степенью серьезности 10 или ниже работает так же, как PRINT. RAISERROR с тяжестью 11 или выше причин выполнения, чтобы вернуть SQL_ERROR, и последующий вызов на **S'LGetDiagRec** возвращает *S'LState* 42000. Например, следующая инструкция возвращает значение SQL_SUCCESS_WITH_INFO.  
  
```  
SQLExecDirect (hstmt, "PRINT  'Some message' ", SQL_NTS);  
```  
  
 Вызов **S'LGetDiagRec** возвращается:  
  
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
  
 Вызов **S'LGetDiagRec** возвращается:  
  
```  
szSQLState = "01000", *pfNative Error = 50000,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Sample error 1."  
```  
  
 Следующая инструкция возвращает значение SQL_ERROR.  
  
```  
SQLExecDirect (hstmt, "RAISERROR ('Sample error 2.', 11, -1)", SQL_NTS)  
```  
  
 Вызов **S'LGetDiagRec** возвращается:  
  
```  
szSQLState = "42000", *pfNative Error = 50000,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Sample error 2."  
```  
  
 Сроки вызова **S'LGetDiagRec** имеют решающее значение при включении в набор результатов выход из заявлений PRINT или RAISERROR. Звонок в **S'LGetDiagRec** для получения выхода PRINT или RAISERROR должен быть сделан сразу же после получения заявления, которое получает SQL_ERROR или SQL_SUCCESS_WITH_INFO. Это просто в случае выполнения отдельной инструкции SQL, как показано в примере выше. В этих случаях вызов на **sLExecDirect** или **S'LExecute** возвращается SQL_ERROR или SQL_SUCCESS_WITH_INFO, а затем можно вызвать **s'LGetDiagRec.** При программировании циклов для обработки выходных данных пакета инструкций SQL или выполнении хранимых процедур [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возникают осложнения.  
  
 В этом случае [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает результирующий набор для каждой инструкции SELECT, выполненной в пакете или хранимой процедуре. Если пакет или процедура содержит инструкции PRINT или RAISERROR, то их выходные данные чередуются с результирующими наборами инструкций. Если первое заявление в партии или процедуре является PRINT или RAISERROR, **S'LExecute** или **S'LExecDirect** возвращается SQL_SUCCESS_WITH_INFO или SQL_ERROR, и приложение должно позвонить в **S'LGetDiagRec** до тех пор, пока оно не вернется SQL_NO_DATA для получения информации PRINT или RAISERROR.  
  
 Если заявление PRINT или RAISERROR приходит после выписки по S'L (например, выписка SELECT), то информация PRINT или RAISERROR возвращается, когда позиции [S'LMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md)на наборе результатов, содержащий ошибку. **S'LMoreResults** возвращает SQL_SUCCESS_WITH_INFO или SQL_ERROR в зависимости от серьезности сообщения. Сообщения извлекаются, вызывая **S'LGetDiagRec** до тех пор, пока они не SQL_NO_DATA будут.  
  
## <a name="see-also"></a>См. также:  
 [Обработка ошибок и сообщений](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
