---
title: RestoreHistory (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- restorehistory
- restorehistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- restorehistory system table
ms.assetid: 9140ecc1-d912-4d76-ae70-e2a857da6d44
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8f042e3948af90c8eeda86490e1bdda53a181f8d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="restorehistory-transact-sql"></a>restorehistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждой операции восстановления. Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**restore_history_id**|**int**|Уникальный идентификационный номер, который определяет каждую операцию восстановления. Удостоверение, первичный ключ.|  
|**restore_date**|**datetime**|Дата и время завершения операции восстановления. Может иметь значение NULL.|  
|**destination_database_name**|**nvarchar(128)**|Имя целевой базы данных для операции восстановления. Может иметь значение NULL.|  
|**user_name**|**nvarchar(128)**|Имя пользователя, выполнявшего операцию восстановления. Может иметь значение NULL.|  
|**backup_set_id**|**int**|Уникальный идентификационный номер, которым определяется восстанавливаемый резервный набор данных. Ссылки на **backupset(backup_set_id)**.|  
|**restore_type**|**char(1)**|Тип операции восстановления:<br /><br /> D = база данных<br /><br /> F = Файл<br /><br /> G = Файловая группа<br /><br /> I = Дифференциал<br /><br /> L = журнал<br /><br /> V = Только проверка<br /><br /> Может иметь значение NULL.|  
|**Замените**|**бит**|Показывает, определен ли операцией восстановления параметр REPLACE:<br /><br /> 1 = Определен<br /><br /> 0 = Не определен<br /><br /> Может иметь значение NULL.<br /><br /> Если база данных возвращается к состоянию по моментальному снимку базы данных, значение 0 является единственным параметром.|  
|**recovery**|**бит**|Показывает, определен ли операцией восстановления параметр RECOVERY или NORECOVERY:<br /><br /> 1 = RECOVERY<br /><br /> Может иметь значение NULL.<br /><br /> Если база данных состоянию моментальный снимок базы данных, 1 является единственным параметром.<br /><br /> 0 = NORECOVERY|  
|**Перезагрузка**|**бит**|Показывает, определен ли операцией восстановления параметр RESTART:<br /><br /> 1 = Определен<br /><br /> 0 = Не определен<br /><br /> Может иметь значение NULL.<br /><br /> Если база данных возвращается к состоянию по моментальному снимку базы данных, значение 0 является единственным параметром.|  
|**stop_at**|**datetime**|Момент времени, когда база данных была восстановлена. Может иметь значение NULL.|  
|**device_count**|**tinyint**|Количество устройств, вовлеченных в операцию восстановления. Это число может быть меньше количества носителей резервной копии. Может иметь значение NULL.<br /><br /> Если база данных возвращается к состоянию по моментальному снимку базы данных, это число всегда равно 1.|  
|**stop_at_mark_name**|**nvarchar(128)**|Показывает, что восстановление совершается к состоянию на момент выполнения транзакции, содержащей именованную метку. Может иметь значение NULL.<br /><br /> Если база данных возвращается к состоянию по моментальному снимку базы данных, используется значение NULL.|  
|**stop_before**|**бит**|Показывает, была ли включена транзакция, содержащая именованную метку, в процесс восстановления:<br /><br /> 0 = Процесс восстановления был остановлен перед помеченной транзакцией.<br /><br /> 1 = Помеченная транзакция была включена в процесс восстановления.<br /><br /> Может иметь значение NULL.<br /><br /> Если база данных возвращается к состоянию по моментальному снимку базы данных, используется значение NULL.|  
  
## <a name="remarks"></a>Замечания  
 Чтобы уменьшить число строк в данной таблице, а также в других таблицах резервной копии и журнал, выполните [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) хранимой процедуры.  
  
## <a name="see-also"></a>См. также  
 [Резервное копирование и восстановление таблицы &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [restorefile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/restorefile-transact-sql.md)   
 [restorefilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)   
 [Системные таблицы (Transact-SQL)](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
