---
title: Перемещение базы данных с поддержкой FILESTREAM | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], moving a FILESTREAM-enabled database
ms.assetid: dd4d270d-9283-431a-aa6b-e571fced1893
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 33d2f34f9f2ea63f23c570c0b4ada95906649215
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68091529"
---
# <a name="move-a-filestream-enabled-database"></a>переместить базу данных с поддержкой FILESTREAM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе показано перемещение базы данных с поддержкой FILESTREAM.  
  
> [!NOTE]  
>  В примерах этого раздела требуется база данных Archive, созданная в разделе [Создание базы данных с поддержкой FILESTREAM](../../relational-databases/blob/create-a-filestream-enabled-database.md).  
  
### <a name="to-move-a-filestream-enabled-database"></a>Перемещение базы данных с поддержкой FILESTREAM  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]нажмите кнопку **Создать запрос** , чтобы открыть редактор запросов.  
  
2.  Скопируйте следующий скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] в редактор запросов и нажмите кнопку **Выполнить**. Этот скрипт показывает расположение физических файлов базы данных, который использует база данных FILESTREAM.  
  
    ```sql  
    USE Archive  
    GO  
    SELECT type_desc, name, physical_name from sys.database_files  
    ```  
  
3.  Скопируйте следующий скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] в редактор запросов и нажмите кнопку **Выполнить**. Этот код переводит базу данных `Archive` в режим вне сети.  
  
    ```sql  
    USE master  
    EXEC sp_detach_db Archive  
    GO  
    ```  
  
4.  Создайте папку `C:\moved_location`и переместите в нее файлы и папки, перечисленные на шаге 2.  
  
5.  Скопируйте следующий скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] в редактор запросов и нажмите кнопку **Выполнить**. Этот скрипт переводит базу данных `Archive` в режим «в сети».  
  
    ```sql  
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
  
## <a name="see-also"></a>См. также:  
 [sp_detach_db (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)  
  
  
