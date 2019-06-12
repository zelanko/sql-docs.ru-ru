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
manager: jroth
ms.openlocfilehash: 02aef28bb40c4d4f48b28630d1752c9e5f88c3e5
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66781547"
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
