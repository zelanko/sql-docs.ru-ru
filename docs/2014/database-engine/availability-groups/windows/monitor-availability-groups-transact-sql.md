---
title: Отслеживание групп доступности (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- dynamic management views [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], listeners
- Availability Groups [SQL Server], databases
- catalog views [SQL Server], AlwaysOn Availability Groups
ms.assetid: 881a34de-8461-4811-8c62-322bf7226bed
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4b97d62e7dede1cbbe4229f824407946f2fe43ba
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62789823"
---
# <a name="monitor-availability-groups-transact-sql"></a>Отслеживание групп доступности (Transact-SQL)
  Для мониторинга групп доступности и реплик доступности, а также связанных баз данных с помощью [!INCLUDE[tsql](../../../includes/tsql-md.md)]в [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] предусмотрен набор представлений каталога, динамических административных представлений и свойств сервера. С помощью инструкций [!INCLUDE[tsql](../../../includes/tsql-md.md)] SELECT можно использовать представления для отслеживания групп доступности, их реплик и баз данных. Сведения, возвращаемые по данной группе доступности, зависят от наличия подключения к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на котором размещена первичная или вторичная реплика.  
  
> [!TIP]  
>  Многие из этих представлений можно объединять с помощью их столбцов ID, что позволяет возвращать сведения из нескольких представлений в одном запросе.  
  
 
  
##  <a name="Permissions"></a> Permissions  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]представлениям каталога требуется разрешение VIEW ANY DEFINITION на экземпляр сервера. [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]для динамических административных представлений требуется разрешение VIEW SERVER STATE на сервере.  
  
##  <a name="AoAgFeatureOnSI"></a>Наблюдение за функцией группы доступности AlwaysOn на экземпляре сервера  
 Для наблюдения за компонентом [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] на экземпляре сервера пользуйтесь следующей встроенной функцией.  
  
 Функция [SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql)  
 Возвращает сведения о свойствах сервера о том, включен ли [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , а также (если включен) был ли он запущен на экземпляре сервера.  
  
 **Имена столбцов:** IsHadrEnabled, HadrManagerStatus  
  
##  <a name="WSFC"></a>Наблюдение за группами доступности в кластере WSFC  
 Для мониторинга отказоустойчивой кластеризации Windows Server (WSFC), на котором размещается локальный экземпляр сервера с поддержкой [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], используются следующие представления:  
  
 [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql)  
 Если на узле отказоустойчивой кластеризации Windows Server (WSFC), где размещен экземпляр SQL Server с включенным [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , имеется кворум WSFC, **sys.dm_hadr_cluster** возвращает строку, которая предоставляет имя кластера и сведения о форуме. Если узел WSFC не набирает кворум, строки не возвращаются.  
  
 **Имена столбцов:** cluster_name, quorum_type, quorum_type_desc, quorum_state, quorum_state_desc  
  
 [sys.dm_hadr_cluster_members](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql)  
 Если на узле WSFC, где размещен локальный экземпляр WSFC Server с поддержкой AlwaysOn, имеется кворум WSFC, то возвращается по одной строке для каждого из элементов, составляющих кворум, вместе с состоянием каждого из них.  
  
 **Имена столбцов:** member_name, member_type, member_type_desc, member_state, member_state_desc, number_of_quorum_votes  
  
 [sys.dm_hadr_cluster_networks](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)  
 Возвращает по строке для каждого из элементов, участвующих в конфигурации подсети группы доступности. Это динамическое административное представление можно использовать для проверки виртуального сетевого IP-адреса, настроенного для каждой из реплик доступности.  
  
 **Имена столбцов:** member_name, network_subnet_ip, network_subnet_ipv4_mask, network_subnet_prefix_length, is_public, is_ipv4  
  
 **Первичный ключ:** member_name + network_subnet_IP + network_subnet_prefix_length  
  
 [sys.dm_hadr_instance_node_map](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-instance-node-map-transact-sql)  
 Для каждого экземпляра SQL Server, на котором размещена реплика доступности, присоединенная к своей группе доступности AlwaysOn, возвращается имя узла отказоустойчивого кластера Windows Server (WSFC), где размещен экземпляр сервера. Это динамическое административное представление может использоваться следующим образом.  
  
-   Динамическое административное представление может оказаться полезным для обнаружения группы доступности с несколькими репликами доступности, размещенными на одном узле WSFC, поскольку такая конфигурация, которая может возникнуть после отработки отказа FCI в том случае, если группа доступности сконфигурирована неверно, не поддерживается.  
  
-   Когда несколько экземпляров SQL Server размещаются на одном узле WSFC, DLL-библиотека ресурсов через это динамическое административное представление определяет экземпляр SQL Server, к которому следует подключаться.  
  
 **Имена столбцов:** ag_resource_id, instance_name, NODE_NAME  
  
 [sys.dm_hadr_name_id_map](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-name-id-map-transact-sql)  
 Показывает сопоставлению групп доступности AlwaysOn, что текущий экземпляр SQL Server присоединен к трем уникальным идентификаторам: идентификатору группы доступности, идентификатору ресурса WSFC и идентификатору группы WSFC. Цель такого сопоставления состоит в обработке сценария, в ходе которого ресурс/группа WSFC переименовывается.  
  
 **Имена столбцов:** ag_name, ag_id, ag_resource_id, ag_group_id  
  
> [!NOTE]  
>  См. также описание команд **sys.dm_hadr_availability_replica_cluster_nodes** и **sys.dm_hadr_availability_replica_cluster_states** в разделе [Мониторинг реплик доступности](#AvReplicas) и описание команд **sys.availability_databases_cluster** и **sys.dm_hadr_database_replica_cluster_states** в разделе [Мониторинг баз данных доступности](#AvDbs) далее в этой статье.  
  
 Сведения о кластерах WSFC и [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]см. в разделе [отказоустойчивая кластеризация Windows Server &#40;WSFC&#41; с SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) и [отказоустойчивой кластеризацией и группы доступности AlwaysOn &#40;](failover-clustering-and-always-on-availability-groups-sql-server.md)SQL Server&#41;.  
  
##  <a name="AvGroups"></a>Мониторинг групп доступности  
 Для мониторинга групп доступности, для которых на экземпляре сервера размещена реплика доступности, используются следующие представления.  
  
 [sys.availability_groups](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)  
 Возвращает строку для каждой группы доступности, для которых в локальном экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] размещена реплика доступности. Каждая строка содержит кэшированную копию метаданных группы доступности.  
  
 **Имена столбцов:** group_id, имя, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc  
  
 [sys.availability_groups_cluster](/sql/relational-databases/system-catalog-views/sys-availability-groups-cluster-transact-sql)  
 Возвращает строку для каждой группы доступности в кластере WSFC. Каждая строка содержит метаданные группы доступности из отказоустойчивой кластеризации Windows Server (WSFC).  
  
 **Имена столбцов:** group_id, имя, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc  
  
 [sys.dm_hadr_availability_group_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql)  
 Возвращает по строке для каждой из групп доступности, у которых имеется реплика доступности на локальном экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Каждая строка отображает состояния работоспособности определенной группы доступности.  
  
 **Имена столбцов:** group_id, primary_replica, primary_recovery_health, primary_recovery_health_desc, secondary_recovery_health, secondary_recovery_health_desc, synchronization_health, synchronization_health_desc  
  
##  <a name="AvReplicas"></a>Мониторинг реплик доступности  
 Для мониторинга групп доступности используются следующие представления и системная функция.  
  
 [sys.availability_replicas](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)  
 Возвращает строку для каждой реплики доступности, для которой в локальном экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] размещена реплика доступности.  
  
 **Имена столбцов:** replica_id, group_id, replica_metadata_id, replica_server_name, owner_sid, endpoint_url, availability_mode, availability_mode_desc, FAILOVER_MODE, failover_mode_desc, SESSION_TIMEOUT, primary_role_allow_connections, primary_role_allow_connections_desc, secondary_role_allow_connections, secondary_role_allow_connections_desc, create_date, modify_date, backup_priority, READ_ONLY_ROUTING_URL  
  
 [sys.availability_read_only_routing_lists](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
 Возвращает строку для списка маршрутизации только для чтения для каждой реплики доступности в группе доступности AlwaysOn в отказоустойчивом кластере WSFC.  
  
 **Имена столбцов:** replica_id, routing_priority, read_only_replica_id  
  
 [sys.dm_hadr_availability_replica_cluster_nodes](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-nodes-transact-sql)  
 Возвращает по строке для каждой из реплик доступности (независимо от состояния соединения) в группах доступности AlwaysOn в отказоустойчивой кластеризации Windows Server (WSFC).  
  
 **Имена столбцов:** group_name, replica_server_name, NODE_NAME  
  
 [sys.dm_hadr_availability_replica_cluster_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
 Возвращает по строке для каждой из реплик (вне зависимости от состояния соединения) во всех группах доступности AlwaysOn (вне зависимости от расположения реплики) в отказоустойчивой кластеризации Windows Server (WSFC).  
  
 **Имена столбцов:** replica_id, replica_server_name, group_id, join_state, join_state_desc  
  
 [sys.dm_hadr_availability_replica_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)  
 Возвращает строку с состоянием каждой локальной реплики доступности и для каждой удаленной реплики доступности, входящей в ту же группу доступности.  
  
 **Имена столбцов:** replica_id, group_id, is_local, role, role_desc, operational_state, operational_state_desc, connected_state, connected_state_desc, recovery_health, recovery_health_desc, synchronization_health, synchronization_health_desc, last_connect_error_number, last_connect_error_description и last_connect_error_timestamp  
  
 [sys.fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
 Определяет, является ли текущая реплика предпочитаемой резервной репликой отработки.  
  
> [!NOTE]  
>  Сведения о счетчиках производительности для реплик доступности (объект производительности **SQLServer:Availability Replica**  ) см. в статье [Счетчики производительности для реплик доступности](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).  
  
##  <a name="AvDbs"></a>Мониторинг баз данных доступности  
 Для мониторинга баз данных доступности используйте следующие представления.  
  
 [sys.availability_databases_cluster](/sql/relational-databases/system-catalog-views/sys-availability-databases-cluster-transact-sql)  
 Содержит по строке для каждой базы данных на экземпляре SQL Server в составе групп доступности AlwaysOn в кластере, независимо от того, присоединена ли уже локальная копия базы данных к группе доступности.  
  
> [!NOTE]  
>  При добавлении базы данных в группу доступности база данных-источник автоматически присоединяется к группе. Базы данных-получатели необходимо подготовить на каждой из вторичных реплик до того, как их можно будет присоединить к группе доступности.  
  
 **Имена столбцов:** group_id, group_database_id, database_name  
  
 [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
 Содержит одну строку для каждой базы данных в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Если база данных принадлежит к реплике доступности, то в строке для этой базы данных отображается идентификатор GUID реплики и уникальный идентификатор базы данных внутри группы доступности.  
  
 имена столбцов: replica_id, group_database_id ** [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] **  
  
 [sys.dm_hadr_auto_page_repair](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-auto-page-repair-transact-sql)  
 Возвращает строку для каждой попытки автоматического восстановления страниц во всех базах данных доступности в реплике доступности, размещенной в группе доступности на экземпляре сервера. Это представление содержит строки, связанные с последними попытками автоматического восстановления страниц в определенной базе данных-источнике или получателе, количество которых ограничено числом в 100 строк на каждую базу данных. По достижении максимального значения строка для следующей попытки автоматического восстановления страниц заменяет одну из существующих записей.  
  
 **Имена столбцов:** database_id, file_id, page_id, error_type, page_status, modification_time  
  
 [sys.dm_hadr_database_replica_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql)  
 Возвращает по строке для каждой из баз данных, участвующих в любой группе доступности, реплика доступности которой размещена на локальном экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 **Имена столбцов:** database_id, group_id, replica_id, group_database_id, is_local, synchronization_state, synchronization_state_desc, is_commit_participant, synchronization_health, synchronization_health_desc, database_state, database_state_desc, is_suspended, suspend_reason, suspend_reason_desc recovery_lsn, truncation_lsn, last_sent_lsn, last_sent_time, last_received_lsn, last_received_time, log_send_queue_size, log_send_rate, redo_queue_size, redo_rate, filestream_send_rate, end_of_log_lsn, last_commit_lsn, last_commit_time, low_water_mark_for_ghosts  
  
 [sys.dm_hadr_database_replica_cluster_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql)  
 Возвращает строку с информацией, помогающей составить представление о работоспособности баз данных доступности каждой из групп доступности в отказоустойчивой кластеризации Windows Server (WSFC). Динамическое административное представление удобно использовать при планировании или при отработке отказа либо при поиске вторичной реплики в группе доступности, которая не дает усекать журнал данной базы данных-источника.  
  
 **Имена столбцов:** replica_id, group_database_id, database_name, is_failover_ready, is_pending_secondary_suspend, is_database_joined, recovery_lsn, truncation_lsn  
  
> [!NOTE]  
>  Расположение первичной реплики — авторитетный источник для группы доступности.  
  
> [!NOTE]  
>  Сведения о счетчиках производительности [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] для баз данных доступности (объект производительности **SQLServer:Database Replica** ) см. в разделе [SQL Server, реплика базы данных](../../../relational-databases/performance-monitor/sql-server-database-replica.md). Кроме того, чтобы отслеживать активность журнала транзакций в базах данных доступности, используйте следующие счетчики объекта производительности **SQLServer: databases** : **время записи журнала на диск (МС)**, **сбросов журнала/с**, **промахов кэша пула журнала/с**, **операций чтения с диска пула журнала/с**и **запросов пула журналов/с**. Дополнительные сведения см. в разделе [SQL Server, Database Object](../../../relational-databases/performance-monitor/sql-server-databases-object.md).  
  
##  <a name="AGlisteners"></a>Отслеживание прослушивателей групп доступности  
 Для мониторинга прослушивателей группы доступности в подсети кластера WSFC используйте следующие представления:  
  
 [sys.availability_group_listener_ip_addresses](/sql/relational-databases/system-catalog-views/sys-availability-group-listener-ip-addresses-transact-sql)  
 Возвращает строку для каждого совместимого виртуального IP-адреса, который в настоящее время включен для прослушивателя группы доступности.  
  
 **Имена столбцов:** listener_id, ip_address, ip_subnet_mask, is_dhcp, network_subnet_ip, network_subnet_prefix_length, network_subnet_ipv4_mask, state, state_desc  
  
 [sys.availability_group_listeners](/sql/relational-databases/system-catalog-views/sys-availability-group-listeners-transact-sql)  
 Для любой выбранной группы доступности возвращает либо ноль строк, указывая, что с группой доступности не связано ни одного сетевого имени, либо отдельную строку для каждой конфигурации прослушивателя группы доступности в кластере WSFC.  
  
 **Имена столбцов:** group_id, listener_id, dns_name, порт, is_conformant, ip_configuration_string_from_cluster  
  
 [sys.dm_tcp_listener_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-tcp-listener-states-transact-sql)  
 Возвращает строку, содержащую сведения о динамическом состоянии для каждого прослушивателя TCP.  
  
 **Имена столбцов:** listener_id, ip_address, is_ipv4, порт, тип, type_desc, состояние, state_desc, start_time  
  
 **Первичный ключ:** listener_id  
  
 Сведения о прослушивателях групп доступности см. в разделе [Прослушиватели группы доступности, подключения клиентов и отработка отказа приложений (SQL Server)](../../listeners-client-connectivity-application-failover.md).  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Задачи наблюдения групп доступности AlwaysOn**  
  
-   [Используйте сведения обозревателя объектов для мониторинга групп доступности &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md)  
  
-   [Просмотр свойств группы доступности (SQL Server)](view-availability-group-properties-sql-server.md)  
  
-   [Просмотр свойств реплики доступности &#40;SQL Server&#41;](view-availability-replica-properties-sql-server.md)  
  
-   [Просмотр свойств прослушивателя группы доступности (SQL Server)](view-availability-group-listener-properties-sql-server.md)  
  
 **Справочник по наблюдениям за группами доступности AlwaysOn (Transact-SQL)**  
  
-   [SERVERPROPERTY (Transact-SQL)](/sql/t-sql/functions/serverproperty-transact-sql)  
  
-   [sys. availability_group_listener_ip_addresses &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-group-listener-ip-addresses-transact-sql)  
  
-   [sys. availability_group_listeners &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-group-listeners-transact-sql)  
  
-   [sys. availability_databases_cluster &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-databases-cluster-transact-sql)  
  
-   [sys. availability_groups &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)  
  
-   [sys. availability_read_only_routing_lists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
  
-   [sys. availability_replicas &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)  
  
-   [sys. dm_hadr_availability_replica_cluster_nodes &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-nodes-transact-sql)  
  
-   [sys. dm_hadr_availability_replica_cluster_states &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
  
-   [sys. database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
-   [sys. dm_hadr_auto_page_repair &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-auto-page-repair-transact-sql)  
  
-   [sys. dm_hadr_availability_group_states &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql)  
  
-   [sys. dm_hadr_availability_replica_cluster_states &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
  
-   [sys. dm_hadr_availability_replica_states &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)  
  
-   [sys. dm_hadr_database_replica_states &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql)  
  
-   [sys. dm_hadr_database_replica_cluster_states &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql)  
  
-   [sys. dm_hadr_cluster &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql)  
  
-   [sys. dm_hadr_cluster_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql)  
  
-   [sys. dm_hadr_cluster_networks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)  
  
-   [sys. dm_hadr_database_replica_cluster_states &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql)  
  
-   [sys. dm_hadr_database_replica_states &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql)  
  
-   [sys. dm_hadr_instance_node_map &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-instance-node-map-transact-sql)  
  
-   [sys. dm_hadr_name_id_map &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-name-id-map-transact-sql)  
  
-   [sys. dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
-   [sys. dm_tcp_listener_states &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-tcp-listener-states-transact-sql)  
  
-   [sys. fn_hadr_backup_is_preferred_replica &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
  
 **Счетчики производительности AlwaysOn:**  
  
-   [SQL Server, реплика доступности](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)  
  
-   [SQL Server, реплика базы данных](../../../relational-databases/performance-monitor/sql-server-database-replica.md)  
  
-   [SQL Server, объект Databases](../../../relational-databases/performance-monitor/sql-server-databases-object.md)  
  
 **Управление на основе политик для групп доступности AlwaysOn**  
  
-   [Используйте политики AlwaysOn для просмотра работоспособности группы доступности &#40;SQL Server&#41;](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)  
  
-   [Использование панели мониторинга AlwaysOn &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
## <a name="see-also"></a>См. также:  
 [Группы доступности AlwaysOn (SQL Server)](always-on-availability-groups-sql-server.md)   
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Мониторинг групп доступности &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)  
  
  
