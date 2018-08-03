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
ms.openlocfilehash: f529c88044444f3fb6e428b6c69f5a5cf5917251
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278915"
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>Соответствие требованиям JDBC 4.3 для JDBC Driver
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

    
> [!NOTE]  
>  Версии Microsoft JDBC Driver для SQL Server до 6.4 соответствуют спецификациям Java Database Connectivity (JDBC) API 4.2. Этот раздел не применяется к версиям до 6.4.  
  
 Начиная с версии 6.4 Microsoft JDBC Driver для SQL Server — JAVA 10 совместимы, но это не полностью соответствует спецификации JDBC API 4.3. Драйвер вызывает исключение SQLFeatureNotSupportedException для нереализованными. 
 
 Следующие методы API-интерфейса JDBC 4.3 реализованы в Microsoft JDBC Driver 6.4 для SQL Server.
 
  **Класс SQLServerConnection**  
  
|Новые методы|Описание|Значимые реализации|  
|-----------------|-----------------|-------------------------------|  
|void beginRequest()|Подсказки к драйверу, что запрос, независимый элемент работы, который начинается в данном соединении. Подробнее: [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#beginRequest--).|Сохраняет значения полей подключения, которые могут быть изменены через открытые методы API: `databaseAutoCommitMode`, `transactionIsolationLevel`, `networkTimeout`, `holdability`, `sendTimeAsDatetime`, `statementPoolingCacheSize`, `disableStatementPooling`, `serverPreparedStatementDiscardThreshold`, `enablePrepareOnFirstPreparedStatementCall `, `catalogName`, `sqlWarnings`, `useBulkCopyForBatchInsert `.|
|void endRequest()|Подсказки для драйвера, который был выполнен запрос, а независимый элемент работы. Подробнее: [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#endRequest--).|Закрывает операторы, которые создаются во время операция и выполняет откат всех открытых транзакций. Метод также отменяет изменения в поля подключения, которые перечислены выше.|