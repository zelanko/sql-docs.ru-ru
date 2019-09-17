---
title: sys. availability_groups_cluster (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.availability_groups_cluster
- availability_groups_cluster
- availability_groups_cluster_TSQL
- sys.availability_groups_cluster_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.availability_groups_cluster catalog view
- Availability Groups [SQL Server], WSFC clusters
ms.assetid: d0f4683f-cdf0-4227-8b68-720ffe58f158
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a9ca998a0b65fff44e71549d1dae879d73288dfb
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70874270"
---
# <a name="sysavailability_groups_cluster-transact-sql"></a>sys.availability_groups_cluster (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает по строке для каждой группы доступности AlwaysOn в кластере WSFC. Каждая строка содержит метаданные группы доступности из кластера WSFC.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|Уникальный идентификатор (GUID) группы доступности.|  
|**name**|**sysname**|Имя группы доступности. Определяемое пользователем имя, которое должно быть уникальным в отказоустойчивом кластере Windows Server (WSFC).|  
|**resource_id**|**nvarchar(40)**|Идентификатор ресурса для ресурса кластера WSFC.|  
|**resource_group_id**|**nvarchar(40)**|Идентификатор группы ресурсов кластера WSFC, принадлежащей к группе доступности.|  
|**failure_condition_level**|**int**|Определяемый пользователем уровень условий сбоя, при котором должен быть запущен автоматический переход на другой ресурс, может принимать одно из следующих целочисленных значений:<br /><br /> 1: Указывает, что следует запустить автоматический переход на другой ресурс при возникновении любой из следующих ситуаций. <br />[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] — Служба не работает.<br />— Аренда группы доступности для подключения к отказоустойчивому кластеру WSFC истекает, так как от экземпляра сервера не получено подтверждение. Дополнительные сведения см. в разделе [Как это работает: время ожидания аренды Always On в SQL Server](https://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-Always%20On-lease-timeout.aspx).<br /><br /> 2: Указывает, что следует запустить автоматический переход на другой ресурс при возникновении любой из следующих ситуаций.  <br />— Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не подключается к кластеру, и превышено заданное пользователем пороговое значение **HEALTH_CHECK_TIMEOUT** группы доступности. <br />-Реплика доступности находится в состоянии сбоя. <br />3: Указывает, что следует запустить автоматический переход на другой ресурс в случае появления критических внутренних ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], таких как потерянные спин-блокировки, серьезные нарушения доступа для записи или формирование слишком больших дампов. Это значение по умолчанию. <br />4: Указывает, что следует запустить автоматический переход на другой ресурс в случае появления не столь серьезных внутренних ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например устойчивое состояние нехватки памяти в пуле внутренних ресурсов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br />5: Указывает, что следует запустить автоматический переход на другой ресурс при любом удовлетворяющим условиям состоянии сбоя, включая:<br />— Исчерпание рабочих потоков SQL Engine. <br />— Обнаружение неразрешимой взаимоблокировки.<br /><br /> Уровни условий сбоя (1–5) варьируются от наименее ограничительного уровня 1 до наиболее ограничительного уровня 5. Заданный уровень условий включает в себя ограничения всех предыдущих уровней. Таким образом, наиболее строгий уровень 5 включает в себя ограничения уровней с 1 по 4, уровень 4 содержит ограничения уровней с 1 по 3 и т. д.<br /><br /> Чтобы изменить это значение, используйте параметр FAILURE_CONDITION_LEVEL инструкции [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] .|  
|**health_check_timeout**|**int**|Время ожидания (в миллисекундах), в течение которого системная хранимая процедура [sp_server_diagnostics](../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md) возвращает сведения о работоспособности сервера, прежде чем предполагается, что экземпляр сервера будет реагировать на запросы или не отвечает. Значение по умолчанию — 30 000 миллисекунд (30 секунд).<br /><br /> Чтобы изменить это значение, используйте параметр HEALTH_CHECK_TIMEOUT инструкции [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] .|  
|**automated_backup_preference**|**tinyint**|Предпочитаемое расположение для выполнения резервного копирования баз данных доступности в этой группе доступности. Одно из следующих значений:<br /><br /> 0: Базой. Резервное копирование должно всегда выполняться в первичной реплике.<br />1: Только вторичная. Создание резервных копий во вторичной реплике является предпочтительным.<br />2: Предпочитать вторичный. Создание резервных копий во вторичной реплике является предпочтительным, но создание резервных копий в первичной реплике также является допустимым при отсутствии вторичных реплик для операций резервного копирования. Это поведение установлено по умолчанию.<br />3: Любая реплика. Приоритет места выполнения резервного копирования отсутствует.<br /><br /> Дополнительные сведения см. в статье [Активные вторичные реплики: резервное копирование во вторичных репликах (группы доступности Always On)](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).|  
|**automated_backup_preference_desc**|**nvarchar(60)**|Описание **AUTOMATED_BACKUP_PREFERENCE**, одно из следующих:<br /><br /> PRIMARY<br /><br /> SECONDARY_ONLY<br /><br /> SECONDARY<br /><br /> None|  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требует разрешения VIEW ANY DEFINITION на экземпляре сервера.  
  
## <a name="see-also"></a>См. также  
 [sys.availability_replicas (Transact-SQL)](../../relational-databases/system-catalog-views/sys-availability-replicas-transact-sql.md)   
 [Группы доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Отслеживание групп доступности (Transact-SQL)](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Отслеживание групп доступности (Transact-SQL)](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  
