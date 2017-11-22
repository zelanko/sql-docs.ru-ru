---
title: "Управление размером пакета массового копирования | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-bulk-copy-operations
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- ODBC, bulk copy operations
- batches [ODBC]
- bulk copy [ODBC], batch sizes
ms.assetid: 4b24139f-788b-45a6-86dc-ae835435d737
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bf255294a7237b60a16c8d39ebb8d3d4dd82f1e8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="managing-bulk-copy-batch-sizes"></a>Управление размером пакета массового копирования
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Основным назначением пакета в операциях массового копирования является определение области транзакции. Если размер пакета не задан, то функции массового копирования рассматривают все массовое копирование как единую транзакцию. Если указан размер пакета, каждый пакет представляет собой транзакцию, которая фиксируется после завершения работы пакета.  
  
 Если при выполнении массового копирования размер пакета не указан и возникает ошибка, то происходит откат всего массового копирования. Восстановление массового копирования с продолжительным временем выполнения может занять значительное время. Если размер пакета задан, массовое копирование рассматривает каждый пакет как транзакцию и фиксирует каждый пакет. Если происходит ошибка, то необходим откат только одного последнего необработанного пакета.  
  
 Размер пакета может также влиять на затраты ресурсов, связанные с управлением блокировками. При выполнении массового копирования на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], подсказка TABLOCK можно задать с помощью [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) установить блокировку таблицы вместо блокировок строк. Минимальные издержки всей операции массового копирования может дать одна блокировка таблицы. Если подсказка TABLOCK не указана, выполняются блокировки для отдельных строк и издержки обслуживания всех блокировок во время массового копирования могут уменьшить производительность. Поскольку блокировки удерживаются только во время транзакции, указание размера пакета приводит к регулярному формированию фиксации, которая освобождает текущие блокировки.  
  
 Количество строк в пакете может значительно повлиять на производительность при массовом копировании большого числа строк. Рекомендуемый размер пакета зависит от типа выполняемого массового копирования.  
  
-   При массовом копировании в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] укажите подсказку TABLOCK и задайте большой размер пакета.  
  
-   Если подсказка TABLOCK не указана, ограничьте размер пакета числом менее 1000 строк.  
  
 При массовом копировании данных из файла, размер пакета указывается вызовом **bcp_control** с параметром bcpbatch, затем ВЫЗЫВАЕТСЯ перед вызовом метода [bcp_exec](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md). При массовом копировании из переменных программы с помощью [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) и [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md), размером пакета осуществляется путем вызова [bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) после вызова [bcp_ sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) *x* раз, где *x* — количество строк в пакете.  
  
 Помимо указания размера транзакции, пакеты также оказывают влияние при отправке строк по сети серверу. Функции массового копирования обычно кэшируют строки из **bcp_sendrow** до заполнения сетевой пакет, а затем отправить на сервер полный пакет. Если приложение вызывает **bcp_batch**, однако текущий пакет отправляется на сервер, независимо от того, был заполнен. Использование очень маленького размера пакета может снизить производительность, если оно приведет к отправке на сервер большого числа частично заполненных пакетов. Например, вызов **bcp_batch** после каждого **bcp_sendrow** вызывает каждой строки, которые будут отправляться в отдельном пакете и, если строки не очень большие, ведет к потере места в каждом пакете. Размер сетевых пакетов для SQL Server по умолчанию равен 4 КБ, несмотря на то, что приложение может изменять размер, вызвав [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) с атрибутом SQL_ATTR_PACKET_SIZE.  
  
 Другой побочный эффект пакетов заключается в том, что каждый пакет рассматривается как необработанный результирующий набор до ее завершения с **bcp_batch**. Если никакие другие операции попытки подключения выполняются в дескрипторе соединения пакета при необработанных, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента выдает сообщение об ошибке с кодом SQLState = «HY000» и строка сообщения об ошибке из:  
  
```  
"[Microsoft][SQL Server Native Client] Connection is busy with  
results for another hstmt."  
```  
  
## <a name="see-also"></a>См. также:  
 [Выполнение операций массового копирования &#40; ODBC &#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)   
 [Массовый импорт и экспорт данных (SQL Server)](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
