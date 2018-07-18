---
title: sp_delete_backup_file_snapshot (Transact-SQL) | Документация Майкрософт
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5afe5530-a404-4fa5-af3c-bc7c3ca43ce6
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 12cb91c23c87e32d25d73f551d7aa6b76fa66288
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036212"
---
# <a name="spdeletebackupfilesnapshot-transact-sql"></a>sp_delete_backup_file_snapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Удаляет указанный моментального снимка резервной копии из указанной базы данных. Используется системная хранимая процедура в сочетании с **sys.fn_db_backup_file_snapshots** системную функцию выявления и удаления потерянных моментальных снимков резервных копий. Дополнительные сведения см. в разделе [Резервные копии моментальных снимков файлов для файлов базы данных в Azure](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  

  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_delete_backup_file_snapshot  
    [ @db_name = ] N’<database_name>  
    , [ @snapshot_url = ] N’<snapshot_url>  
```  
  
## <a name="arguments"></a>Аргументы  
 *[ @db_name =] имя_базы_данных*  
 Имя базы данных, содержащей моментального снимка может быть удален, указанное в виде строки Юникода.  
  
 *[ @snapshot_url =] snapshot_url*  
 URL-адрес моментального снимка, может быть удален, указанное в виде строки Юникода.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение ALTER ANY DATABASE.  
  
## <a name="see-also"></a>См. также  
 [sys.fn_db_backup_file_snapshots &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)   
 [sp_delete_backup (Transact-SQL)](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md)  
  
  
