---
title: managed_backup.fn_available_backups (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- smart_admin.fn_available_backups
- smart_admin.fn_available_backups_TSQL
- fn_available_backups_TSQL
- fn_available_backups
dev_langs:
- TSQL
helpviewer_keywords:
- fn_available_backups
- smart_admin.fn_available_backups
ms.assetid: 7aa84474-16e5-49bd-a703-c8d1408ef107
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6d94d3127a5957b1684133019cf4991cba7adbff
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47769450"
---
# <a name="managedbackupfnavailablebackups-transact-sql"></a>managed_backup.fn_available_backups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Возвращает таблицу, где нуль, одна или несколько строк, для доступных файлов резервных копий для указанной базы данных. Возвращаемые файлы резервных копий являются резервными копиями, созданными [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
managed_backup.fn_available_backups ([@database_name = ] 'database name')  
```  
  
##  <a name="Arguments"></a> Аргументы  
 @database_name  
 Имя базы данных. @database_name Это NVARCHAR(512).  
  
## <a name="table-returned"></a>Возвращаемая таблица  
 Таблица имеет уникальное кластеризованное ограничение в (database_guid, backup_start_date и first_lsn, backup_type).   
Если база данных удалена, затем создана повторно, возвращаются резервные наборы данных для всех баз данных. Выходные данные упорядочиваются по database_guid, уникально идентифицирующим каждую базу данных.   
Если в LSN имеются разрывы, означающие разрыв в цепочке журналов, таблица будет содержать отдельную строку для каждого пропущенного сегмента номера LSN.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|Backup_path|NVARCHAR(260) COLLATE Latin1_General_CI_AS_KS_WS|URL-адрес файла резервной копии.|  
|backup_type|NVARCHAR(6)|«DB» для резервной копии базы данных; «LOG» для резервной копии журналов|  
|expiration_date|DATETIME|Дата, в которую ожидается удаление этого файла. Эта настройка основывается на возможности восстановить базу данных до определенного момента времени внутри заданного срока хранения.|  
|database_guid|UNIQUEIDENTIFIER|Значение GUID для указанной базы данных.  GUID однозначно определяет базу данных.|  
|first_lsn|NUMERIC(25, 0)|Регистрационный номер транзакции в журнале для первой или самой ранней записи журнала в резервном наборе данных. Может иметь значение NULL.|  
|last_lsn|NUMERIC(25, 0)|Регистрационный номер транзакции в журнале для следующей записи журнала после резервного набора данных. Может иметь значение NULL.|  
|backup_start_date|DATETIME|Дата и время начала операции резервного копирования.|  
|backup_finish_date|NVARCHAR(128)|Дата и время окончания операции резервного копирования.|  
|machine_name|NVARCHAR(128)|Имя компьютера, на котором установлен экземпляр SQL Server и выполняется [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|  
|last_recovery_fork_id|UNIQUEIDENTIFIER|Идентификационный номер для конечной вилки восстановления.|  
|first_recovery_fork_id|UNIQUEIDENTIFIER|Идентификатор начальной вилки восстановления. Для резервного копирования данных параметр first_recovery_fork_guid равен last_recovery_fork_guid.|  
|fork_point_lsn|NUMERIC(25, 0)|Если значение first_recovery_fork_id не равно значению last_recovery_fork_id, данный параметр представляет собой регистрационный номер транзакции в журнале для вилки. В противном случае - значение NULL.|  
|availability_group_guid|UNIQUEIDENTIFIER|Если базы данных является базой данных Always On, это идентификатор GUID группы доступности. В противном случае — значение NULL.|  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуется **ВЫБЕРИТЕ** разрешения для данной функции.  
  
## <a name="examples"></a>Примеры  
 В следующем примере перечисляются все доступные резервные копии, созданные посредством [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] для базы данных «MyDB».  
  
```  
SELECT *   
FROM managed_backup.fn_available_backups ('MyDB')  
  
```  
  
## <a name="see-also"></a>См. также  
 [SQL Server управляемое резервное копирование в Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)   
 [Восстановление из резервных копий в Microsoft Azure](../../relational-databases/backup-restore/restoring-from-backups-stored-in-microsoft-azure.md)  
  
  
