---
title: "Асинхронный режим и команда SQLCancel | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|ODBC
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ebff53e9267b023f2688f2d3d3e930dec7645aec
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="creating-a-driver-application---asynchronous-mode-and-sqlcancel"></a>Создание приложения драйвера - асинхронный режим и команда SQLCancel
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

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
  
 Иногда команда остается необработанной долгое время. Если приложение должно отменить команду без ожидания ответа, его можно сделать, вызвав **SQLCancel** с той же инструкции обработки необработанных командой. Это единственный случай **SQLCancel** следует использовать. Некоторые программисты используют **SQLCancel** если они обработка части результирующего набора и нужно отменить оставшуюся часть результирующего набора. [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md) или [SQLCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md) следует использовать для отмены оставшейся части необработанного результирующего набора, не **SQLCancel**.  
  
## <a name="see-also"></a>См. также  
 [Создание драйвера приложение ODBC собственного клиента SQL Server](../../../relational-databases/native-client/odbc/creating-a-driver-application.md)  
  
  
