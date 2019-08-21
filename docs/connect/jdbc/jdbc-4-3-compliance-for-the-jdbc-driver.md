---
title: Соответствие JDBC 4,3 для драйвера JDBC | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 36025ec0-3c72-4e68-8083-58b38e42d03b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0ed9b10ad9e9a927789505c7d7327c6cf4d1ff3c
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69027946"
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>Соответствие JDBC 4.3 для JDBC Driver

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

> [!NOTE]  
> Версии Microsoft JDBC Driver для SQL Server до 6.4 соответствуют только спецификациям Java Database Connectivity (JDBC) API 4.2. Этот раздел не относится к версиям до 6.4 включительно.

Начиная с версии 6,4, драйвер Microsoft JDBC для SQL Server совместим с Java 9 и создает `SQLFeatureNotSupportedException` новые API-интерфейсы JDBC 4,3 с нереализованными методами.

Драйвер Microsoft JDBC Driver 7,0 для SQL Server выпуска совместим с JAVA 10 и поддерживает перечисленные ниже API-интерфейсы. Драйвер создает исключение `SQLFeatureNotSupportedException` для других нереализованных методов из спецификаций JDBC 4,3.

|Новый API|Описание|Значимые реализации|  
|-----------------|-----------------|-------------------------------|  
|void java.sql.connection.beginRequest()|Указания драйвера о том, что запрос, независимая единица работы, начинается с этого соединения. Подробнее: [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#beginRequest--).|Сохраняет значения изменяемых полей соединения с помощью открытых методов `databaseAutoCommitMode`API: `serverPreparedStatementDiscardThreshold` `disableStatementPooling` `networkTimeout`, `transactionIsolationLevel`,, `statementPoolingCacheSize` `holdability` `sendTimeAsDatetime`,,,,, `enablePrepareOnFirstPreparedStatementCall`, `catalogName`, `sqlWarnings`, `useBulkCopyForBatchInsert`.|
|void java.sql.connection.endRequest()|Указания драйвера о завершении запроса, независимой единицы работы. Подробнее: [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#endRequest--).|Закрывает инструкции, созданные во время работы, и выполняет откат всех открытых транзакций. Метод также возвращает изменения в указанные выше поля подключения.|
