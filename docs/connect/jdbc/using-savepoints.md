---
title: Использование точек сохранения | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3b48eb13-32ef-4fb3-8e95-dbc9468c9a44
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dccc8739a02fa478c153bbbe1702b925942f8efd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="using-savepoints"></a>Использование точек сохранения
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Точки сохранения предоставляют механизм отката части транзакций. В пределах [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], можно создать точку сохранения с помощью инструкции SAVE TRANSACTION savepoint_name. После выполняется инструкция ROLLBACK TRANSACTION savepoint_name для отката до точки сохранения вместо отката до начала транзакции.  
  
 Точки сохранения удобно использовать, когда вероятность возникновения ошибок мала. Откат до точки сохранения в ситуации, когда ошибка встречается крайне редко, часто более эффективен, чем подход, когда каждая транзакция проверяет допустимость обновления, прежде чем его выполнить. Операции обновления и отката являются ресурсоемкими, поэтому точки сохранения приносят пользу, только если вероятность ошибок небольшая, а затраты на проверку допустимости обновления относительно высокие.  
  
 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Поддерживает использование точек сохранения через [setSavepoint](../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md) метод [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) класса. С помощью метода setSavepoint, можно создавать именованную или неименованную точку сохранения в текущей транзакции, а метод вернет [SQLServerSavepoint](../../connect/jdbc/reference/sqlserversavepoint-class.md) объекта. В транзакции можно создать несколько точек сохранения. Для отката транзакции до заданной точки сохранения, можно передать объект SQLServerSavepoint [rollback (java.sql.Savepoint)](../../connect/jdbc/reference/rollback-method-java-sql-savepoint.md) метод.  
  
 В следующем примере используется точка сохранения при выполнении локальной транзакции, состоящей из двух раздельных инструкций в `try` блока. Инструкции выполняются для таблицы Production.ScrapReason в [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных, а точка сохранения используется для отката второй инструкции. При этом в базе данных фиксируется только первая инструкция.  
  
 [!code[JDBC#UsingSavepoints1](../../connect/jdbc/codesnippet/Java/using-savepoints_1.java)]  
  
## <a name="see-also"></a>См. также  
 [Выполнение транзакций с помощью драйвера JDBC](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)  
  
  
