---
title: "backupmediafamily (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2b2435ce3fe98104aaf3bbb857e89779adb221e4
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="backupmediafamily-transact-sql"></a>backupmediafamily (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого семейства носителей. Если семейство носителей хранится на зеркальном наборе носителей, семейство имеет отдельную строку для каждого зеркала в наборе носителей. Эта таблица хранится в **msdb** базы данных.  
    
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**media_set_id**|**int**|Уникальный идентификатор набора носителей, элементом которого является данное семейство. References **backupmediaset(media_set_id)**|  
|**family_sequence_number**|**tinyint**|Позиция семейства носителей в наборе носителей.|  
|**media_family_id**|**uniqueidentifier**|Уникальный идентификатор семейства носителей. Может иметь значение NULL.|  
|**media_count**|**int**|Количество носителей в семействе носителей. Может иметь значение NULL.|  
|**logical_device_name**|**nvarchar(128)**|Имя устройства резервного копирования в **sys.backup_devices.name**. Если это временное устройство резервного копирования (в отличие от постоянного устройства резервного копирования, которое существует в **sys.backup_devices**), значение **logical_device_name** имеет значение NULL.|  
|**physical_device_name**|**nvarchar(260)**|Физическое имя устройства резервного копирования. Может иметь значение NULL.|  
|**device_type**|**tinyint**|Тип устройства резервного копирования:<br /><br /> 2 = диск;<br /><br /> 5 = лента;<br /><br /> 7 = виртуальное устройство<br /><br /> 105 = постоянное устройство резервного копирования.<br /><br /> Может иметь значение NULL.<br /><br /> Все имена постоянных устройств и номера устройств можно найти в **sys.backup_devices**.|  
|**physical_block_size**|**int**|Физический размер блока, используемого для записи семейства носителей. Может иметь значение NULL.|  
|**mirror**|**tinyint**|Номер зеркала (0-3).|  
  
## <a name="remarks"></a>Remarks  
 Инструкция RESTORE VERIFYONLY FROM *устройство_резервного_копирования* WITH LOADHISTORY заполняет столбцы **backupmediaset** таблицу с соответствующими значениями из заголовка набора носителей.  
  
 Чтобы уменьшить число строк в данной таблице, а также в других таблицах резервной копии и журнал, выполните [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) хранимой процедуры.  
  
## <a name="see-also"></a>См. также  
 [Резервное копирование и восстановление таблицы &#40; Transact-SQL &#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile (Transact-SQL)](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupfilegroup (Transact-SQL)](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupmediaset (Transact-SQL)](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupset (Transact-SQL)](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [Системные таблицы &#40; Transact-SQL &#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
