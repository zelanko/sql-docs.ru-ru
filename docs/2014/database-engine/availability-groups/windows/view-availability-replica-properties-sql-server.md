---
title: Просмотр свойств реплики доступности (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ', policies'
ms.assetid: 14fed3c4-8ecc-4e1c-931d-a7ec1e9f9e90
caps.latest.revision: 10
author: rothja
ms.author: jroth
manager: jhubbard
ms.openlocfilehash: 62c6b2f80730ecb1d82cd0e35f8904651ac041d9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095276"
---
# <a name="view-availability-replica-properties-sql-server"></a>Просмотр свойств реплики доступности (SQL Server)
  В этом разделе описывается просмотр свойств реплики доступности для группы доступности AlwaysOn с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Просмотр и изменение свойств реплики доступности**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена первичная реплика, и разверните дерево сервера.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности** .  
  
3.  Разверните группу доступности, которой принадлежит реплика доступности, а затем разверните узел **Реплики доступности** .  
  
4.  Щелкните правой кнопкой мыши реплику доступности, свойства которой нужно просмотреть, и выберите команду **Свойства** .  
  
5.  В диалоговом окне **Свойства реплики доступности** на странице **Общие** просмотрите свойства текущей реплики. Если установлено соединение с первичной репликой, можно изменить следующие свойства: режим доступности, режим перехода на другой ресурс, доступ соединения для первичной роли, доступ чтения для вторичной роли (доступная для чтения вторичная роль) и значение времени ожидания сеанса. Дополнительные сведения см. в разделе [свойства реплики доступности &#40;страница «Общие»&#41;](availability-replica-properties-general-page.md).  
  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Просмотр свойств и состояний реплик доступности**  
  
 Для просмотра свойств и состояний реплик доступности используются следующие представления и системная функция.  
  
 [sys.availability_replicas](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)  
 Возвращает строку для каждой реплики доступности, для которой в локальном экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] размещена реплика доступности.  
  
 **Имена столбцов:** replica_id, group_id, replica_metadata_id, replica_server_name, owner_sid, endpoint_url, availability_mode, availability_mode_desc, failover_mode, failover_mode_desc, session_timeout, primary_role_allow_connections, primary_role_allow_connections_desc, secondary_role_allow_connections, secondary_role_allow_connections_desc, create_date, modify_date, backup_priority, read_only_routing_url  
  
 [sys.availability_read_only_routing_lists](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
 Возвращает строку для списка маршрутизации только для чтения для каждой реплики доступности в группе доступности AlwaysOn в отказоустойчивом кластере WSFC.  
  
 **Имена столбцов:** replica_id, routing_priority, read_only_replica_id  
  
 [sys.dm_hadr_availability_replica_cluster_nodes](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-nodes-transact-sql)  
 Возвращает по строке для каждой из реплик доступности (независимо от состояния соединения) в группах доступности AlwaysOn в отказоустойчивой кластеризации Windows Server (WSFC).  
  
 **Имена столбцов:** group_name, replica_server_name, node_name  
  
 [sys.dm_hadr_availability_replica_cluster_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
 Возвращает по строке для каждой из реплик (вне зависимости от состояния соединения) во всех группах доступности AlwaysOn (вне зависимости от расположения реплики) в отказоустойчивой кластеризации Windows Server (WSFC).  
  
 **Имена столбцов:** replica_id, replica_server_name, group_id, join_state, join_state_desc  
  
 [sys.dm_hadr_availability_replica_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)  
 Возвращает строку с состоянием каждой локальной реплики доступности и для каждой удаленной реплики доступности, входящей в ту же группу доступности.  
  
 **Имена столбцов:** replica_id, group_id, is_local, role, role_desc, operational_state, operational_state_desc, connected_state, connected_state_desc, recovery_health, recovery_health_desc, synchronization_health, synchronization_health_desc, last_connect_error_number, last_connect_error_description и last_connect_error_timestamp  
  
 [sys.fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
 Определяет, является ли текущая реплика предпочитаемой резервной репликой отработки. Возвращаемое значение равно 1, если база данных в текущем экземпляре сервера является предпочитаемой репликой. В противном случае возвращается значение 0.  
  
> [!NOTE]  
>  Сведения о счетчиках производительности для реплик доступности (объект производительности **SQLServer:Availability Replica**  ) см. в статье [Счетчики производительности для реплик доступности](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).  
  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Просмотр сведений о группах доступности**  
  
-   [Просмотр свойств группы доступности (SQL Server)](view-availability-group-properties-sql-server.md)  
  
-   [Просмотр свойств прослушивателя группы доступности (SQL Server)](view-availability-group-listener-properties-sql-server.md)  
  
-   [Политики AlwaysOn на случай проблем в работе с группами доступности AlwaysOn &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md)
  
-   [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [Отслеживание групп доступности (Transact-SQL)](monitor-availability-groups-transact-sql.md)  
  
 **Управление репликами доступности**  
  
-   [Добавление вторичной реплики к группе доступности (SQL Server)](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Присоединение вторичной реплики к группе доступности (SQL Server)](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Настройка доступа только для чтения в реплике доступности (SQL Server)](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [Смена режима доступности для реплики доступности (SQL Server)](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [Смена режима отработки отказа для реплики доступности (SQL Server)](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [Изменение периода ожидания сеанса для реплики доступности (SQL Server)](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
-   [Удаление вторичной реплики из группы доступности (SQL Server)](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
 **Управление базой данных доступности**  
  
-   [Добавление базы данных в группу доступности (SQL Server)](availability-group-add-a-database.md)  
  
-   [Присоединение базы данных-получателя к группе доступности (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Приостановка базы данных доступности (SQL Server)](suspend-an-availability-database-sql-server.md)  
  
-   [Возобновление базы данных доступности (SQL Server)](resume-an-availability-database-sql-server.md)  
  
-   [Удаление базы данных-получателя из группы доступности (SQL Server)](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [Удаление базы данных-источника из группы доступности (SQL Server)](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
  
## <a name="see-also"></a>См. также  
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Отслеживание групп доступности (Transact-SQL)](monitor-availability-groups-transact-sql.md)   
 [Политики AlwaysOn на случай проблем в работе с группами доступности AlwaysOn &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md)   
 [Администрирование группы доступности (SQL Server)](administration-of-an-availability-group-sql-server.md)  
  
  
