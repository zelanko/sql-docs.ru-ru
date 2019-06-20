---
title: Асинхронный режим и команда SQLCancel | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- asynchronous operations [SQL Server Native Client]
- SQLCancel function
- SQLSetConnectAttr function
- SQL Server Native Client, asynchronous operations
- ODBC functions
- ODBC applications, asynchronous operations
- SQL Server Native Client ODBC driver, asynchronous mode
ms.assetid: f31702a2-df76-4589-ac3b-da5412c03dc2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3a4ec4e5d7575fdf5d915c8209999e1285fa79aa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63144325"
---
# <a name="asynchronous-mode-and-sqlcancel"></a>Асинхронный режим и команда SQLCancel
  Некоторые функции ODBC могут работать как синхронно, так и асинхронно. В приложении могут быть разрешены асинхронные операции как для дескриптора инструкции, так и для дескриптора соединения. Если параметр установлен для дескриптора соединения, он затрагивает все дескрипторы инструкции в этом дескрипторе соединения. Приложение использует следующие инструкции, чтобы включить или отключить асинхронный режим:  
  
```  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
```  
  
 Когда приложение вызывает функцию ODBC в синхронном режиме, драйвер не возвращает управление приложению, пока не получит уведомление о том, что сервер завершил выполнение команды.  
  
 В асинхронном режиме драйвер возвращает управление приложению немедленно, даже перед отправкой команды серверу. Драйвер выставляет код возврата в значение SQL_STILL_EXECUTING. Приложение может выполнять другую работу.  
  
 Когда приложение проверяет завершение выполнения команды, делается тот же вызов функции с теми же параметрами для драйвера. Если драйвер еще не получил ответ от сервера, он опять вернет значение SQL_STILL_EXECUTING. Приложение должно проверять команду периодически до тех пор, пока код возврата не станет отличен от SQL_STILL_EXECUTING. Когда приложение получает любой другой код возврата, даже SQL_ERROR, оно может определить, что выполнение команды завершено.  
  
 Иногда команда остается необработанной долгое время. Если приложение должно отменить команду без ожидания ответа, это можно сделать, вызвав **SQLCancel** с той же инструкции обработки как необработанные команды. Это единственный случай, когда **SQLCancel** следует использовать. Некоторые программисты используют **SQLCancel** когда они обработка части результирующего набора и нужно отменить оставшуюся часть результирующего набора. [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) или [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) следует использовать для отмены оставшейся части необработанного результирующего набора, не **SQLCancel**.  
  
## <a name="see-also"></a>См. также  
 [Создание драйвера ODBC для собственного клиента SQL Server](creating-a-driver-application.md)  
  
  
