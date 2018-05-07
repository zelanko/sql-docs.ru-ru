---
title: Основные сведения о транзакциях | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d3e0414c-6809-4bb1-93b1-4960507faecc
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6045c482a931329e3d62c49dedea7ea86a14c545
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="understanding-transactions"></a>Основные сведения о транзакциях
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Транзакции — это группы операций, объединенные в логические рабочие модули. Их используют для управления согласованностью и целостностью каждого действия в транзакции и технической поддержки во избежание возможных ошибок в системе.  
  
 С [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], транзакции может быть локальной или распределенной. В транзакциях применяются также уровни изоляции. Дополнительные сведения об уровнях изоляции, поддерживаемых драйвером JDBC см. в разделе [основные сведения об уровнях изоляции](../../connect/jdbc/understanding-isolation-levels.md).  
  
 Транзакции должны управляться приложениями посредством или инструкций Transact-SQL, или методов, предоставляемых драйвером JDBC, но не тем и другим одновременно. Одновременное использование инструкций Transact-SQL и методов JDBC API для одной и той же транзакции может привести к неполадкам, например к невозможности зафиксировать транзакцию в ожидаемое время: фиксация или откат транзакции и начало новой произойдет в неожиданный момент, возникнут исключения "Не удалось возобновить транзакцию".  
  
## <a name="using-local-transactions"></a>Использование локальных транзакций  
 Транзакция считается локальной, если она является однофазной и управляется базой данных напрямую. Драйвер JDBC поддерживает локальные транзакции с помощью различных методов [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) класса, включая [setAutoCommit](../../connect/jdbc/reference/setautocommit-method-sqlserverconnection.md), [фиксации](../../connect/jdbc/reference/commit-method-sqlserverconnection.md)и [отката](../../connect/jdbc/reference/rollback-method.md). Локальные транзакции обычно явно управляются приложением или автоматически управляются сервером приложений Java Enterprise Edition (Java EE).  
  
 В следующем примере выполняется локальная транзакция, состоящая из двух отдельных инструкций в `try` блока. Инструкции выполняются для таблицы Production.ScrapReason в [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных и они будут зафиксированы, при отсутствии исключений. Код в `catch` блок откат транзакции, если возникает исключение.  
  
 [!code[JDBC#UnderstandingTransactions1](../../connect/jdbc/codesnippet/Java/understanding-transactions_1.java)]  
  
## <a name="using-distributed-transactions"></a>Использование распределенных транзакций  
 Распределенная транзакция обновляет данные в двух или более сетевых базах данных, при этом сохраняются свойства атомарности, согласованности, изолированности и устойчивости (ACID) обработки транзакций. Поддержка распределенных транзакций была добавлена в JDBC API в дополнительной спецификации API JDBC 2.0. Распределенные транзакции обычно автоматически управляются диспетчером транзакций Java Transaction Service (JTS) в среде сервера приложений Java EE. Тем не менее [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] поддерживает распределенные транзакции с любым диспетчером транзакций, совместимым интерфейсом Java Transaction API (JTA).  
  
 Драйвер JDBC безупречно интегрируется с [!INCLUDE[msCoName](../../includes/msconame_md.md)] координатор распределенных транзакций (MS DTC), обеспечивая полноценную поддержку распределенных транзакций с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. MS DTC является средство управления распределенными транзакциями, предоставляемые [!INCLUDE[msCoName](../../includes/msconame_md.md)] для [!INCLUDE[msCoName](../../includes/msconame_md.md)] систем Windows. MS DTC использует проверенной технологии обработки транзакций из [!INCLUDE[msCoName](../../includes/msconame_md.md)] поддерживает функции XA, например полный двухфазный распределенный протокол фиксации и восстановление распределенных транзакций.  
  
 Дополнительные сведения об использовании распределенных транзакций см. в разделе [основные сведения о транзакциях XA](../../connect/jdbc/understanding-xa-transactions.md).  
  
## <a name="see-also"></a>См. также  
 [Выполнение транзакций с помощью драйвера JDBC](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)  
  
  
