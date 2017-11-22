---
title: "sys.dm_os_volume_stats (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_os_volume_stats_TSQL
- dm_os_volume_stats
- sys.dm_os_volume_stats
- sys.dm_os_volume_stats_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_os_volume_stats dynamic management function
ms.assetid: fa1c58ad-8487-42ad-956c-983f2229025f
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 43d9ead206eb4f5a83d0006c3b23626346b04fe5
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmosvolumestats-transact-sql"></a>sys.dm_os_volume_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о томе (каталоге) операционной системы, в котором хранятся указанные базы данных и файлы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Используйте эту функцию динамического управления для проверки атрибутов физического диска или для получения сведений об объеме свободного пространства в каталоге.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sys.dm_os_volume_stats (database_id, file_id)  
```  
  
##  <a name="Arguments"></a> Аргументы  
 *database_id*  
 Идентификатор базы данных. *database_id* — **int**, не имеет значения по умолчанию. Не может быть NULL.  
  
 *file_id*  
 Идентификатор файла. *file_id* — **int**, не имеет значения по умолчанию. Не может быть NULL.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
||||  
|-|-|-|  
|**Столбец**|**Тип данных**|**Description**|  
|**database_id**|**int**|Идентификатор базы данных. Не может иметь значение null.|  
|**file_id**|**int**|Идентификатор файла. Не может иметь значение null.|  
|**volume_mount_point**|**nvarchar(512)**|Точка подключения, с которой ассоциирован корень тома. Может возвращать пустую строку.|  
|**volume_id**|**nvarchar(512)**|Идентификатор тома операционной системы. Может возвращать пустую строку|  
|**logical_volume_name**|**nvarchar(512)**|Логическое имя тома. Может возвращать пустую строку|  
|**file_system_type**|**nvarchar(512)**|Тип файловой системы тома (например, NTFS, FAT, RAW). Может возвращать пустую строку|  
|**total_bytes**|**bigint**|Общий размер тома в байтах. Не может иметь значение null.|  
|**available_bytes**|**bigint**|Доступное свободное место на томе. Не может иметь значение null.|  
|**supports_compression**|**bit**|Указывает, поддерживает ли том сжатие на уровне операционной системы. Не может иметь значение null.|  
|**supports_alternate_streams**|**bit**|Указывает, поддерживает ли том дополнительные потоки. Не может иметь значение null.|  
|**supports_sparse_files**|**bit**|Указывает, поддерживает ли том разреженные файлы.  Не может иметь значение null.|  
|**is_read_only**|**bit**|Указывает, помечен ли том как доступный только для чтения. Не может иметь значение null.|  
|**is_compressed**|**bit**|Указывает, сжат ли том в настоящее время. Не может иметь значение null.|  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Permissions  
 Необходимо разрешение VIEW SERVER STATE.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-return-total-space-and-available-space-for-all-database-files"></a>A. Получение сведений об общем и доступном пространстве для всех файлов баз данных  
 В следующем примере выполняется возврат значения общего и доступного пространства (в байтах) для всех файлов баз данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT f.database_id, f.file_id, volume_mount_point, total_bytes, available_bytes  
FROM sys.master_files AS f  
CROSS APPLY sys.dm_os_volume_stats(f.database_id, f.file_id);  
```  
  
### <a name="b-return-total-space-and-available-space-for-the-current-database"></a>Б. Получение сведений об общем и доступном пространстве для текущей базы данных  
 В следующем примере выполняется возврат значения общего и доступного пространства (в байтах) для файлов текущей базы данных.  
  
```  
SELECT database_id, f.file_id, volume_mount_point, total_bytes, available_bytes  
FROM sys.database_files AS f  
CROSS APPLY sys.dm_os_volume_stats(DB_ID(f.name), f.file_id);  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.master_files &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
  
  
