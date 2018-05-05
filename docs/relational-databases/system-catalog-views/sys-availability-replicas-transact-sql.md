---
title: sys.availability_replicas (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 10/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- availability_replicas_TSQL
- availability_replicas
- sys.availability_replicas
- sys.availability_replicas_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.availability_replicas catalog view
ms.assetid: 0a06e9b6-a1e4-4293-867b-5c3f5a8ff62c
caps.latest.revision: 62
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 016a65e7606e43ec0eb567b7a4e17f07fd2d950f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysavailabilityreplicas-transact-sql"></a>sys.availability_replicas (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

Возвращает по строке для каждой из реплик доступности, принадлежащих к любой группе доступности AlwaysOn в отказоустойчивом кластере WSFC.  
  
Если экземпляр локального сервера не может связаться с отказоустойчивым кластером, например, по причине останова кластера или потери кворума, то будут возвращены строки только для локальных реплик доступности. Эти строки будут содержать только столбцы данных, которые локально кэшируются в метаданные.  
  
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**replica_id**|**uniqueidentifier**|Уникальный идентификатор реплики.|  
|**group_id**|**uniqueidentifier**|Уникальный идентификатор группы доступности, к которой относится реплика.|  
|**replica_metadata_id**|**int**|Идентификатор локального объекта метаданных для реплик доступности в компоненте Database Engine.|  
|**replica_server_name**|**nvarchar(256)**|Имя сервера экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на котором размещена данная реплика, а также имя экземпляра, если экземпляр не является используемым по умолчанию.|  
|**owner_sid**|**varbinary(85)**|SID (идентификатор безопасности), зарегистрированный на данном экземпляре сервера для внешнего владельца реплики доступности.<br /><br /> Значение NULL для нелокальных реплик доступности.|  
|**endpoint_url**|**nvarchar(128)**|Строковое представление определяемой пользователем конечной точки зеркального отображения базы данных, которое используется соединениями первичной реплики со вторичной для синхронизации данных. Сведения о синтаксисе конечной точки URL-адресов см. в разделе [Указание URL-адреса конечной точки при добавлении или изменении реплики доступности (SQL Server)](../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md).<br /><br /> NULL = не удалось связаться с отказоустойчивым кластером WSFC.<br /><br /> Чтобы изменить эту конечную точку, используйте параметр ENDPOINT_URL [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции.|  
|**availability_mode**|**tinyint**|Режим доступности реплики может быть одним из следующих.<br /><br /> 0 &#124; асинхронной фиксации. Первичная реплика может фиксировать транзакции, не ожидая, пока вторичная реплика запишет запись журнала транзакций на диск.<br /><br /> 1 &#124; синхронной фиксации. Первичная реплика ожидает возможности выполнения фиксации транзакции, пока вторичная реплика записывает транзакцию на диск.<br /><br />4 &#124; только конфигурацию. Первичная реплика отправляет метаданные конфигурации группы доступности в реплике синхронно. Пользовательские данные не передаются в реплике. В SQL Server CU1 2017 г. и более поздней версии.<br /><br /> Дополнительные сведения см. в разделе [Режимы доступности (группы доступности AlwaysOn)](../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md).|  
|**availability_mode_desc**|**nvarchar(60)**|Описание **доступности\_режим**, одно из:<br /><br /> АСИНХРОННЫЕ\_ФИКСАЦИИ<br /><br /> СИНХРОННЫЕ\_ФИКСАЦИИ<br /><br /> КОНФИГУРАЦИЯ\_ТОЛЬКО<br /><br /> Чтобы изменить режим доступности реплики доступности, используйте параметр AVAILABILITY_MODE [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции.<br/><br>Нельзя изменить режим доступности реплики конфигурации\_только. Невозможно изменить конфигурацию\_реплики только для получателей или основной реплики. |  
|**Переход на другой ресурс\_режим**|**tinyint**|[Режим отработки отказа](../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md) реплики доступности, одно из:<br /><br /> 0 &#124; перехода на другой ресурс вручную. Если переход на вторичную реплику установлен в режим отработки отказа вручную, то он должен быть инициирован вручную администратором базы данных. Тип выполняемой отработки отказа зависит от того, была ли синхронизирована вторичная реплика следующим образом:<br /><br /> Если реплика доступности не была синхронизирована или синхронизация еще выполняется, то может быть выполнена только принудительная отработка отказа (с возможной потерей данных).<br /><br /> Если режим доступности установлен на синхронную фиксацию (**доступности\_режим** = 1) и группа доступности в настоящее время отработки отказа синхронизированной, вручную без может произойти потеря данных.<br /><br /> 1 &#124; автоматического перехода на другой ресурс. Реплика является потенциальной целью для автоматического перехода на другой ресурс.  Автоматическая отработка отказа поддерживается только в том случае, если режим доступности установлен на синхронную фиксацию (**доступности\_режим** = 1) и группа доступности в состоянии synchronized.<br /><br /> Чтобы просмотреть свертку состояния синхронизации базы данных для каждой базы данных доступности в группе доступности, используйте **синхронизации\_работоспособности** и **синхронизации\_работоспособности\_desc** столбцы [sys.dm_hadr_availability_replica_states](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql.md) динамическое административное представление. Свертка проверяет состояние синхронизации для каждой базы данных доступности, а также режим доступности для ее реплики доступности.<br /><br /> **Примечание:** Чтобы просмотреть состояние синхронизации базы данных доступности, запросите **синхронизации\_состояние** и **синхронизации\_работоспособности** столбцы [sys.dm_hadr_database_replica_states](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md) динамическое административное представление.|  
|**Переход на другой ресурс\_режим\_desc**|**nvarchar(60)**|Описание **перехода на другой ресурс\_режим**, одно из:<br /><br /> MANUAL<br /><br /> AUTOMATIC<br /><br /> Чтобы изменить режим отработки отказа, используйте отработки ОТКАЗА\_параметр режима [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции.|  
|**сеанс\_время ожидания**|**int**|Интервал времени ожидания в секундах. Интервал времени ожидания — это максимальное время, в течение которого реплика ожидает получения сообщения от другой реплики перед тем, как соединение между первичной и вторичной репликой будет признано несостоявшимся. Время ожидания сеанса определяет, связаны ли вторичные реплики с первичной.<br /><br /> При обнаружении ошибки соединения с вторичной репликой, первичная реплика считает, что вторичная реплика не\_SYNCHRONIZED. При обнаружении ошибки соединения с первичной репликой вторичная реплика просто пытается установить соединение повторно.<br /><br /> **Примечание:** промежутки времени ожидания сеанса не вызывают автоматический переход на другой ресурс.<br /><br /> Чтобы изменить это значение, используйте параметр SESSION_TIMEOUT [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции.|  
|**основной\_роли\_Разрешить\_подключений**|**tinyint**|Допускается ли наличие всех соединений или только соединений для чтения и записи, одно из следующих значений:<br /><br /> 2 = все (по умолчанию)<br /><br /> 3 = чтение и запись|  
|**основной\_роли\_Разрешить\_подключений\_desc**|**nvarchar(60)**|Описание **основной\_роли\_Разрешить\_подключений**, одно из:<br /><br /> ALL<br /><br /> ЧТЕНИЕ\_ЗАПИСИ|  
|**вторичный\_роли\_Разрешить\_подключений**|**tinyint**|Указывает, могут ли базы данных заданной реплики доступности, играющей роль вторичной (т. е. служащей вторичной репликой), принимать соединения от клиентов. Может принимать одно из следующих значений:<br /><br /> 0 = Нет. Не допускаются соединения к базам данных из вторичной реплики, к базам данных также невозможен доступ только для чтения. Это параметр по умолчанию.<br /><br /> 1 = только для чтения. К базам данных из вторичной реплики разрешаются соединения только для чтения. Для всех баз данных в реплике разрешен доступ для чтения.<br /><br /> 2= все. К базам данных во вторичной реплике разрешаются все соединения на доступ только для чтения.<br /><br /> Дополнительные сведения см. в разделе [Активные вторичные реплики: доступные только для чтения вторичные реплики (группы доступности AlwaysOn)](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).|  
|**secondary_role_allow_connections_desc**|**nvarchar(60)**|Описание **secondary_role_allow_connections**, одно из:<br /><br /> Нет<br /><br /> READ_ONLY<br /><br /> ALL|  
|**create_date**|**datetime**|Дата создания реплики.<br /><br /> NULL = на данном экземпляре сервера реплика отсутствует.|  
|**modify_date**|**datetime**|Дата последнего изменения реплики.<br /><br /> NULL = на данном экземпляре сервера реплика отсутствует.|  
|**backup_priority**|**int**|Представляет определяемый пользователем приоритет выполнения резервного копирования на данной реплике по отношению к другим репликам в той же группе доступности. Значение представляет собой целое число в диапазоне от 0 до 100.<br /><br /> Дополнительные сведения см. в статье [Активные вторичные реплики, резервное копирование во вторичных репликах (группы доступности Always On)](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).|  
|**read_only_routing_url**|**nvarchar(256)**|Конечная точка подключения (URL-адрес) реплики доступности, доступной только для чтения. Дополнительные сведения см. в статье [Настройка маршрутизации только для чтения в группе доступности (SQL Server)](../../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md).|  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требует разрешения VIEW ANY DEFINITION на экземпляре сервера.  
  
## <a name="see-also"></a>См. также  
 [sys.availability_groups (Transact-SQL)](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)   
 [Обзор групп доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Группы доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Отслеживание групп доступности & #40; Transact-SQL & #41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Отслеживание групп доступности (Transact-SQL)](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  
