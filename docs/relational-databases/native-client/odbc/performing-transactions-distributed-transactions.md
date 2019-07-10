---
title: Создание распределенных транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 05/13/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, performing distributed transactions
- SQL Server Native Client ODBC driver, transactions
- distributed transactions [ODBC]
- transactions [ODBC]
- ODBC, transactions
ms.assetid: 2c17fba0-7a3c-453c-91b7-f801e7b39ccb
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 179885276bdda206e4414bd22675e97449df9129
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67687615"
---
# <a name="create-a-distributed-transaction"></a>Создание распределенной транзакции

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

<!--
The following includes .md file is Empty, as of long before 2019/May/13.
/includes/snac-deprecated.md
-->

[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

Распределенная транзакция могут создаваться для разных систем Microsoft SQL по-разному.

## <a name="odbc-driver-calls-the-msdtc-for-sql-server-on-premises"></a>Драйвер ODBC вызывает координатор MSDTC для локального сервера SQL

Координатор распределенных транзакций Microsoft (MSDTC) позволяет приложениям для расширения или _распространять_ транзакцию по нескольким экземплярам [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Распределенная транзакция работает даже в том случае, если два экземпляра размещаются на разных компьютерах.

MSDTC установлена для Microsoft SQL Server в локальной, но недоступен для облачной службы Майкрософт базы данных SQL Azure.

MSDTC вызывается драйвером собственного клиента SQL Server для Open Database Connectivity (ODBC), когда ваш C++ программа управляет распределенной транзакции. Драйвер ODBC для собственного клиента используется диспетчер транзакций, совместимый с открытым группы распределенных транзакций обработки (DTP) стандартный XA. Этот соответствия требуется координатором MS DTC. Как правило все команды управления транзакциями отправляются через этот драйвер ODBC для собственного клиента. Последовательность выглядит следующим образом:

1. Ваш C++ ODBC для собственного клиента приложение запускает транзакцию путем вызова [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md), с выключенным режимом автоматической фиксации.

2. Приложение обновляет некоторые данные в SQL Server X на компьютере A.

3. Приложение обновляет некоторые данные на сервере SQL на компьютере B.
    - При сбое обновления на сервере SQL, откатываются все незафиксированные обновления на обоих экземплярах SQL Server

4. Наконец, приложение завершает транзакцию путем вызова [SQLEndTran _(1)_ ](../../../relational-databases/native-client-odbc-api/sqlendtran.md), с параметром SQL_COMMIT или SQL_ROLLBACK.

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

_(1)_  MSDTC можно вызывать, не ODBC. В этом случае MSDTC становится диспетчером транзакций, а приложение больше не использует **SQLEndTran**.

### <a name="only-one-distributed-transaction"></a>Только одной распределенной транзакции

Предположим, что ваш C++ приложения ODBC для собственного клиента прикрепляется к распределенной транзакции. Затем приложение присоединяет второй распределенной транзакции. В этом случае [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента покидает исходную распределенную транзакцию и прикрепляется к новой распределенной транзакции.

Дополнительные сведения см. в разделе [Справочник программиста DTC](https://docs.microsoft.com/previous-versions/windows/desktop/ms686108\(v=vs.85\)).

## <a name="c-alternative-for-sql-database-in-the-cloud"></a>C#альтернатива для базы данных SQL в облаке

MSDTC не поддерживается для базы данных SQL Azure или хранилище данных SQL Azure.

Тем не менее, распределенной транзакции могут создаваться для базы данных SQL за счет вашей C# программы использовать класс .NET [System.Transactions.TransactionScope](/dotnet/api/system.transactions.transactionscope).

### <a name="other-programming-languages"></a>Другие языки программирования

Следующие другие языки программирования может не предоставляет поддержку распределенных транзакций в службе базы данных SQL:

- Собственный C++ , использующие драйверы ODBC
- Связанный сервер с помощью Transact-SQL
- Драйверы JDBC

## <a name="see-also"></a>См. также

[Выполнение транзакций (ODBC)](performing-transactions-in-odbc.md)
