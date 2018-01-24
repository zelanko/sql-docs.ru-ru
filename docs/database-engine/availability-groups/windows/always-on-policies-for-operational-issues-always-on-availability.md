---
title: "Политики AlwaysOn на случай проблем в работе с группами доступности AlwaysOn | Документы Майкрософт"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: availability-groups
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], troubleshooting
- Availability Groups [SQL Server], policies
ms.assetid: afa5289c-641a-4c03-8749-44862384ec5f
caps.latest.revision: "19"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b92e1a679cfa738620e8e46195b2df14e8ee03ad
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="always-on-policies-for-operational-issues---always-on-availability"></a>Политики AlwaysOn на случай проблем в работе с группами доступности AlwaysOn
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Модель правил определения исправности [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] вычисляет набор стандартных (PBM) политик управления на основе политик. Их можно использовать для просмотра исправности группы доступности и реплики доступности и базы данных в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 **В этом разделе.**  
  
-   [Термины и определения](#TermsAndDefinitions)  
  
-   [Стандартные политики и проблемы](#Always OnPBM)  
  
-   [Панель мониторинга AlwaysOn](#Dashboard)  
  
-   [Расширение модели исправности AlwaysOn](#ExtendHealthModel)  
  
-   [Связанные задачи](#RelatedTasks)  
  
-   [См. также](#RelatedContent)  
  
##  <a name="TermsAndDefinitions"></a> Термины и определения  
 Стандартные политики AlwaysOn  
 Набор встроенных политик, который позволяет администратору базы данных проверить группу доступности, а также соответствие ее реплик доступности и баз данных состояниям, определенным политиками AlwaysOn.  
  
 [Группы доступности AlwaysOn](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
 Решение высокой доступности и аварийного восстановления, являющееся альтернативой зеркальному отображению баз данных на уровне предприятия.  
  
 группа доступности  
 Контейнер для дискретного набора пользовательских баз данных, известного как *базы данных доступности*, которые совместно отрабатывают отказ.  
  
 реплика доступности  
 Создание экземпляра группы доступности, которая размещена на определенном экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и поддерживает локальную копию каждой базы данных доступности, входящей в группу доступности. Существует два типа реплик доступности: одна *первичная* и от одной до четырех *вторичных реплик*. Экземпляры сервера, на которых размещаются реплики доступности для данной группы доступности, должны размещаться на разных узлах одной кластеризации WSFC.  
  
 база данных доступности  
 База данных, принадлежащая к группе доступности. Для каждой базы данных доступности группа доступности поддерживает одну копию для записи и чтения ( *база данных-источник*) и от одной до четырех копий только для чтения (*базы данных-получатели*).  
  
 Панель мониторинга AlwaysOn  
 Панель мониторинга [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] дает обзорное представление исправности группы доступности. Дополнительные сведения см. в подразделе [Панель мониторинга AlwaysOn](#Dashboard)далее в этом разделе.  
  
##  <a name="Always OnPBM"></a> Стандартные политики и проблемы  
 В следующей таблице приведены итоговые сведения о стандартных политиках.  
  
|Имя политики|Проблема|Категория**\***|Аспект|  
|-----------------|-----------|--------------------|-----------|  
|Состояние кластера WSFC|[WSFC cluster service is offline](../../../database-engine/availability-groups/windows/wsfc-cluster-service-is-offline.md).|Критическая|Экземпляр SQL Server|  
|Режим «в сети» группы доступности|[Availability group is offline](../../../database-engine/availability-groups/windows/availability-group-is-offline.md).|Критическая|группа доступности|  
|Готовность группы доступности к автоматическому переходу на другой ресурс при сбое|[Availability group is not ready for automatic failover](../../../database-engine/availability-groups/windows/availability-group-is-not-ready-for-automatic-failover.md).|Критическая|группа доступности|  
|Состояние синхронизации данных реплик доступности|[Some availability replicas are not synchronizing data](../../../database-engine/availability-groups/windows/some-availability-replicas-are-not-synchronizing-data.md).|Предупреждение|группа доступности|  
|Состояние синхронизации данных синхронных реплик|[Some synchronous replicas are not synchronized](../../../database-engine/availability-groups/windows/some-synchronous-replicas-are-not-synchronized.md).|Предупреждение|группа доступности|  
|Состояние роли реплик доступности|[Some availability replicas do not have a healthy role](../../../database-engine/availability-groups/windows/some-availability-replicas-do-not-have-a-healthy-role.md).|Предупреждение|группа доступности|  
|Состояние соединения с репликами доступности|[Some availability replicas are disconnected](../../../database-engine/availability-groups/windows/some-availability-replicas-are-disconnected.md).|Предупреждение|группа доступности|  
|Состояние роли реплики доступности|[Availability replica does not have a healthy role](../../../database-engine/availability-groups/windows/availability-replica-does-not-have-a-healthy-role.md).|Критическая|реплика доступности|  
|Состояние соединения с репликами доступности|[Availability replica is disconnected](../../../database-engine/availability-groups/windows/availability-replica-is-disconnected.md).|Критическая|Реплика доступности|  
|Состояние присоединения реплики доступности|[Реплика доступности не присоединена](../../../database-engine/availability-groups/windows/availability-replica-is-not-joined.md).|Предупреждение|Реплика доступности|  
|Состояние синхронизации данных реплики доступности|[Data synchronization state of some availability database is not healthy](../../../database-engine/availability-groups/windows/data-synchronization-state-of-some-availability-database-is-not-healthy.md).|Предупреждение|Реплика доступности|  
|Состояние приостановки базы данных доступности|[Availability database is suspended](../../../database-engine/availability-groups/windows/availability-database-is-suspended.md).|Предупреждение|База данных доступности|  
|Состояние присоединения базы данных доступности|[Secondary database is not joined](../../../database-engine/availability-groups/windows/secondary-database-is-not-joined.md).|Предупреждение|База данных доступности|  
|Состояние синхронизации базы данных доступности|[Data synchronization state of availability database is not healthy](../../../database-engine/availability-groups/windows/data-synchronization-state-of-availability-database-is-not-healthy.md).|Предупреждение|База данных доступности|  
  
> [!IMPORTANT]  
>  **\*** При работе с политиками AlwaysOn имена категорий используются в качестве идентификаторов. При изменении имени категории AlwaysOn ее функция оценки работоспособности будет нарушена. Поэтому не следует изменять имена категорий AlwaysOn.  
  
##  <a name="Dashboard"></a> Панель мониторинга AlwaysOn  
 Панель мониторинга AlwaysOn дает обзорное представление исправности группы доступности. На панели мониторинга AlwaysOn имеются следующие функции:  
  
-   Позволяет легко увидеть сведения о данной группе доступности, а также ее реплик доступности и баз данных.  
  
-   Показывает визуальные признаки ключевых состояний, чтобы помочь администраторам баз данных принимать быстрые рабочие решения.  
  
-   Предоставляет точки запуска для сценариев устранения неполадок.  
  
-   Для данной рабочей проблемы выдает в диалоговом окне **Результат оценки политики** сведения о нарушениях определенной политики исправности AlwaysOn и ссылки на справку для исправления.  
  
-   Предоставляет средство просмотра расширенных событий исправности с целью показа предшествующих событий для специфических проблем AlwaysOn.  
  
-   Если автоматическое переключение группы доступности может помочь устранению, предоставляет точку запуска для ссылок[мастера перехода на другой ресурс для группы доступности](../../../database-engine/availability-groups/windows/use-the-fail-over-availability-group-wizard-sql-server-management-studio.md). Этот мастер помогает администратору базы данных выполнить переход на другой ресурс вручную.  
  
##  <a name="ExtendHealthModel"></a> Расширение модели исправности AlwaysOn  
 Расширение модели исправности [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] — это просто создание собственных пользовательских политик и их размещение в категориях по типам наблюдаемых объектов.  После изменения некоторых параметров панель мониторинга AlwaysOn автоматически вычисляет собственные, определяемые пользователем политики, а также стандартные политики AlwaysOn.  
  
 Определяемая пользователем политика может использовать доступные аспекты управления на основе политик, включая те из них, которые применяются в стандартных политиках AlwaysOn (см. подраздел [Стандартные политики и проблемы](#Always OnPBM)выше в этом разделе). Аспект сервера содержит следующие свойства для мониторинга работоспособности [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] : (**IsHadrEnabled** и **HadrManagerStatus**). Аспект сервера содержит также следующие свойства политики для мониторинга конфигурации кластера WSFC: **ClusterQuorumType**и **ClusterQuorumState**.  
  
 Дополнительные сведения см. в записи [Модель исправности AlwaysOn, часть 2. Расширение модели исправности](http://blogs.msdn.com/b/sqlAlways On/archive/2012/02/13/extending-the-Always On-health-model.aspx) (в блоге SQL Server AlwaysOn Team; на английском языке).  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Использование политик AlwaysOn для просмотра состояния группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)  
  
-   [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [Аварийное восстановление WSFC через принудительный кворум (SQL Server)](../../../sql-server/failover-clusters/windows/wsfc-disaster-recovery-through-forced-quorum-sql-server.md)  
  
-   [Принудительный запуск кластера WSFC без кворума](../../../sql-server/failover-clusters/windows/force-a-wsfc-cluster-to-start-without-a-quorum.md)  
  
-   [Выполнение принудительного перехода на другой ресурс вручную для группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [Устранение неполадок с операцией добавления файла, давшей сбой (группы доступности AlwaysOn)](../../../database-engine/availability-groups/windows/troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="RelatedContent"></a> См. также  
  
-   [Модель исправности AlwaysOn, часть 1. Архитектура модели исправности](http://blogs.msdn.com/b/sqlAlways On/archive/2012/02/13/extending-the-Always On-health-model.aspx)  
  
-   [Модель исправности AlwaysOn, часть 2. Расширение модели исправности](http://blogs.msdn.com/b/sqlAlways On/archive/2012/02/13/extending-the-Always On-health-model.aspx)  
  
-   [Руководство по решениям режима AlwaysOn в Microsoft SQL Server для обеспечения высокой доступности и аварийного восстановления](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
## <a name="see-also"></a>См. также:  
 [Группы доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Администрирование группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/administration-of-an-availability-group-sql-server.md)   
 [Отслеживание групп доступности (SQL Server)](../../../database-engine/availability-groups/windows/monitoring-of-availability-groups-sql-server.md)  
  
  
