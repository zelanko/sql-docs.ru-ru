---
title: "backupfilegroup (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- backupfilegroup_TSQL
- backupfilegroup
dev_langs: TSQL
helpviewer_keywords:
- filegroups [SQL Server], backupfilegroup system table
- backupfilegroup system table
ms.assetid: d26e8fbe-f5c5-4e10-b2bd-0d8e16ea21f9
caps.latest.revision: "53"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 244658ccae187622bf1d67b312867d7b41584182
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="backupfilegroup-transact-sql"></a>backupfilegroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждой файловой группы во время резервного копирования. **backupfilegroup** хранится в **msdb** базы данных.  
  
> [!NOTE]  
>  **Backupfilegroup** таблице показана конфигурация файловой группы базы данных, а не резервный набор данных. Чтобы определить, следует ли включить файл в резервном наборе данных, используйте **is_present** столбец [backupfile](../../relational-databases/system-tables/backupfile-transact-sql.md) таблицы.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**backup_set_id**|**int**|Резервный набор данных, содержащий эту файловую группу.|  
|**name**|**sysname**|Имя файловой группы.|  
|**filegroup_id**|**int**|Идентификатор файловой группы, уникальный в пределах базы данных. Соответствует **data_space_id** в **sys.filegroups**.|  
|**filegroup_guid**|**uniqueidentifier**|Глобальный уникальный идентификатор файловой группы. Может иметь значение NULL.|  
|**type**|**char(2)**|Тип содержимого, может принимать одно из двух значений:<br /><br /> FG = файловая группа «Строки»<br /><br /> SL = файловая группа журнала сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**type_desc**|**nvarchar(60)**|Описание типа функции, может принимать одно из двух значений:<br /><br /> ROWS_FILEGROUP<br /><br /> SQL_LOG_FILEGROUP|  
|**is_default**|**bit**|Файловая группа по умолчанию; используется, если в инструкции CREATE TABLE или CREATE INDEX не указана ни одна из файловых групп.|  
|**is_readonly**|**bit**|1 = Файловая группа доступна только для чтения.|  
|**log_filegroup_guid**|**uniqueidentifier**|Может иметь значение NULL.|  
  
## <a name="remarks"></a>Замечания  
  
> [!IMPORTANT]  
>  Одно и то же имя файловой группы может использоваться в разных базах данных, однако у каждой файловой группы есть свой идентификатор GUID. Таким образом **(backup_set_id filegroup_guid)** является уникальным ключом, идентифицирующим файловую группу в **backupfilegroup**.  
  
 Инструкция RESTORE VERIFYONLY FROM *устройство_резервного_копирования* WITH LOADHISTORY заполняет столбцы **backupmediaset** таблицу с соответствующими значениями из заголовка набора носителей.  
  
 Чтобы уменьшить число строк в данной таблице, а также в других таблицах резервной копии и журнал, выполните [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) хранимой процедуры.  
  
## <a name="see-also"></a>См. также:  
 [Резервное копирование и восстановление таблицы &#40; Transact-SQL &#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile (Transact-SQL)](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupmediafamily (Transact-SQL)](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)   
 [backupmediaset (Transact-SQL)](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupset (Transact-SQL)](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [Системные таблицы &#40; Transact-SQL &#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
