---
title: sp_delete_backup (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/03/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 808e50ae-ff6e-4520-9ce2-530591d3d59b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: edb0740ce1bbc0009996849e39bf495c23ba29b0
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.contentlocale: ru-RU
ms.lasthandoff: 07/07/2020
ms.locfileid: "86053721"
---
# <a name="sp_delete_backup-transact-sql"></a>sp_delete_backup (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Удаляет все моментальные снимки и файл резервной копии, которые составляют резервный набор моментальных снимков из указанной базы данных. Эта системная хранимая процедура является единственным рекомендуемым методом управления резервными наборами моментальных снимков. Дополнительные сведения см. в разделе [Резервные копии моментальных снимков файлов для файлов базы данных в Azure](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_delete_backup   
    [ @backup_url = ] backup_metadata_file_url  
    ,[ [ @db_name = ] database_name | NULL ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *[ @backup_url =] backup_meta_file_url*  
 URL-адрес удаляемого архива, который удаляет все моментальные снимки, содержащие указанный резервный набор данных, включая сам файл резервной копии.  
  
 *[ @db_name =] database_name*  
 Имя базы данных, содержащей удаляемый моментальный снимок. Если указано имя базы данных, система проверяет, что указанный URL-адрес резервного копирования является URL-адресом резервной копии для указанной базы данных, и использует [sp_delete_backup_file_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md) для удаления каждого моментального снимка. Если имя базы данных не указано, проверка базы данных не выполняется.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение ALTER ANY DATABASE или разрешение ALTER для указанной базы данных.  
  
## <a name="see-also"></a>См. также  
 [sys. fn_db_backup_file_snapshots &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)   
 [sp_delete_backup_file_snapshot (Transact-SQL)](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)  
  
  
