---
title: JDBC 4.3 соответствия для драйвера JDBC | Документация Майкрософт
ms.custom: ''
ms.date: 07/24/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 36025ec0-3c72-4e68-8083-58b38e42d03b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fc2fbb2b217880b255d522149dabd38701a8c0e4
ms.sourcegitcommit: 8bc5d85bd157f9cfd52245d23062d150b76066ef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 03/07/2019
ms.locfileid: "57579064"
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>Соответствие требованиям JDBC 4.3 для JDBC Driver

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

> [!NOTE]  
> Версии Microsoft JDBC Driver для SQL Server до 6.4 соответствуют только спецификациям Java Database Connectivity (JDBC) API 4.2. Этот раздел не относится к версиям до 6.4 включительно.

Начиная с версии 6.4, Microsoft JDBC Driver для SQL Server совместим JAVA 9 и создает `SQLFeatureNotSupportedException` по новый API JDBC 4.3, которые нереализованными методы.

С 7.0 драйвера Microsoft JDBC для версии SQL Server драйвер теперь JAVA 10 совместимых, а ниже поддерживает упомянутые API-интерфейсы. Драйвер вызывает `SQLFeatureNotSupportedException` для других нереализованными спецификациям JDBC 4.3.

|Новый интерфейс API|Описание|Значимые реализации|  
|-----------------|-----------------|-------------------------------|  
|void java.sql.connection.beginRequest()|Подсказки к драйверу, что запрос, независимый элемент работы, который начинается в данном соединении. Подробнее: [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#beginRequest--).|Сохраняет значения полей подключения, которые могут быть изменены через открытые методы API: `databaseAutoCommitMode`, `transactionIsolationLevel`, `networkTimeout`, `holdability`, `sendTimeAsDatetime`, `statementPoolingCacheSize`, `disableStatementPooling`, `serverPreparedStatementDiscardThreshold`, `enablePrepareOnFirstPreparedStatementCall`, `catalogName`, `sqlWarnings`, `useBulkCopyForBatchInsert`.|
|void java.sql.connection.endRequest()|Подсказки для драйвера, который был выполнен запрос, а независимый элемент работы. Подробнее: [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#endRequest--).|Закрывает операторы, которые создаются во время операция и выполняет откат всех открытых транзакций. Метод также отменяет изменения в поля подключения, которые перечислены выше.|
