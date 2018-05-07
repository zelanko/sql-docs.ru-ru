---
title: Транзакции в ODBC | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client|ODBC
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, transactions
- transactions [ODBC]
- ODBC, transactions
ms.assetid: c5a87fa5-827a-4e6f-a0d9-924bac881eb0
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: aeea2e4d425e4d6a5c2a28a803b5ae344b7c8730
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="performing-transactions-in-odbc"></a>Выполнение транзакций в ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Управление транзакциями в ODBC выполняется на уровне соединения. Когда приложение завершает транзакцию, оно фиксирует или откатывает назад все операции со всеми инструкциями, хранящими дескриптор данного соединения. Для фиксации или отката транзакции приложения должны вызывать метод [SQLEndTran](../../../relational-databases/native-client-odbc-api/sqlendtran.md) вместо непосредственного выполнения инструкции COMMIT или ROLLBACK.  
  
 Для переключения между двумя режимами управления транзакциями, которые применяются в ODBC, используется метод [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) .  
  
-   Режим автоматической фиксации  
  
     Каждая отдельная инструкция языка автоматически фиксируется после успешного завершения. При работе в режиме автоматической фиксации других средств управления транзакциями не требуется.  
  
-   Режим ручной фиксации  
  
     Все выполненные инструкции будут включены в одну и ту же транзакцию, если ее не прекратить явным образом, вызвав **SQLEndTran**.  
  
 Режим автоматической фиксации применяется в ODBC по умолчанию. Любое новое соединение находится в режиме автоматической фиксации, пока не будет вызван метод **SQLSetConnectAttr** для перехода в режим ручной фиксации. Когда приложение отключает режим автоматической фиксации, следующая инструкция, введенная в базу данных, начнет транзакцию. Эта транзакция остается в силе, пока приложение не вызовет функцию **SQLEndTran** с параметром SQL_COMMIT либо SQL_ROLLBACK. Команда, посланная в базу данных после вызова функции **SQLEndTran** , начинает новую транзакцию.  
  
 Если приложение переключается с режима ручной фиксации на автоматическую, драйвер фиксирует все транзакции, открытые в этот момент для данного соединения.  
  
 Приложения ODBC не должны использовать инструкции языка Transact-SQL, такие как BEGIN TRANSACTION, COMMIT TRANSACTION и ROLLBACK TRANSACTION, потому что это может привести к ситуации, когда поведение драйвера не определено. Приложение ODBC должно выполняться в режиме автоматической фиксации и не использовать никаких функций или инструкций для управления транзакциями или работать в режиме ручной фиксации и использовать функцию ODBC **SQLEndTran** для фиксации и отката транзакций.  
  
## <a name="see-also"></a>См. также  
 [Выполнение транзакций & #40; ODBC & #41;](http://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
  
