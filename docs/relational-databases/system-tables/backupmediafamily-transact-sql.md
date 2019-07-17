---
title: backupmediafamily (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- backupmediafamily
- backupmediafamily_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backupmediafamily system table
- backup media [SQL Server], backupmediafamily system table
ms.assetid: ee16de24-3d95-4b2e-a094-78df2514d18a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6ea3fd7937447ba3ed0f3ad89965301dead772cf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68122881"
---
# <a name="backupmediafamily-transact-sql"></a>backupmediafamily (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого семейства носителей. Если семейство носителей хранится на зеркальном наборе носителей, семейство имеет отдельную строку для каждого зеркала в наборе носителей. Эта таблица хранится в **msdb** базы данных.  
    
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**media_set_id**|**int**|Уникальный идентификатор набора носителей, элементом которого является данное семейство. Ссылки на **backupmediaset(media_set_id)**|  
|**family_sequence_number**|**tinyint**|Позиция семейства носителей в наборе носителей.|  
|**media_family_id**|**uniqueidentifier**|Уникальный идентификатор семейства носителей. Может иметь значение NULL.|  
|**media_count**|**int**|Количество носителей в семействе носителей. Может иметь значение NULL.|  
|**logical_device_name**|**nvarchar(128)**|Имя устройства резервного копирования в **sys.backup_devices.name**. Если это временное устройство резервного копирования (в противоположность постоянному устройству резервного копирования в **sys.backup_devices**), значение **logical_device_name** имеет значение NULL.|  
|**physical_device_name**|**nvarchar(260)**|Физическое имя устройства резервного копирования. Может иметь значение NULL. Это поле совместно используется процесс резервного копирования и восстановления. Он может содержать исходный путь назначения резервного копирования или исходный путь восстановления источника. В зависимости от резервного копирования или восстановления, произошла ли сначала на сервере для базы данных. Обратите внимание на то, что последовательных восстановлений из одного файла резервной копии не обновит путь независимо от ее расположение во время восстановления. По этой причине **physical_device_name** поле не может использоваться для восстановления пути, используемого см. в разделе.|  
|**device_type**|**tinyint**|Тип устройства резервного копирования:<br /><br /> 2 = диск;<br /><br /> 5 = лента;<br /><br /> 7 = виртуальное устройство<br /><br /> 9 = хранилища azure<br /><br /> 105 = постоянное устройство резервного копирования.<br /><br /> Может иметь значение NULL.<br /><br /> Все имена постоянных устройств и их номера находятся в **sys.backup_devices**.|  
|**physical_block_size**|**int**|Физический размер блока, используемого для записи семейства носителей. Может иметь значение NULL.|  
|**зеркальный**|**tinyint**|Номер зеркала (0-3).|  
  
## <a name="remarks"></a>Примечания  
 Инструкция RESTORE VERIFYONLY FROM *устройство_резервного_копирования* WITH LOADHISTORY заполняет столбцы **backupmediaset** таблицу с соответствующими значениями из заголовка набора носителей.  
  
 Чтобы уменьшить число строк в данной таблице, а также в других резервных и таблицах журнала, выполните [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) хранимой процедуры.  
  
## <a name="see-also"></a>См. также  
 [Резервное копирование и восстановление таблиц &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile (Transact-SQL)](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupfilegroup (Transact-SQL)](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupmediaset (Transact-SQL)](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupset (Transact-SQL)](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [Системные таблицы (Transact-SQL)](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
