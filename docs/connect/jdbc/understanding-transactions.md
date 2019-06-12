---
title: Основные сведения о транзакциях | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d3e0414c-6809-4bb1-93b1-4960507faecc
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ad6ccc7f65d6d4c65fb1bb63b58e0b13269ea351
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66788384"
---
# <a name="understanding-transactions"></a>Основные сведения о транзакциях

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Транзакции — это группы операций, объединенные в логические рабочие модули. Их используют для управления согласованностью и целостностью каждого действия в транзакции и технической поддержки во избежание возможных ошибок в системе.

При использовании драйвера [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] транзакции могут быть как локальными, так и распределенными. В транзакциях применяются также уровни изоляции. Дополнительные сведения об уровнях изоляции, поддерживаемых драйвером JDBC, см. в разделе [основные сведения об уровнях изоляции](../../connect/jdbc/understanding-isolation-levels.md).

Транзакции должны управляться приложениями посредством или инструкций Transact-SQL, или методов, предоставляемых драйвером JDBC, но не тем и другим одновременно. Одновременное использование инструкций Transact-SQL и методов JDBC API для одной и той же транзакции может привести к неполадкам, например к невозможности зафиксировать транзакцию в ожидаемое время: фиксация или откат транзакции и начало новой произойдет в неожиданный момент, возникнут исключения "Не удалось возобновить транзакцию".

## <a name="using-local-transactions"></a>Использование локальных транзакций

Транзакция считается локальной, если она является однофазной и управляется базой данных напрямую. Драйвер JDBC поддерживает локальные транзакции с помощью различных методов класса [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md), включая [setAutoCommit](../../connect/jdbc/reference/setautocommit-method-sqlserverconnection.md), [commit](../../connect/jdbc/reference/commit-method-sqlserverconnection.md) и [rollback](../../connect/jdbc/reference/rollback-method.md). Локальные транзакции обычно явно управляются приложением или автоматически управляются сервером приложений Java Enterprise Edition (Java EE).

В приведенном ниже примере выполняется локальная транзакция, состоящая из двух отдельных инструкций в блоке `try`. Инструкции выполняются для таблицы Production.ScrapReason в примере базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] и фиксируются при отсутствии исключений. Код в блоке `catch` откатит транзакцию, если возникнет исключение.

[!code[JDBC#UnderstandingTransactions1](../../connect/jdbc/codesnippet/Java/understanding-transactions_1.java)]

## <a name="using-distributed-transactions"></a>Использование распределенных транзакций

Распределенная транзакция обновляет данные в двух или более сетевых базах данных, при этом сохраняются свойства атомарности, согласованности, изолированности и устойчивости (ACID) обработки транзакций. Поддержка распределенных транзакций была добавлена в JDBC API в дополнительной спецификации API JDBC 2.0. Распределенные транзакции обычно автоматически управляются диспетчером транзакций Java Transaction Service (JTS) в среде сервера приложений Java EE. Тем не менее драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] поддерживает распределенные транзакции с любым диспетчером транзакций, совместимым с интерфейсом Java Transaction API (JTA).

Драйвер JDBC интегрируется с координатором распределенных транзакций [!INCLUDE[msCoName](../../includes/msconame_md.md)] (MS DTC), обеспечивая полноценную поддержку распределенных транзакций с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. MS DTC — это средство управления распределенными транзакциями, предоставляемое [!INCLUDE[msCoName](../../includes/msconame_md.md)] для [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows. Используя проверенную технологию обработки транзакций [!INCLUDE[msCoName](../../includes/msconame_md.md)], MS DTC поддерживает функции XA, например полный двухфазный распределенный протокол фиксации и восстановление распределенных транзакций.

Дополнительные сведения об использовании распределенных транзакций см. в разделе [основные сведения о транзакциях XA](../../connect/jdbc/understanding-xa-transactions.md).

## <a name="see-also"></a>См. также:

[Выполнение транзакций с помощью драйвера JDBC](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)
