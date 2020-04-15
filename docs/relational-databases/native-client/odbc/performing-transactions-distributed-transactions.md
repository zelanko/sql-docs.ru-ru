---
title: Создание распределенных транзакций Документы Майкрософт
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f21ea9b7146b2907a09688f5189d6d9ae4f3f26a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303713"
---
# <a name="create-a-distributed-transaction"></a>Создание распределенной транзакции

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

<!--
The following includes .md file is Empty, as of long before 2019/May/13.
/includes/snac-deprecated.md
-->


Распределенная транзакция может быть создана для различных систем Microsoft S'L по-разному.

## <a name="odbc-driver-calls-the-msdtc-for-sql-server-on-premises"></a>Драйвер ODBC вызывает MSDTC для сервера S'L

Координатор распределенных транзакций Майкрософт (MSDTC) позволяет приложениям расширять или [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] _распространять_ транзакцию в двух или более экземплярах. Распределенная транзакция работает даже тогда, когда эти два экземпляра размещаются на отдельных компьютерах.

MSDTC устанавливается для сервера Microsoft S'L Server, но недоступен для облачного сервиса базы данных Azure S'L от Microsoft.

MSDTC вызывается драйвером родного клиента сервера S'L Server для Open Database Connectivity (ODBC), когда ваша программа СЗ управляет распределенной транзакцией. Драйвер Native Client ODBC имеет менеджера транзакций, который соответствует стандарту XA Open Group Distributed Transaction Processing (DTP). Это соответствие требуется MSDTC. Как правило, все команды управления транзакциями отправляются через драйвер Native Client ODBC. Последовательность выглядит так:

1. Ваше приложение «Родной клиент» odBC начинает транзакцию, вызывая [s'LSetConnectAttr,](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)с выключенным режимом автоматического обслуживания.

2. Приложение обновляет некоторые данные на сервере X s'L на компьютере А.

3. Приложение обновляет некоторые данные на сервере Y s'L на компьютере B.
    - В случае сбоя обновления на сервере Y, все незафиксированные обновления в обоих экземплярах сервера s'L отогоняются.

4. Наконец, приложение завершает транзакцию, позвонив по [телефону S'LEndTran _(1)_](../../../relational-databases/native-client-odbc-api/sqlendtran.md)с опцией SQL_COMMIT или SQL_ROLLBACK.

_(1)_ MSDTC может вызываться без ODBC. В таком случае MSDTC становится менеджером транзакций, и приложение больше не использует **S'LEndTran.**

### <a name="only-one-distributed-transaction"></a>Только одна распределенная транзакция

Предположим, что ваше приложение «Родной клиент» ODBC зачислено в распределенную транзакцию. Далее приложение зачисляется во второй распределенной транзакции. В этом случае [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер Native Client ODBC покидает исходную распределенную транзакцию и зачисляется в новую распределенную транзакцию.

Для получения дополнительной информации, см [DTC программистА Справка](https://docs.microsoft.com/previous-versions/windows/desktop/ms686108\(v=vs.85\)).

## <a name="c-alternative-for-sql-database-in-the-cloud"></a>Альтернатива для базы данных S'L в облаке

MSDTC не поддерживается ни для базы данных Azure S'L, ни для хранилища данных Azure S'L.

Тем не менее, распределенная транзакция может быть создана для базы данных S'L, если ваша программа C'S используется в программе класса .NET [System.Transactions.TransactionScope.](/dotnet/api/system.transactions.transactionscope)

### <a name="other-programming-languages"></a>Другие языки программирования

Следующие другие языки программирования могут не предоставлять никакой поддержки распределенным транзакциям с помощью службы базы данных S'L:

- Коренные са, которые используют драйверы ODBC
- Связанный сервер с использованием Сделки-СЗЛ
- Драйверы JDBC

## <a name="see-also"></a>См. также

[Выполнение транзакций (ODBC)](performing-transactions-in-odbc.md)
