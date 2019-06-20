---
title: Управление размером пакета массового копирования | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- ODBC, bulk copy operations
- batches [ODBC]
- bulk copy [ODBC], batch sizes
ms.assetid: 4b24139f-788b-45a6-86dc-ae835435d737
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9e6d028939e62665c194f67cdcb490fd17cc4087
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63013918"
---
# <a name="managing-bulk-copy-batch-sizes"></a>Управление размером пакета массового копирования
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Основным назначением пакета в операциях массового копирования является определение области транзакции. Если размер пакета не задан, то функции массового копирования рассматривают все массовое копирование как единую транзакцию. Если указан размер пакета, каждый пакет представляет собой транзакцию, которая фиксируется после завершения работы пакета.  
  
 Если при выполнении массового копирования размер пакета не указан и возникает ошибка, то происходит откат всего массового копирования. Восстановление массового копирования с продолжительным временем выполнения может занять значительное время. Если размер пакета задан, массовое копирование рассматривает каждый пакет как транзакцию и фиксирует каждый пакет. Если происходит ошибка, то необходим откат только одного последнего необработанного пакета.  
  
 Размер пакета может также влиять на затраты ресурсов, связанные с управлением блокировками. При выполнении массового копирования на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], подсказка TABLOCK можно задать с помощью [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) получить блокировку таблицы вместо блокировок строк. Минимальные издержки всей операции массового копирования может дать одна блокировка таблицы. Если подсказка TABLOCK не указана, выполняются блокировки для отдельных строк и издержки обслуживания всех блокировок во время массового копирования могут уменьшить производительность. Поскольку блокировки удерживаются только во время транзакции, указание размера пакета приводит к регулярному формированию фиксации, которая освобождает текущие блокировки.  
  
 Количество строк в пакете может значительно повлиять на производительность при массовом копировании большого числа строк. Рекомендуемый размер пакета зависит от типа выполняемого массового копирования.  
  
-   При массовом копировании в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] укажите подсказку TABLOCK и задайте большой размер пакета.  
  
-   Если подсказка TABLOCK не указана, ограничьте размер пакета числом менее 1000 строк.  
  
 При массовом копировании из файла данных, размер пакета указывается вызовом **bcp_control** с параметром BCPBATCH, перед вызовом [bcp_exec](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md). При массовом копировании из переменных программы с помощью [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) и [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md), размер пакета осуществляется путем вызова функции [bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) после вызова метода [bcp_ sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) *x* раз, где *x* — количество строк в пакете.  
  
 Помимо указания размера транзакции, пакеты также оказывают влияние при отправке строк по сети серверу. Функции массового копирования обычно кэшируют строки из **bcp_sendrow** до сетевого пакета заполняется, а затем отправить полный пакет на сервер. Если приложение вызывает **bcp_batch**, однако текущий пакет отправляется на сервер, независимо от того, будет ли он заполнен. Использование очень маленького размера пакета может снизить производительность, если оно приведет к отправке на сервер большого числа частично заполненных пакетов. Например, вызов **bcp_batch** после каждого **bcp_sendrow** приводит к каждой строки, которые будут отправляться в отдельном пакете и, если строки имеют очень большой размер, занимает лишнее пространство, в каждом пакете. Размер сетевого пакета для SQL Server по умолчанию равен 4 КБ, несмотря на то, что приложение может изменить размер, вызвав [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) с атрибутом SQL_ATTR_PACKET_SIZE.  
  
 Другой побочный эффект пакетов заключается в том, что каждый пакет рассматривается как необработанный результирующий набор до завершения с **bcp_batch**. Если никакие другие операции применяются на дескриптор соединения, хотя пакет представляет собой необработанные, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента выдает ошибку с кодом SQLState = «HY000» и строку сообщения об ошибке из:  
  
```  
"[Microsoft][SQL Server Native Client] Connection is busy with  
results for another hstmt."  
```  
  
## <a name="see-also"></a>См. также  
 [Выполнение операций массового копирования &#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)   
 [Массовый импорт и экспорт данных (SQL Server)](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
