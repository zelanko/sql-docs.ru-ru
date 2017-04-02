---
title: "Другие подписчики, отличные от SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/08/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "подписчики, отличные от SQL Server, другие типы"
ms.assetid: 96b8beb9-38e8-4ce4-97ca-c0f8656b73b4
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# Другие подписчики, отличные от SQL Server
  Список отличных[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживаемых подписчиков [!INCLUDE[msCoName](../../../includes/msconame-md.md)], в разделе [Non-SQL Server Subscribers](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md). В данном разделе содержатся сведения о требованиях к драйверам ODBC и поставщикам OLE DB.  
  
## Требования к драйверам ODBC  
 Драйвер ODBC:  
  
-   Должен быть совместим с уровнем 1 ODBC.  
  
-   Требуется потокобезопасная среда распространителя.  
  
-   Должен поддерживать транзакции.  
  
-   Должен поддерживать язык описания данных (Data Definition Language, DDL).  
  
-   Не может быть доступным только для чтения.  
  
-   Должен поддерживать длинные имена таблиц, таких как **MSreplication_subscriptions**.  
  
## Репликация при помощи интерфейсов OLE DB  
 Поставщики OLE DB должны поддерживать эти объекты для репликации транзакций:  
  
-   объект**DataSource**   
  
-   объект**Session**   
  
-   объект**Command**   
  
-   объект**Rowset**   
  
-   объект**Error**   
  
### Интерфейсы объекта DataSource  
 Необходимы следующие интерфейсы для подключения к источнику данных:  
  
-   **IDBInitialize**  
  
-   **IDBCreateSession**  
  
-   **IDBProperties**  
  
 Если поставщик поддерживает интерфейс **IDBInfo** , [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует интерфейс для получения сведений, таких, как символ-идентификатор в кавычках, максимальная длина инструкции SQL, а также максимальное число символов в именах таблиц и столбцов.  
  
### Интерфейсы объекта Session  
 Требуются следующие интерфейсы:  
  
-   **IDBCreateCommand**  
  
-   **ITransaction**  
  
-   **ITransactionLocal**  
  
-   **IDBSchemaRowset**  
  
### Интерфейсы объекта Command  
 Требуются следующие интерфейсы:  
  
-   **ICommand**  
  
-   **ICommandProperties**  
  
-   **ICommandText**  
  
-   **ICommandPrepare**  
  
-   **IColumnsInfo**  
  
-   **IAccessor**  
  
-   **ICommandWithParameters**  
  
 **IAccessor** необходим для создания методов доступа к параметрам. Если поставщик поддерживает интерфейс **IColumnRowset**, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует его, чтобы определить, является ли столбец столбцом идентификаторов.  
  
### Интерфейсы объекта Rowset  
 Требуются следующие интерфейсы:  
  
-   **IRowset**  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
 Приложение должно открыть набор строк в реплицированной таблице, которая создается в базе данных подписки. Интерфейсы**IColumnsInfo** и **IAccessor** необходимы для доступа к данным в наборе строк.  
  
### Интерфейсы объекта Error  
 Используйте следующие интерфейсы для управления ошибками:  
  
-   **IErrorRecords**  
  
-   **IErrorInfo**  
  
 Используйте интерфейс **ISQLErrorInfo** , если он поддерживается поставщиком OLE DB.  
  
 Дополнительные сведения о поставщике OLE DB см. в документации, поставляемой с используемым поставщиком OLE DB.  
  
## См. также:  
 [Подписчики, отличные от подписчиков SQL Server](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)  
  
  