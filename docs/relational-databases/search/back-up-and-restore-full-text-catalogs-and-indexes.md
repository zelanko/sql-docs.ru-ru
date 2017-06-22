---
title: "Создание резервных копий и восстановление полнотекстовых каталогов и индексов | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-search
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full-text indexes [SQL Server], backing up
- full-text search [SQL Server], back up and restore
- recovery [full-text search]
- backups [SQL Server], full-text indexes
- full-text indexes [SQL Server], restoring
- restore operations [full-text search]
ms.assetid: 6a4080d9-e43f-4b7b-a1da-bebf654c1194
caps.latest.revision: 62
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 36c621b35e944fe536e3a2983113ba7586e6e461
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="back-up-and-restore-full-text-catalogs-and-indexes"></a>Создание резервных копий и восстановление полнотекстовых каталогов и индексов
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  В этом разделе рассказывается о создании резервных копий и восстановлении полнотекстовых индексов, созданных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]полнотекстовый каталог — это логическое понятие, он не хранится в файловой группе. Следовательно, для того чтобы создать резервную копию полнотекстового каталога в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], следует определить все файловые группы, содержащие полнотекстовый индекс, принадлежащий каталогу. Затем необходимо создать резервные копии этих файловых групп, одну за другой.  
  
> [!IMPORTANT]  
>  Импортировать полнотекстовые каталоги можно при обновлении базы данных [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] . Каждый полнотекстовый каталог — это файл базы данных в собственной файловой группе. Чтобы создать резервную копию импортированного каталога, достаточно создать резервную копию его файловой группы. Дополнительные сведения см. в разделе [Резервное копирование и восстановление полнотекстовых каталогов](http://go.microsoft.com/fwlink/?LinkID=121052)электронной документации по [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .  
  
##  <a name="backingup"></a> Резервное копирование полнотекстовых индексов полнотекстового каталога  
  
###  <a name="Find_FTIs_of_a_Catalog"></a> Поиск полнотекстовых индексов полнотекстового каталога  
 Свойства полнотекстовых индексов можно получить с помощью инструкции [SELECT](../../t-sql/queries/select-transact-sql.md) , выбирающей столбцы из представлений каталога [sys.fulltext_indexes](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md) и [sys.fulltext_catalogs](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md) .  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @TableID int;  
SET @TableID = (SELECT OBJECT_ID('AdventureWorks2012.Production.Product'));  
SELECT object_name(@TableID), i.is_enabled, i.change_tracking_state,   
   i.has_crawl_completed, i.crawl_type, c.name as fulltext_catalog_name   
   FROM sys.fulltext_indexes i, sys.fulltext_catalogs c   
   WHERE i.fulltext_catalog_id = c.fulltext_catalog_id;  
GO  
```  
  
  
###  <a name="Find_FG_of_FTI"></a> Поиск файловой группы или файла, содержащего полнотекстовый индекс  
 При создании полнотекстовый индекс размещается в одном из следующих мест.  
  
-   В указанной пользователем файловой группе.  
  
-   В несекционированной таблице — в той же файловой группе, что и базовая таблица или представление.  
  
-   В секционированной таблице — в первичной файловой группе.  
  
> [!NOTE]  
>  Сведения о создании полнотекстового индекса см. в разделах [Создание полнотекстовых индексов и управление ими](../../relational-databases/search/create-and-manage-full-text-indexes.md) и [CREATE FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/create-fulltext-index-transact-sql.md).  
  
 Чтобы найти файловую группу полнотекстового индекса таблицы или представления, можно использовать следующий запрос, в котором *object_name* — это имя таблицы или представления:  
  
```  
SELECT name FROM sys.filegroups f, sys.fulltext_indexes i   
   WHERE f.data_space_id = i.data_space_id   
      and i.object_id = object_id('object_name');  
GO  
  
```  
  
  
###  <a name="Back_up_FTIs_of_FTC"></a> Создание резервных копий файловых групп, содержащих полнотекстовые индексы  
 После того как были найдены файловые группы с индексами полнотекстового каталога, следует создать резервные копии всех файловых групп. Во время резервного копирования удалять или добавлять полнотекстовые каталоги нельзя.  
  
 При первом резервном копировании необходимо создать полную резервную копию файла. После того как для файловой группы была создана полная резервная копия файла, резервное копирование можно выполнять, сохраняя только изменения в файловой группе путем создания ряда из нескольких разностных резервных копий файла, основанных на полной резервной копии файла.  
  
 **Создание резервных копий файлов и файловых групп**  
  
-   [Резервное копирование файлов и файловых групп (SQL Server)](../../relational-databases/backup-restore/back-up-files-and-filegroups-sql-server.md)  
  
-   [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)  
  
  
##  <a name="Restore_FTI"></a> Восстановление полнотекстового индекса  
 При восстановлении резервной копии файловой группы выполняется восстановление файлов полнотекстового индекса, а также остальных файлов файловой группы. По умолчанию файловая группа восстанавливается в том месте на диске, где была создана резервная копия.  
  
 Если во время создания резервной копии таблица с полнотекстовым индексом находилась в режиме «в сети» и в ней производилось заполнение, то после восстановления заполнение продолжится.  
  
 **Восстановление файловой группы**  
  
-   [Восстановление файлов и файловых групп (SQL Server)](../../relational-databases/backup-restore/restore-files-and-filegroups-sql-server.md)  
  
-   [Восстановление файлов и файловых групп поверх существующих файлов (SQL Server)](../../relational-databases/backup-restore/restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
-   [Восстановление файлов в новое место (SQL Server)](../../relational-databases/backup-restore/restore-files-to-a-new-location-sql-server.md)  
  
-   [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)  
  
  
## <a name="see-also"></a>См. также:  
 [Управление и наблюдение за полнотекстовым поиском для экземпляра сервера](../../relational-databases/search/manage-and-monitor-full-text-search-for-a-server-instance.md)   
 [Обновление полнотекстового поиска](../../relational-databases/search/upgrade-full-text-search.md)  
  
  
