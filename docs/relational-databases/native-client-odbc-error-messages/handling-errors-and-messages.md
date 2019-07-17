---
title: Обработка ошибок и сообщений | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, about error handling
- errors [ODBC]
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], about messages
- ODBC error handling
- SQL_INVALID_HANDLE return code
- errors [ODBC], about error handling
- messages [ODBC]
ms.assetid: 74ea9630-e482-4a46-bb45-f5234f079b48
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0076dd904f15f4c2d27dba845e86f0b2b881e2cb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041158"
---
# <a name="handling-errors-and-messages"></a>Обработка ошибок и сообщений
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Когда приложение вызывает функцию ODBC, драйвер выполняет функцию и возвращает диагностические сведения двумя способами: Код возврата указывает общий успех или сбой функции ODBC, а диагностические записи предоставляют подробные сведения о функции. Диагностическая запись состоит из записи заголовка и записи состояния. При успешном выполнении функции возвращается как минимум одна диагностическая запись, запись заголовка.  
  
 Диагностические сведения используются во время разработки для перехвата программных ошибок, например недопустимых дескрипторов и синтаксических ошибок в жестко запрограммированных инструкциях SQL. Она также используется во время выполнения для захвата ошибок и предупреждений времени выполнения, например усечения данных, нарушения правил и синтаксических ошибок в инструкциях SQL, введенных пользователем. Программная логика обычно основана на кодах возврата.  
  
 Например, после того, приложение вызывает **SQLFetch** для получения строк в результирующем наборе, код возврата указывает, был ли достигнут конец результирующего набора (SQL_NO_DATA), если информационные сообщения были возвращены (SQL_SUCCESS_ WITH_INFO), или если возникает ошибка (SQL_ERROR).  
  
 Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента возвращает отличное от SQL_SUCCESS, приложение может вызвать **SQLGetDiagRec** для получения сведений или сообщений об ошибках. Используйте **SQLGetDiagRec** для прокрутки вверх и вниз, сообщение, если имеется более одного сообщения.  
  
 Код возврата SQL_INVALID_HANDLE всегда указывает на программную ошибку, поэтому не должен встречаться во время выполнения. Все другие коды возврата предоставляют сведения времени выполнения, хотя SQL_ERROR может означать программную ошибку.  
  
 Исходный [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного API DB-Library для C, позволяет приложению устанавливать обработку ошибок обратного вызова и функции обработки сообщений, возвращающие ошибки или сообщения. Некоторые инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], например PRINT, RAISERROR, DBCC и SET, возвращают свои результаты функции обработки сообщений DB-Library, а не результирующему набору. Однако API-интерфейс ODBC не имеет такой возможности обратного вызова. Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента обнаруживает сообщения, приходящие обратно из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], он присваивает коду возврата значение SQL_SUCCESS_WITH_INFO или SQL_ERROR и возвращает сообщение в виде одной или нескольких диагностических записей. Таким образом, приложение ODBC должно внимательно проверять так, наличие этих кодов возврата и вызов **SQLGetDiagRec** для получения данных сообщения.  
  
 Сведения об ошибках трассировки см. в статье [Отслеживание доступа к данным](https://go.microsoft.com/fwlink/?LinkId=125805). Сведения об улучшениях для отслеживания ошибок, появившихся в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], см. в разделе [доступ к диагностическим сведениям в журнале расширенных событий](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Обработка инструкций, выдающих сообщения](../../relational-databases/native-client-odbc-error-messages/processing-statements-that-generate-messages.md)  
  
-   [Диагностические записи и поля](../../relational-databases/native-client-odbc-error-messages/diagnostic-records-and-fields.md)  
  
-   [Собственные номера ошибок](../../relational-databases/native-client-odbc-error-messages/native-error-numbers.md)  
  
-   [SQLSTATE &#40;коды ошибок ODBC&#41;](../../relational-databases/native-client-odbc-error-messages/sqlstate-odbc-error-codes.md)  
  
-   [Сообщения об ошибках](../../relational-databases/native-client-odbc-error-messages/error-messages.md)  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client (ODBC)](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
