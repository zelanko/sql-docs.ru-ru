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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6fdfdf5b38c6f346f7bdaac67281d68821107fab
ms.sourcegitcommit: 5a9ec5e28543f106bf9e7aa30dd0a726bb750e25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/08/2020
ms.locfileid: "82925138"
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
|**failure_condition_level**|**int**|Определяемый пользователем уровень условий сбоя, при котором должен быть запущен автоматический переход на другой ресурс, может принимать одно из следующих целочисленных значений:<br /><br /> 1: указывает, что автоматический переход на другой ресурс должен быть инициирован при выполнении любого из следующих условий. <br />— [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Служба не работает.<br />— Аренда группы доступности для подключения к отказоустойчивому кластеру WSFC истекает, так как от экземпляра сервера не получено подтверждение. Дополнительные сведения см. в разделе [Принцип работы. Время ожидания аренды AlwaysOn в SQL Server](https://techcommunity.microsoft.com/t5/sql-server-support/how-it-works-sql-server-alwayson-lease-timeout/ba-p/317268).<br /><br /> 2: указывает, что автоматический переход на другой ресурс должен быть инициирован при выполнении любого из следующих условий.  <br />— Экземпляр не [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключается к кластеру, и превышено заданное пользователем пороговое значение **HEALTH_CHECK_TIMEOUT** группы доступности. <br />-Реплика доступности находится в состоянии сбоя. <br />3: указывает, что автоматический переход на другой ресурс должен быть инициирован при критических [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] внутренних ошибках, таких как потерянные спин-блокировки, серьезные нарушения доступа для записи или слишком большой объем дампа. Это значение по умолчанию. <br />4: указывает, что автоматический переход на другой ресурс должен быть инициирован на умеренных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] внутренних ошибках, таких как устойчивое состояние нехватки памяти во [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] внутреннем пуле ресурсов.<br />5: указывает, что автоматический переход на другой ресурс должен быть инициирован при любых условиях полного сбоя, в том числе:<br />— Исчерпание рабочих потоков SQL Engine. <br />— Обнаружение неразрешимой взаимоблокировки.<br /><br /> Уровни условий сбоя (1–5) варьируются от наименее ограничительного уровня 1 до наиболее ограничительного уровня 5. Заданный уровень условий включает в себя ограничения всех предыдущих уровней. Таким образом, наиболее строгий уровень 5 включает в себя ограничения уровней с 1 по 4, уровень 4 содержит ограничения уровней с 1 по 3 и т. д.<br /><br /> Чтобы изменить это значение, используйте параметр FAILURE_CONDITION_LEVEL инструкции [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] .|  
|**health_check_timeout**|**int**|Время ожидания (в миллисекундах), в течение которого [sp_server_diagnostics](../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md) системная хранимая процедура возвращает сведения о работоспособности сервера, прежде чем предполагается, что экземпляр сервера будет реагировать на запросы или не отвечает. Значение по умолчанию — 30 000 миллисекунд (30 секунд).<br /><br /> Чтобы изменить это значение, используйте параметр HEALTH_CHECK_TIMEOUT инструкции [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] .|  
|**automated_backup_preference**|**tinyint**|Предпочитаемое расположение для выполнения резервного копирования баз данных доступности в этой группе доступности. Принимает одно из следующих значений:<br /><br /> 0: основной. Резервное копирование должно всегда выполняться в первичной реплике.<br />1: только вторичная. Создание резервных копий во вторичной реплике является предпочтительным.<br />2: предпочитать вторичную. Создание резервных копий во вторичной реплике является предпочтительным, но создание резервных копий в первичной реплике также является допустимым при отсутствии вторичных реплик для операций резервного копирования. Это поведение по умолчанию.<br />3. Любая реплика. Приоритет места выполнения резервного копирования отсутствует.<br /><br /> Дополнительные сведения см. в статье [Активные вторичные реплики: резервное копирование во вторичных репликах (группы доступности Always On)](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).|  
|**automated_backup_preference_desc**|**nvarchar(60)**|Описание **AUTOMATED_BACKUP_PREFERENCE**, одно из следующих:<br /><br /> PRIMARY<br /><br /> SECONDARY_ONLY<br /><br /> SECONDARY<br /><br /> None|  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требует разрешения VIEW ANY DEFINITION на экземпляре сервера.  
  
## <a name="see-also"></a>См. также  
 [sys. availability_replicas &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-availability-replicas-transact-sql.md)   
 [Always On группы доступности &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Мониторинг групп доступности &#40;&#41;Transact-SQL](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Отслеживание групп доступности (Transact-SQL)](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  
