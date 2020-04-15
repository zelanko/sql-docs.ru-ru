---
title: Обработка ошибок и сообщений Документы Майкрософт
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 59bb40dbfc7f8596968d2dc441396dc9c076bb82
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291746"
---
# <a name="handling-errors-and-messages"></a>Обработка ошибок и сообщений
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Когда приложение вызывает функцию ODBC, драйвер выполняет функцию и возвращает диагностическую информацию двумя способами: код возврата указывает общий успех или сбой функции ODBC, а диагностические записи предоставляют подробную информацию о функции. Диагностическая запись состоит из записи заголовка и записи состояния. При успешном выполнении функции возвращается как минимум одна диагностическая запись, запись заголовка.  
  
 Диагностические сведения используются во время разработки для перехвата программных ошибок, например недопустимых дескрипторов и синтаксических ошибок в жестко запрограммированных инструкциях SQL. Она также используется во время выполнения для захвата ошибок и предупреждений времени выполнения, например усечения данных, нарушения правил и синтаксических ошибок в инструкциях SQL, введенных пользователем. Программная логика обычно основана на кодах возврата.  
  
 Например, после того, как приложение вызывает **S'LFetch** для извлечения строк в наборе результатов, код возврата указывает, был ли достигнут конец набора результатов (SQL_NO_DATA), если какие-либо информационные сообщения были возвращены (SQL_SUCCESS_WITH_INFO) или если произошла ошибка (SQL_ERROR).  
  
 Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] водитель Native Client ODBC возвращает что-либо, кроме SQL_SUCCESS, приложение может позвонить в **S'LGetDiagRec** для получения любых информационных сообщений или сообщений об ошибках. Для прокрутки набора сообщений, если есть более одного сообщения, используйте **S'LGetDiagRec.**  
  
 Код возврата SQL_INVALID_HANDLE всегда указывает на программную ошибку, поэтому не должен встречаться во время выполнения. Все другие коды возврата предоставляют сведения времени выполнения, хотя SQL_ERROR может означать программную ошибку.  
  
 Оригинальный [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] родной API, DB-Library для C, позволяет приложению устанавливать функции обработки ошибок обратного вызова и обработки сообщений, которые возвращают ошибки или сообщения. Некоторые инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], например PRINT, RAISERROR, DBCC и SET, возвращают свои результаты функции обработки сообщений DB-Library, а не результирующему набору. Однако API-интерфейс ODBC не имеет такой возможности обратного вызова. Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] водитель Native Client ODBC обнаруживает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]сообщения, возвращающиеся из, он устанавливает код возврата ODBC для SQL_SUCCESS_WITH_INFO или SQL_ERROR и возвращает сообщение в качестве одной или нескольких диагностических записей. Поэтому приложение ODBC должно тщательно проверить эти коды возврата и вызвать **S'LGetDiagRec** для получения данных сообщений.  
  
 Сведения об ошибках трассировки см. в статье [Отслеживание доступа к данным](https://go.microsoft.com/fwlink/?LinkId=125805). См. сведения об улучшениях трассировки ошибок, добавленных в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], в руководстве по [получению доступа к диагностическим сведениям в расширенном журнале событий](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Обработка инструкций, выдающих сообщения](../../relational-databases/native-client-odbc-error-messages/processing-statements-that-generate-messages.md)  
  
-   [Диагностические записи и поля](../../relational-databases/native-client-odbc-error-messages/diagnostic-records-and-fields.md)  
  
-   [Собственные коды ошибок](../../relational-databases/native-client-odbc-error-messages/native-error-numbers.md)  
  
-   [Коды по ошибке &#40;ODBC&#41;](../../relational-databases/native-client-odbc-error-messages/sqlstate-odbc-error-codes.md)  
  
-   [сообщения об ошибках](../../relational-databases/native-client-odbc-error-messages/error-messages.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client (ODBC)](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
