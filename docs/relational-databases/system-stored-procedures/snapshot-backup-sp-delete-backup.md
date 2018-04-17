---
title: sp_delete_backup (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/03/2015
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 808e50ae-ff6e-4520-9ce2-530591d3d59b
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 26f0dde7c29de4e9ded31217f5da6fdff952def2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="spdeletebackup-transact-sql"></a>sp_delete_backup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Удаляет все моментальные снимки и файл резервной копии, составляют набор из указанной базы данных резервной копии моментального снимка. Данная системная хранимая процедура рекомендуется только для управления резервных наборов данных снимков. Дополнительные сведения см. в разделе [Резервные копии моментальных снимков файлов для файлов базы данных в Azure](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_delete_backup   
    [ @backup_url = ] backup_metadata_file_url  
    ,[ [ @db_name = ] database_name | NULL ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *[ @backup_url = ] backup_meta_file_url*  
 URL-адрес в резервной копии для удаления, который удаляет все снимки, из которых состоит указанный резервный набор, включая файл резервной копии.  
  
 *[ @db_name =] имя_базы_данных*  
 Имя базы данных, содержащей моментальный снимок для удаления. Если имя базы данных не предоставлен, система проверяет, что URL-адрес резервного копирования предоставлен резервного копирования URL-адрес для указанной базы данных и использует [sp_delete_backup_file_snapshot &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md) удалить каждый моментальный снимок. Если имя базы данных не указано, эта проверка базы данных не выполняется.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение ALTER ANY DATABASE или разрешение ALTER в указанной базе данных.  
  
## <a name="see-also"></a>См. также  
 [sys.fn_db_backup_file_snapshots &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)   
 [sp_delete_backup_file_snapshot (Transact-SQL)](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)  
  
  
