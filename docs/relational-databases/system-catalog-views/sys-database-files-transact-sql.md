---
title: sys.database_files (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 09/19/2016
ms.prod: ''
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.database_files
- sys.database_files_TSQL
- database_files
- database_files_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_files catalog view
ms.assetid: 0f5b0aac-c17d-4e99-b8f7-d04efc9edf44
caps.latest.revision: 61
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: f50b9b9da7eb904222ef307355e86c91a093db5b
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39550314"
---
# <a name="sysdatabasefiles-transact-sql"></a>sys.database_files (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Содержит по одной строке для каждого из файлов базы данных, в которых она хранится. Это представление на каждую базу данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**file_id**|**int**|Идентификатор файла в базе данных.|  
|**file_guid**|**uniqueidentifier**|Идентификатор GUID файла.<br /><br /> NULL = база данных обновлена с предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**type**|**tinyint**|Тип файла:<br /><br /> 0 = строки (включает файлы полнотекстовых каталогов, которые обновляются или создаются в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])<br /><br /> 1 = журнал.<br /><br /> 2 = FILESTREAM.<br /><br /> 3 = [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> 4 = полнотекстовый (полнотекстовые каталоги с датой, более ранней, чем [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]; полнотекстовые каталоги, которые были обновлены или созданы в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], сообщат о типе файлов 0).|  
|**type_desc**|**nvarchar(60)**|Описание типа файла:<br /><br /> ROWS (включает файлы полнотекстовых каталогов, которые обновляются или создаются в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).<br /><br /> LOG<br /><br /> FILESTREAM<br /><br /> FULLTEXT (полнотекстовые каталоги в версии, предшествующей [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).|  
|**data_space_id**|**int**|Значение может быть больше или равно 0. Значение, равное 0, представляет файл журнала базы данных, а значение больше 0 представляет идентификатор файловой группы, в которой хранится этот файл данных.|  
|**name**|**sysname**|Логическое имя файла в базе данных.|  
|**physical_name**|**nvarchar(260)**|Имя файла в операционной системе. Если база данных размещается с AlwaysOn [вторичная реплика](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md), **physical_name** указывает на папку первичной реплики базы данных. Правильное расположение файла для чтения базы данных-получателя, выполните запрос [sys.sysaltfiles](../../relational-databases/system-compatibility-views/sys-sysaltfiles-transact-sql.md).|  
|**state**|**tinyint**|Состояние файла:<br /><br /> 0 = ONLINE<br /><br /> 1 = RESTORING<br /><br /> 2 = RECOVERING<br /><br /> 3 = RECOVERY_PENDING<br /><br /> 4 = SUSPECT<br /><br /> 5 = [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> 6 = OFFLINE<br /><br /> 7 = DEFUNCT|  
|**state_desc**|**nvarchar(60)**|Описание состояния файла:<br /><br /> ONLINE<br /><br /> RESTORING<br /><br /> RECOVERING<br /><br /> RECOVERY_PENDING<br /><br /> SUSPECT<br /><br /> OFFLINE<br /><br /> DEFUNCT<br /><br /> Дополнительные сведения см. в разделе [Состояния файлов](../../relational-databases/databases/file-states.md).|  
|**size**|**int**|Текущий размер файла в страницах по 8 КБ.<br /><br /> 0 = не определено.<br /><br /> Для моментального снимка базы данных аргумент size отражает максимальное пространство, которое моментальный снимок может использовать только для файла.<br /><br /> Для контейнеров файловых групп FILESTREAM размер отражает текущий используемый размер контейнера.|  
|**max_size**|**int**|Максимальный размер файла в страницах по 8 КБ:<br /><br /> 0 = Увеличение размера запрещено.<br /><br /> -1 = размер файла может увеличиваться до полного заполнения диска.<br /><br /> 268435456 = файл журнала может увеличиваться до 2 ТБ.<br /><br /> Для контейнеров файловых групп FILESTREAM max_size отражает максимальный размер контейнера.<br /><br /> Обратите внимание на то, что базы данных, которые обновляются с размером файла журнала неограниченного возвращают -1 для максимального размера файла журнала.|  
|**рост**|**int**|0 = Файл имеет фиксированный размер и не будет увеличиваться.<br /><br /> >0 = Размер файла будет увеличиваться автоматически.<br /><br /> Если значение is_percent_growth = 0, шаг увеличения размера указывается в единицах по 8 КБ, с округлением до ближайших 64 КБ.<br /><br /> Если значение аргумента is_percent_growth = 1, шаг увеличения размера выражается в процентах от общего размера.|  
|**is_media_read_only**|**bit**|1 = файл находится на носителе только для чтения.<br /><br /> 0 = файл размещен на носителе для чтения-записи.|  
|**is_read_only**|**bit**|1 = файл помечен как файл только для чтения.<br /><br /> 0 = файл помечен для чтения-записи.|  
|**is_sparse**|**bit**|1 = разреженный файл.<br /><br /> 0 = неразреженный файл.<br /><br /> Дополнительные сведения см. в разделе [Просмотр размера разреженного файла снимка базы данных (Transact-SQL)](../../relational-databases/databases/view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md).|  
|**значение аргумента is_percent_growth**|**bit**|1 = размер файла увеличивается в процентах.<br /><br /> 0 = абсолютное увеличение размера в страницах.|  
|**is_name_reserved**|**bit**|1 = имя удаленного файла (name или physical_name) доступно для использования только после следующего резервного копирования журнала. После того как файлы удалены из базы данных, логические имена остаются в зарезервированном состоянии до следующего резервного копирования журнала. Этот столбец является важным только в случае использования модели полного восстановления и модели восстановления с неполным протоколированием.|  
|**create_lsn**|**numeric(25,0)**|Регистрационный номер транзакции в журнале (LSN), на котором создан файл.|  
|**drop_lsn**|**numeric(25,0)**|Номер LSN, с которым файл удален.<br /><br /> 0 = имя файла недоступно для повторного использования.|  
|**read_only_lsn**|**numeric(25,0)**|Номер LSN, на котором файловая группа, содержащая файл, изменила тип с «для чтения и записи» на «только для чтения» (самое последнее изменение).|  
|**read_write_lsn**|**numeric(25,0)**|Номер LSN, на котором файловая группа, содержащая файл, изменила тип с «только для чтения» на «для чтения и записи» (самое последнее изменение).|  
|**differential_base_lsn**|**numeric(25,0)**|Основа для разностных резервных копий. Экстенты данных, измененных после того, как этот номер LSN будет включен в разностную резервную копию.|  
|**differential_base_guid**|**uniqueidentifier**|Уникальный идентификатор базовой резервной копии, на которой будет основываться разностная резервная копия.|  
|**differential_base_time**|**datetime**|Время, соответствующее differential_base_lsn.|  
|**redo_start_lsn**|**numeric(25,0)**|Номер LSN, с которого должен начаться следующий накат.<br /><br /> Равно NULL за исключением случаев, когда значение аргумента state = RESTORING или значение аргумента state = RECOVERY_PENDING.|  
|**redo_start_fork_guid**|**uniqueidentifier**|Уникальный идентификатор точки вилки восстановления. Значение аргумента first_fork_guid следующей восстановленной резервной копии журнала должно совпадать с этим значением. Представляет текущее состояние файла.|  
|**redo_target_lsn**|**numeric(25,0)**|Номер LSN, на котором накат в режиме «в сети» по данному файлу может остановиться.<br /><br /> Равно NULL за исключением случаев, когда значение аргумента state = RESTORING или значение аргумента state = RECOVERY_PENDING.|  
|**redo_target_fork_guid**|**uniqueidentifier**|Вилка восстановления, на которой файл может быть восстановлен. Используется в паре с redo_target_lsn.|  
|**backup_lsn**|**numeric(25,0)**|Номер LSN самых новых данных или разностная резервная копия файла.|  
  
> [!NOTE]  
>  При удалении или перестройке больших индексов либо удалении или усечении больших таблиц компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] откладывает фактическое освобождение страниц и связанных блокировок до момента фиксации транзакции. Отложенные операции удаления не освобождают выделенное место немедленно. Следовательно, значения, полученные из sys.database_files сразу после удаления или усечения больших объектов, могут не соответствовать фактическому размеру свободного места на диске.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  

## <a name="examples"></a>Примеры  
Следующая инструкция возвращает имя, размер файла и объем свободного места для каждого файла базы данных.

```
SELECT name, size/128.0 FileSizeInMB,
size/128.0 - CAST(FILEPROPERTY(name, 'SpaceUsed') AS int)/128.0 
   AS EmptySpaceInMB
FROM sys.database_files;
```
Дополнительные сведения, при использовании [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], см. в разделе [определение размера базы данных в базе данных SQL Azure версии 12](https://blogs.msdn.microsoft.com/sqlcat/2016/09/21/determining-database-size-in-azure-sql-database-v12/) в блоге группы консультирования клиентов SQL.
  
## <a name="see-also"></a>См. также  
 [Представления каталогов баз данных и файлов (Transact-SQL)](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [Состояния файла](../../relational-databases/databases/file-states.md)   
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.master_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [Database Files and Filegroups](../../relational-databases/databases/database-files-and-filegroups.md)   
 [sys.data_spaces (Transact-SQL)](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)  
  
  
