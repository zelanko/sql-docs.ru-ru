---
title: "переместить базу данных с поддержкой FILESTREAM | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-blob"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FILESTREAM [SQL Server], перемещение базы данных с поддержкой FILESTREAM"
ms.assetid: dd4d270d-9283-431a-aa6b-e571fced1893
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# переместить базу данных с поддержкой FILESTREAM
  В этом разделе показано перемещение базы данных с поддержкой FILESTREAM.  
  
> [!NOTE]  
>  В примерах этого раздела требуется база данных Archive, созданная в разделе [Создание базы данных с поддержкой FILESTREAM](../../relational-databases/blob/create-a-filestream-enabled-database.md).  
  
### Перемещение базы данных с поддержкой FILESTREAM  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]нажмите кнопку **Создать запрос** , чтобы открыть редактор запросов.  
  
2.  Скопируйте следующий скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] в редактор запросов и нажмите кнопку **Выполнить**. Этот скрипт показывает расположение физических файлов базы данных, который использует база данных FILESTREAM.  
  
    ```tsql  
    USE Archive  
    GO  
    SELECT type_desc, name, physical_name from sys.database_files  
    ```  
  
3.  Скопируйте следующий скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] в редактор запросов и нажмите кнопку **Выполнить**. Этот код переводит базу данных `Archive` в режим вне сети.  
  
    ```tsql  
    USE master  
    EXEC sp_detach_db Archive  
    GO  
    ```  
  
4.  Создайте папку `C:\moved_location`и переместите в нее файлы и папки, перечисленные на шаге 2.  
  
5.  Скопируйте следующий скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] в редактор запросов и нажмите кнопку **Выполнить**. Этот скрипт переводит базу данных `Archive` в режим «в сети».  
  
    ```tsql  
    CREATE DATABASE Archive ON  
    PRIMARY ( NAME = Arch1,  
        FILENAME = 'c:\moved_location\archdat1.mdf'),  
    FILEGROUP FileStreamGroup1 CONTAINS FILESTREAM( NAME = Arch3,  
        FILENAME = 'c:\moved_location\filestream1')  
    LOG ON  ( NAME = Archlog1,  
        FILENAME = 'c:\moved_location\archlog1.ldf')  
    FOR ATTACH  
    GO  
    ```  
  
## См. также:  
 [sp_detach_db (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)  
  
  