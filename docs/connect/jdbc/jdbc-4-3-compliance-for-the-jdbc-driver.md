---
title: JDBC 4.3 соответствия для драйвера JDBC | Документация Майкрософт
ms.custom: ''
ms.date: 07/24/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 36025ec0-3c72-4e68-8083-58b38e42d03b
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 44ec3198bfb6f9898406688df2544dd2e243294b
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2018
ms.locfileid: "39459488"
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>Соответствие требованиям JDBC 4.3 для JDBC Driver

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

> [!NOTE]  
> Версии Microsoft JDBC Driver для SQL Server до 6.4 соответствуют только спецификациям Java Database Connectivity (JDBC) API 4.2. Этот раздел не относится к версиям до 6.4 включительно.

Начиная с версии 6.4, Microsoft JDBC Driver для SQL Server совместим JAVA 9 и создает `SQLFeatureNotSupportedException` по новый API JDBC 4.3, которые нереализованными методы.

С 7.0 драйвера Microsoft JDBC для версии SQL Server драйвер теперь JAVA 10 совместимых, а ниже поддерживает упомянутые API-интерфейсы. Драйвер вызывает `SQLFeatureNotSupportedException` для других нереализованными спецификациям JDBC 4.3.

|Новый интерфейс API|Описание|Значимые реализации|  
|-----------------|-----------------|-------------------------------|  
|void java.sql.connection.beginRequest()|Подсказки к драйверу, что запрос, независимый элемент работы, который начинается в данном соединении. Подробнее: [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#beginRequest--).|Сохраняет значения полей подключения, которые могут быть изменены через открытые методы API: `databaseAutoCommitMode`, `transactionIsolationLevel`, `networkTimeout`, `holdability`, `sendTimeAsDatetime`, `statementPoolingCacheSize`, `disableStatementPooling`, `serverPreparedStatementDiscardThreshold`, `enablePrepareOnFirstPreparedStatementCall `, `catalogName`, `sqlWarnings`, `useBulkCopyForBatchInsert `.|
|void java.sql.connection.endRequest()|Подсказки для драйвера, который был выполнен запрос, а независимый элемент работы. Подробнее: [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#endRequest--).|Закрывает операторы, которые создаются во время операция и выполняет откат всех открытых транзакций. Метод также отменяет изменения в поля подключения, которые перечислены выше.|
