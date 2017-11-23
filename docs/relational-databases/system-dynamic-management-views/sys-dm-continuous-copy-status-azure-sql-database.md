---
title: "sys.dm_continuous_copy_status (база данных SQL Azure) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_continuous_copy_status_TSQL
- dm_continuous_copy_status_TSQL
- dm_continuous_copy_status
- sys.dm_continuous_copy_status
dev_langs: TSQL
helpviewer_keywords:
- dm_continuous_copy_status
- sys.dm_continuous_copy_status
ms.assetid: 411b2e71-4421-4ef5-900d-5af068750899
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4556ca83115890372c53c28c1ee15adfb0d5d835
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmcontinuouscopystatus-azure-sql-database"></a>sys.dm_continuous_copy_status (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Возвращает строку для каждой пользовательской базы данных (V11), в настоящее время участвует в связи непрерывного копирования георепликации. Если для базы данных-источника инициировано несколько связей непрерывного копирования, эта таблица содержит по одной строке для каждой активной базы данных-получателя.  
  
При использовании базы данных SQL V12 следует использовать [sys.dm_geo_replication_link_status](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md) (поскольку *sys.dm_continuous_copy_status* применяется только к V11).

  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**copy_guid**|**uniqueidentifier**|Уникальный идентификатор реплики базы данных.|  
|**partner_server**|**sysname**|Имя связанного сервера базы данных SQL.|  
|**partner_database**|**sysname**|Имя связанной базы данных на связанном сервере базы данных SQL.|  
|**last_replication**|**datetimeoffset**|Метка времени последней реплицированной транзакции.|  
|**replication_lag_sec**|**int**|Разница во времени в секундах между текущим временем и меткой времени последней, успешно зафиксированной транзакции в базе данных-источнике, которая не была подтверждена активной базой данных-получателем.|  
|**replication_state**|**tinyint**|Состояние репликации непрерывного копирования для этой базы данных. Ниже приведены возможные значения и их описания.<br /><br /> 1: Присвоение начальных значений. Выполняется первоначальное заполнение целевого объекта репликации, который находится в несогласованном состоянии на уровне транзакций. Пока первоначальное заполнение не завершится, подключиться к активной базе данных-получателю нельзя. <br />2: Запаздывание. Активная база данных-получатель в настоящий момент синхронизируется с базой данных-источником и находится в состоянии, согласованном на уровне транзакций.<br />3: повторное заполнение. Активная база данных-получатель автоматически заполняется повторно из-за неустранимой ошибки репликации.<br />4: приостановлено. Это неактивная связь непрерывного копирования. Это состояние обычно означает, что доступной для Interlink полосы пропускания недостаточно для уровня активности транзакций в базе данных-источнике. Однако связь непрерывного копирования не повреждена.|  
|**replication_state_desc**|**nvarchar(256)**|Описание replication_state (одно из следующих значений):<br /><br /> SEEDING<br /><br /> CATCH_UP<br /><br /> RE_SEEDING<br /><br /> SUSPENDED|  
|**is_rpo_limit_reached**|**bit**|Этому параметру всегда задается значение 0.|  
|**is_target_role**|**bit**|0 = Источник связи копирования<br /><br /> 1 = Цель связи копирования|  
|**is_interlink_connected**|**bit**|1 = подключение к Interlink установлено.<br /><br /> 0 = подключение к Interlink не установлено.|  
  
## <a name="permissions"></a>Permissions  
 Для получения данных, требуется членство в **db_owner** роли базы данных. Пользователь dbo, члены **dbmanager** роли базы данных и имя входа sa можно запрашивать данное представление также.  
  
## <a name="remarks"></a>Замечания  
 **Sys.dm_continuous_copy_status** представление создается в **ресурсов** базы данных и отображается во всех базах данных, включая логической базе данных master. Однако запрос этого представления для логической базы данных master возвращает пустой набор.  
  
 Если связь непрерывного копирования прекращается в базе данных строк для этой базы данных в **sys.dm_continuous_copy_status** представление исчезает.  
  
 Как **sys.dm_database_copies** представление, **sys.dm_continuous_copy_status** отражает состояние связи непрерывного копирования, в котором базы данных является либо источника или активной базы данных-получателя . В отличие от **sys.dm_database_copies**, **sys.dm_continuous_copy_status** содержит несколько столбцов, содержащих подробные сведения об операциях и производительности. Эти столбцы содержат **last_replication**, и **replication_lag_sec**...  
  
## <a name="see-also"></a>См. также:  
 [sys.dm_database_copies &#40; База данных Azure SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)   
 [Активная Георепликация хранимых процедур &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/81658ee4-4422-4d73-bf7a-86a07422cb0d)  
  
  
