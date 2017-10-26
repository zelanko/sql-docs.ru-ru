---
title: "Использование удержания | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa48306c-e7a0-4dcb-af21-9ebb6898e45a
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 19dfa43e83b3fe94fa75df6a2713497093a08a96
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="using-holdability"></a>Использование удержания
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  По умолчанию результирующий набор, созданный внутри транзакции, сохраняется открытым после фиксации транзакции в базе данных или ее отката. Однако иногда полезно закрыть результирующий набор после фиксации транзакции. Чтобы сделать это, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] поддерживает удержание результирующих наборов.  
  
 Удержание результирующего набора можно задать с помощью [setHoldability](../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md) метод [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) класса. При установке удержания при помощи метода setHoldability, результирующий набор константы удержания ResultSet.HOLD_CURSORS_OVER_COMMIT или ResultSet.CLOSE_CURSORS_AT_COMMIT может использоваться.  
  
 Драйвер JDBC также поддерживает удержание при создании одного из объектов инструкции. При создании объектов инструкции, имеющих перегрузку параметров удержания результирующего набора, удержание объекта инструкции должно соответствовать удержанию подключения. Если они не соответствуют друг другу, возникает исключение. Это происходит потому, что SQL Server поддерживает удержание только на уровне соединения.  
  
 Удержание результирующего набора — это удержание объекта, связанного с результирующим набором, во время создания результирующего набора для серверных курсоров только объект SQLServerConnection. Это не применяется к курсорам на стороне клиента. Все результирующие наборы с курсорами на стороне клиента всегда будет иметь значение удержания ResultSet.HOLD_CURSORS_OVER_COMMIT.  
  
 Для серверных курсоров при соединении с SQL Server 2005 или более поздней версии параметр возможности сохранения влияет только на новые результирующие наборы, которые будут созданы для этого соединения. Это означает, что настройка удержания не имеет влияния на удержание каких-либо результирующих наборов, которые были созданы ранее и открыты в настоящий момент относительно того соединения. Однако для SQL Server 2000 установка возможности сохранения относится и к существующим результирующим наборам, и к новым, которые пока не созданы для данного соединения.  
  
 В следующем примере удержание результирующего набора задается при выполнении локальной транзакции, состоящей из двух раздельных инструкций в `try` блока. Инструкции выполняются для таблицы Production.ScrapReason в [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных. Сначала выполняется переключение на ручной режим транзакции посредством установки для автоматической фиксации **false**. После отключения режима автоматической фиксации инструкции SQL не будут фиксироваться до приложение вызывает [фиксации](../../connect/jdbc/reference/commit-method-sqlserverconnection.md) метод явным образом. Код в блоке catch откатит транзакцию, если возникнет исключение.  
  
 [!code[JDBC#UsingHoldability1](../../connect/jdbc/codesnippet/Java/using-holdability_1.java)]  
  
## <a name="see-also"></a>См. также:  
 [Выполнение транзакций с драйвером JDBC](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)  
  
  

