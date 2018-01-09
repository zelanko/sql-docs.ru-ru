---
title: "Диагностические записи и поля | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
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
- header records [ODBC]
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], diagnostic records
- ODBC error handling, diagnostic records
- SQLGetDiagField function
- diagnostic records [ODBC]
- errors [ODBC], diagnostic records
- fields [ODBC]
- status information [ODBC]
ms.assetid: 4949530c-62d1-4f1a-b592-144244444ce0
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2ced62a96f94fa4cb929f295f7a390c60b42e15d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="diagnostic-records-and-fields"></a>Диагностические записи и поля
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Диагностические записи связаны со средой ODBC, соединением, инструкцией или указателями дескриптора. Когда любая функция ODBC возвращает код возврата, отличный от SQL_SUCCESS или SQL_INVALID_HANDLE, дескриптор, вызванный функцией, имеет связанные диагностические записи, содержащие информационные сообщения или сообщения об ошибке. Эти записи сохраняются до тех пор, пока с помощью данного дескриптора не будет вызвана другая функция, в этот момент записи отменяются. Не существует ограничения на количество диагностических записей, одновременно связанных с дескриптором.  
  
 Существует два типа диагностических записей: заголовок и состояние. Заголовочная запись имеет номер 0; если есть записи состояния, то они имеют номера от 1 и далее. Диагностические записи содержат различные поля для заголовочной записи и для записей состояния. Компоненты ODBC могут также определять свои собственные поля диагностических записей.  
  
 Поля в заголовочной записи содержат общие сведения о выполнении функции, включая код возврата, число строк, число записей состояния и тип выполняемой инструкции. Заголовочная запись создается всегда, если только функция ODBC не возвращает SQL_INVALID_HANDLE. Полный список полей в заголовочной записи см. в разделе [SQLGetDiagField](../../relational-databases/native-client-odbc-api/sqlgetdiagfield.md).  
  
 Поля в записях состояния содержат сведения об конкретных ошибках и предупреждениях, возвращаемых диспетчером драйверов ODBC, драйвером или источником данных, включая значение SQLSTATE, номер собственной ошибки, диагностическое сообщение, номер столбца и номер строки. Записи состояния создаются только в том случае, если функция возвращает SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA или SQL_STILL_EXECUTING. Полный список полей в записях состояния см. в разделе **SQLGetDiagField**.  
  
 **SQLGetDiagRec** получает единую диагностическую запись вместе с его ODBC SQLSTATE, номер внутренней ошибки и полями диагностического сообщения. Эта функциональность аналогична ODBC 2. *x***SQLError** функции. Простейшая функция обработки ошибок в ODBC 3. *x* состоит в повторяющемся вызове **SQLGetDiagRec** начиная с *RecNumber* равным 1 и увеличивая *RecNumber* с 1 до **SQLGetDiagRec** не вернет значение SQL_NO_DATA. Это эквивалентно ODBC 2. *x* приложением, вызывающим метод **SQLError** пока она не возвратит SQL_NO_DATA_FOUND.  
  
 ODBC 3. *x* поддерживает намного больше диагностических сведений, чем ODBC 2. *x*. Эти сведения хранятся в дополнительных полях в диагностических записях, получаемых с помощью **SQLGetDiagField**.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC для собственного клиента имеет специфические для драйвера диагностические поля, которые могут быть получены с **SQLGetDiagField**. Метки для этих специфических для драйвера полей определяются в файле sqlncli.h. С помощью этих меток можно получить состояние [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], степень серьезности, имя сервера, имя процедуры и номер строки, связанный с каждой диагностической записью. Кроме того, файл sqlncli.h содержит определения кодов, драйвер использует для идентификации инструкций Transact-SQL, если приложение вызывает **SQLGetDiagField** с *DiagIdentifier* значение SQL_DIAG_DYNAMIC_ FUNCTION_CODE.  
  
 **SQLGetDiagField** обрабатывается диспетчером драйверов ODBC с помощью сведений об ошибке, кэшированных с базового драйвера. Диспетчер драйверов ODBC не кэширует специфические для драйвера диагностические поля до того, как установлено успешное соединение. **SQLGetDiagField** возвращает значение SQL_ERROR, если он вызывается для получения специфические для драйвера диагностические поля до завершения удачного соединения. Если функция соединения ODBC возвращает SQL_SUCCESS_WITH_INFO, то специфические для драйвера диагностические поля еще не доступны для функции соединения. Можно запустить вызов **SQLGetDiagField** для драйвера диагностические поля только после внесения ODBC другой вызов функции после функции соединения.  
  
 Большинство ошибок, о которых сообщили [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента могут быть эффективно обнаружены с помощью сведений, возвращенных представлением **SQLGetDiagRec**. Однако в некоторых случаях сведения, возвращаемые в специфических для драйвера диагностических полях, важны для диагностирования ошибки. При написании обработчика ошибок ODBC для приложений, использующих [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента рекомендуется также использовать **SQLGetDiagField** для извлечения по крайней мере SQL_DIAG_SS_MSGSTATE и SQL_DIAG_SS_SEVERITY специфические для драйвера поля. Если какая-то ошибка может быть вызвана в нескольких местах кода [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то SQL_DIAG_SS_MSGSTATE показывает сотруднику отдела службы технической поддержки корпорации Майкрософт, где именно ошибка была вызвана, и это может иногда помочь при диагностике проблемы.  
  
## <a name="see-also"></a>См. также:  
 [Обработка ошибок и сообщений](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
