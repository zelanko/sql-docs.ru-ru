---
title: Соответствие требованиям JDBC 4.3 для JDBC Driver | Документация Майкрософт
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
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "69027946"
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>Соответствие JDBC 4.3 для JDBC Driver

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

> [!NOTE]  
> Версии Microsoft JDBC Driver для SQL Server до 6.4 соответствуют только спецификациям Java Database Connectivity (JDBC) API 4.2. Этот раздел не относится к версиям до 6.4 включительно.

Начиная с версии 6.4, Microsoft JDBC Driver для SQL Server совместим с JAVA 9 и выдает `SQLFeatureNotSupportedException` для новых API-интерфейсов JDBC 4.3 с нереализованными методами.

Microsoft JDBC Driver 7.0 для выпуска SQL Server совместим с JAVA 10 и поддерживает перечисленные ниже API-интерфейсы. Драйвер создает `SQLFeatureNotSupportedException` для других нереализованных методов из спецификаций JDBC 4.3.

|Новый API|Описание|Значимые реализации|  
|-----------------|-----------------|-------------------------------|  
|void java.sql.connection.beginRequest()|Указывает драйверу о том, что в этом подключении начинается запрос, независимая единица работы. Подробнее: [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#beginRequest--).|Сохраняет значения полей соединения, изменяемых методами общедоступных API: `databaseAutoCommitMode`, `transactionIsolationLevel`, `networkTimeout`, `holdability`, `sendTimeAsDatetime`, `statementPoolingCacheSize`, `disableStatementPooling`, `serverPreparedStatementDiscardThreshold`, `enablePrepareOnFirstPreparedStatementCall`, `catalogName`, `sqlWarnings`, `useBulkCopyForBatchInsert`.|
|void java.sql.connection.endRequest()|Указывает драйверу о том, что независимая единица работы завершена. Подробнее: [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#endRequest--).|Закрывает инструкции, созданные во время выполнения единицы работы, и выполняет откат всех открытых транзакций. Метод также отменяет изменения в указанных выше полях подключения.|
