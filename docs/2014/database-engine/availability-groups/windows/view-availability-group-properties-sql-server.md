---
title: Просмотр свойств группы доступности (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server]
ms.assetid: 61243c87-bd62-4510-863f-2a8f347caf1f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 102b3defa150707412012d506e0e9e542d80b9a0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62813257"
---
# <a name="view-availability-group-properties-sql-server"></a>Просмотр свойств группы доступности (SQL Server)
  В этом разделе описывается просмотр свойств группы доступности для группы доступности AlwaysOn с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  

  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Просмотр и изменение свойств группы доступности**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена первичная реплика, и разверните дерево сервера.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности** .  
  
3.  Щелкните правой кнопкой мыши группу доступности, свойства которой нужно просмотреть, и выберите команду **Свойства** .  
  
4.  В диалоговом окне **Свойства группы доступности** просмотреть и в некоторых случаях изменить свойства выбранной группы доступности можно на страницах **Общие** и **Настройки резервного копирования** . Дополнительные сведения см. в разделе [свойства группы доступности и создание группы доступности &#40;страница "Общие"&#41; ](availability-group-properties-new-availability-group-general-page.md) и [свойства группы доступности: Создание группы доступности &#40;страница настроек резервного копирования&#41;](availability-group-properties-new-availability-group-backup-preferences-page.md).  
  
     На странице **Разрешения** можно просмотреть текущие имена входа, роли и явные разрешения, связанные с группой доступности. Дополнительные сведения см. в статье [Permissions or Securables Page](../../../relational-databases/security/permissions-or-securables-page.md).  
  

  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Просмотр свойств и состояния группы доступности**  
  
 Чтобы запросить свойства и состояния групп доступности, для которых на экземпляре сервера размещена реплика доступности, используйте следующие представления.  
  
 [sys.availability_groups](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)  
 Возвращает строку для каждой группы доступности, для которых в локальном экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] размещена реплика доступности. Каждая строка содержит кэшированную копию метаданных группы доступности.  
  
 **Имена столбцов:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc  
  
 [sys.availability_groups_cluster](/sql/relational-databases/system-catalog-views/sys-availability-groups-cluster-transact-sql)  
 Возвращает строку для каждой группы доступности в кластере WSFC. Каждая строка содержит метаданные группы доступности из отказоустойчивой кластеризации Windows Server (WSFC).  
  
 **Имена столбцов:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc  
  
 [sys.dm_hadr_availability_group_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql)  
 Возвращает по строке для каждой из групп доступности, у которых имеется реплика доступности на локальном экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Каждая строка отображает состояния работоспособности определенной группы доступности.  
  
 **Имена столбцов:** group_id, primary_replica, primary_recovery_health, primary_recovery_health_desc, secondary_recovery_health, secondary_recovery_health_desc, synchronization_health, synchronization_health_desc  
  

  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Просмотр сведений о группах доступности**  
  
-   [Просмотр свойств реплики доступности (SQL Server)](view-availability-replica-properties-sql-server.md)  
  
-   [Просмотр свойств прослушивателя группы доступности (SQL Server)](view-availability-group-listener-properties-sql-server.md)  
  
-   [Политики AlwaysOn на случай проблем в работе с группами доступности AlwaysOn &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md)
  
-   [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [Отслеживание групп доступности (Transact-SQL)](monitor-availability-groups-transact-sql.md)  
  
 **Настройка существующей группы доступности**  
  
-   [Добавление вторичной реплики к группе доступности (SQL Server)](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Удаление вторичной реплики из группы доступности (SQL Server)](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [Добавление базы данных в группу доступности (SQL Server)](availability-group-add-a-database.md)  
  
-   [Удаление базы данных-получателя из группы доступности (SQL Server)](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [Создание или настройка прослушивателя группы доступности (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Удаление прослушивателя группы доступности (SQL Server)](remove-an-availability-group-listener-sql-server.md)  
  
-   [Удаление базы данных-источника из группы доступности (SQL Server)](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [Удаление группы доступности (SQL Server)](remove-an-availability-group-sql-server.md)  
  
 **Переход на другой ресурс группы доступности вручную**  
  
-   [Выполнение запланированного перехода на другой ресурс вручную для группы доступности (SQL Server)](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [Выполнение принудительного перехода на другой ресурс вручную для группы доступности (SQL Server)](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  

  
## <a name="see-also"></a>См. также  
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41; ](overview-of-always-on-availability-groups-sql-server.md) [отслеживания групп доступности &#40;Transact-SQL&#41; ](monitor-availability-groups-transact-sql.md) [политики AlwaysOn на случай проблем в работе с AlwaysOn Группы доступности &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md) 
  
  
