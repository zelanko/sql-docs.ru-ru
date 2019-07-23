---
title: Использование точек сохранения | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3b48eb13-32ef-4fb3-8e95-dbc9468c9a44
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9212e2de7a093b92c51489bb17623a2120e5ce35
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916220"
---
# <a name="using-savepoints"></a>Использование точек сохранения

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Точки сохранения предоставляют механизм отката части транзакций. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно создать точку сохранения с помощью инструкции SAVE TRANSACTION savepoint_name. После выполняется инструкция ROLLBACK TRANSACTION savepoint_name для отката до точки сохранения вместо отката до начала транзакции.

Точки сохранения удобно использовать, когда вероятность возникновения ошибок мала. Откат до точки сохранения в ситуации, когда ошибка встречается крайне редко, часто более эффективен, чем подход, когда каждая транзакция проверяет допустимость обновления, прежде чем его выполнить. Операции обновления и отката являются ресурсоемкими, поэтому точки сохранения приносят пользу, только если вероятность ошибок небольшая, а затраты на проверку допустимости обновления относительно высокие.

Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] поддерживает использование точек сохранения посредством вызова метода [setSavepoint](../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md) класса [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). С помощью метода setSavepoint можно создать именованную или неименованную точку сохранения в текущей транзакции, а метод возвращает объект [SQLServerSavepoint](../../connect/jdbc/reference/sqlserversavepoint-class.md). В транзакции можно создать несколько точек сохранения. Для отката транзакции до заданной точки сохранения можно передать объект SQLServerSavepoint в метод [rollback (java.sql.Savepoint)](../../connect/jdbc/reference/rollback-method-java-sql-savepoint.md).

В приведенном ниже примере используется точка сохранения при выполнении локальной транзакции, состоящей из двух раздельных инструкций в блоке `try`. Инструкции выполняются для таблицы Production.ScrapReason в образце базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)], а точка сохранения используется для отката второй инструкции. При этом в базе данных фиксируется только первая инструкция.

[!code[JDBC#UsingSavepoints1](../../connect/jdbc/codesnippet/Java/using-savepoints_1.java)]

## <a name="see-also"></a>См. также:

[Выполнение транзакций с помощью драйвера JDBC](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)
