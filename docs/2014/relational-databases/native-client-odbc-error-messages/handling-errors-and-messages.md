---
title: Обработка ошибок и сообщений | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 31216e5a6670ff29c0d7e7ab4f1ee31cc5af0564
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705379"
---
# <a name="handling-errors-and-messages"></a>Обработка ошибок и сообщений
  Когда приложение вызывает функцию ODBC, драйвер выполняет функцию и возвращает диагностическую информацию двумя способами: код возврата указывает на общий успех или сбой функции ODBC, а диагностические записи предоставляют подробные сведения о функции. Диагностическая запись состоит из записи заголовка и записи состояния. При успешном выполнении функции возвращается как минимум одна диагностическая запись, запись заголовка.  
  
 Диагностические сведения используются во время разработки для перехвата программных ошибок, например недопустимых дескрипторов и синтаксических ошибок в жестко запрограммированных инструкциях SQL. Она также используется во время выполнения для захвата ошибок и предупреждений времени выполнения, например усечения данных, нарушения правил и синтаксических ошибок в инструкциях SQL, введенных пользователем. Программная логика обычно основана на кодах возврата.  
  
 Например, после того, как приложение вызывает **SQLFetch** для получения строк в результирующем наборе, код возврата указывает, был ли достигнут конец результирующего набора (SQL_NO_DATA), если были возвращены какие-либо информационные сообщения (SQL_SUCCESS_WITH_INFO) или произошла ошибка (SQL_ERROR).  
  
 Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента возвращает что-либо, кроме SQL_SUCCESS, приложение может вызвать **SQLGetDiagRec** для получения любых информационных или сообщений об ошибках. Используйте **SQLGetDiagRec** для прокрутки набора сообщений вверх и вниз, если имеется более одного сообщения.  
  
 Код возврата SQL_INVALID_HANDLE всегда указывает на программную ошибку, поэтому не должен встречаться во время выполнения. Все другие коды возврата предоставляют сведения времени выполнения, хотя SQL_ERROR может означать программную ошибку.  
  
 Исходный [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный API DB-Library для C позволяет приложению устанавливать функции обработки ошибок и обработки сообщений обратного вызова, возвращающие ошибки или сообщения. Некоторые инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], например PRINT, RAISERROR, DBCC и SET, возвращают свои результаты функции обработки сообщений DB-Library, а не результирующему набору. Однако API-интерфейс ODBC не имеет такой возможности обратного вызова. Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента обнаруживает сообщения, возвращенные из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , он устанавливает код возврата ODBC в SQL_SUCCESS_WITH_INFO или SQL_ERROR и возвращает сообщение в виде одной или нескольких диагностических записей. Поэтому приложение ODBC должно тщательно протестировать эти коды возврата и вызвать **SQLGetDiagRec** для получения данных сообщения.  
  
 Сведения об ошибках трассировки см. в статье [Отслеживание доступа к данным](https://go.microsoft.com/fwlink/?LinkId=125805). См. сведения об улучшениях трассировки ошибок, добавленных в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], в руководстве по [получению доступа к диагностическим сведениям в расширенном журнале событий](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Обработка инструкций, выдающих сообщения](processing-statements-that-generate-messages.md)  
  
-   [Диагностические записи и поля](diagnostic-records-and-fields.md)  
  
-   [Собственные коды ошибок](native-error-numbers.md)  
  
-   [SQLSTATE &#40;коды ошибок ODBC&#41;](sqlstate-odbc-error-codes.md)  
  
-   [сообщения об ошибках](error-messages.md)  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client (ODBC)](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
