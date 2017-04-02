---
title: "удалить моментальный снимок базы данных (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "удаление моментальных снимков базы данных"
  - "удаление моментальных снимков базы данных"
  - "моментальные снимки базы данных [SQL Server], удаление"
ms.assetid: ad70ec97-d5fb-41aa-b72a-915e74b61b76
caps.latest.revision: 36
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 35
---
# удалить моментальный снимок базы данных (Transact-SQL)
  При удалении моментального снимка базы данных он удаляется из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и удаляются разреженные файлы, используемые моментальным снимком. При удалении моментального снимка базы данных все соединения пользователя с ним должны быть завершены.  
  
## Безопасность  
  
###  <a name="Permissions"></a> Разрешения  
 Любой пользователь с разрешениями DROP DATABASE может удалить моментальный снимок базы данных.  
  
##  <a name="TsqlProcedure"></a> Как удалить моментальный снимок базы данных (с помощью Transact-SQL)  
 **Удаление моментального снимка базы данных**  
  
1.  Идентифицируйте моментальный снимок базы данных, который нужно удалить. Просмотреть моментальные снимки в базе данных можно в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Дополнительные сведения см. в разделе [Просмотр моментального снимка базы данных (SQL Server)](../../relational-databases/databases/view-a-database-snapshot-sql-server.md).  
  
2.  Выполните инструкцию [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md) , указав имя моментального снимка базы данных, который нужно удалить. Синтаксис:  
  
     DROP DATABASE *имя_моментального_снимка_базы_данных* [ **,**...*n* ]  
  
     Где *имя_моментального_снимка_базы_данных* — имя удаляемого моментального снимка базы данных.  
  
####  <a name="TsqlExample"></a> Пример (Transact-SQL)  
 Следующий код удаляет моментальный снимок базы данных, имеющий имя SalesSnapshot0600, без влияния на базу данных-источник.  
  
```  
DROP DATABASE SalesSnapshot0600 ;  
```  
  
 Все пользовательские соединения к SalesSnapshot0600 будут завершены, а все разреженные файлы файловой системы NTFS, используемые моментальным снимком, будут удалены.  
  
> [!NOTE]  
>  Сведения об использовании разреженных файлов для моментальных снимков баз данных см. в разделе [Моментальные снимки базы данных (SQL Server)](../../relational-databases/databases/database-snapshots-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Создание моментального снимка базы данных (Transact-SQL)](../../relational-databases/databases/create-a-database-snapshot-transact-sql.md)  
  
-   [Просмотр моментального снимка базы данных (SQL Server)](../../relational-databases/databases/view-a-database-snapshot-sql-server.md)  
  
-   [Восстановление базы данных до состояния, сохраненного в моментальном снимке](../../relational-databases/databases/revert-a-database-to-a-database-snapshot.md)  
  
 ![Значок стрелки, используемый со ссылкой «В начало»](../../analysis-services/instances/media/uparrow16x16.png "Значок стрелки, используемый со ссылкой «В начало»") [&#91;В начало&#93;](#Top)  
  
## См. также:  
 [DROP DATABASE (Transact-SQL)](../../t-sql/statements/drop-database-transact-sql.md)   
 [Моментальные снимки базы данных (SQL Server)](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
  