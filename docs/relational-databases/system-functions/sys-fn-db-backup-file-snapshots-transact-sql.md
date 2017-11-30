---
title: "sys.fn_db_backup_file_snapshots (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/03/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 45010ff2-219f-4086-9ea4-016a6c17cddd
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 30988d44e03a40ffcb8317a603b99633c21c8068
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="sysfndbbackupfilesnapshots-transact-sql"></a>sys.fn_db_backup_file_snapshots (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Возвращает моментальные снимки Azure, связанных с файлами базы данных. Если указанная база данных не найден или если файлы базы данных не хранятся в службе хранилища больших двоичных объектов Microsoft Azure, строки не возвращаются. Использовать в сочетании с системной функцией **sys.sp_delete_backup_file_snapshot** системной хранимой процедуры для идентификации и удаление потерянных резервных копий моментальных снимков. Дополнительные сведения см. в разделе [Резервные копии моментальных снимков файлов для файлов базы данных в Azure](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.fn_db_backup_file_snapshots   
   [ ( database_name ) ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *Имя_базы_данных*  
 Имя запрашиваемой базы данных. Если значение равно NULL, эта функция выполняется в текущей области базы данных.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|file_id|**int**|Идентификатор файла для базы данных. Не допускает значение NULL.|  
|snapshot_time|**nvarchar(260)**|Отметка времени моментального снимка, возвращаемый API-интерфейса REST. Возвращает значение NULL, если моментальный снимок не существует.|  
|snapshot_url|**nvarchar(360)**|Полный URL-адрес файла моментального снимка. Возвращает значение NULL, если моментальный снимок не существует.|  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение VIEW DATABASE STATE на базу данных.  
  
## <a name="see-also"></a>См. также:  
 [sp_delete_backup_file_snapshot &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)   
 [sp_delete_backup (Transact-SQL)](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md)  
  
  
