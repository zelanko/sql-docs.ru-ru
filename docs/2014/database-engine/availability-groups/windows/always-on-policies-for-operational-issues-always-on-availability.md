---
title: Политики Always On для проблем в работе с группами доступности Always On (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], troubleshooting
- Availability Groups [SQL Server], policies
ms.assetid: afa5289c-641a-4c03-8749-44862384ec5f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 815f549cf9ab6dd7fe748c08ae7f32683c9d8551
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62815759"
---
# <a name="always-on-policies-for-operational-issues-with-always-on-availability-groups-sql-server"></a>Политики AlwaysOn на случай проблем в работе с группами доступности AlwaysOn (SQL Server)
  Модель правил определения исправности [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] вычисляет набор стандартных (PBM) политик управления на основе политик. Их можно использовать для просмотра исправности группы доступности и реплики доступности и базы данных в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 
  
##  <a name="TermsAndDefinitions"></a>Термины и определения  
 Стандартные политики AlwaysOn  
 Набор встроенных политик, который позволяет администратору базы данных проверить группу доступности, а также соответствие ее реплик доступности и баз данных состояниям, определенным политиками AlwaysOn.  
  
 [Группы доступности AlwaysOn](always-on-availability-groups-sql-server.md) Решение для обеспечения высокой доступности и аварийного восстановления, которое обеспечивает альтернативу зеркальному отображению базы данных на уровне предприятия.  
  
 группа доступности  
 Контейнер для дискретного набора пользовательских баз данных, известного как *базы данных доступности*, которые совместно отрабатывают отказ.  
  
 реплика доступности  
 Создание экземпляра группы доступности, которая размещена на определенном экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и поддерживает локальную копию каждой базы данных доступности, входящей в группу доступности. Существует два типа реплик доступности: одна *первичная* и от одной до четырех *вторичных реплик*. Экземпляры сервера, на которых размещаются реплики доступности для данной группы доступности, должны размещаться на разных узлах одной кластеризации WSFC.  
  
 база данных доступности  
 База данных, принадлежащая к группе доступности. Для каждой базы данных доступности группа доступности поддерживает одну копию для записи и чтения (*база данных-источник*) и от одной до четырех копий только для чтения (*базы данных-получатели*).  
  
 Панель мониторинга AlwaysOn  
 Панель мониторинга [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] дает обзорное представление исправности группы доступности. Дополнительные сведения см. в подразделе [Панель мониторинга AlwaysOn](#Dashboard)далее в этом разделе.  
  
##  <a name="AlwaysOnPBM"></a>Стандартные политики и проблемы  
 В следующей таблице приведены итоговые сведения о стандартных политиках.  
  
|Имя политики|Проблема|Категори**<sup>*</sup>**|Аспект|  
|-----------------|-----------|------------------------------|-----------|  
|Состояние кластера WSFC|[Служба кластеров WSFC находится в автономном режиме](wsfc-cluster-service-is-offline.md).|Critical|Экземпляр SQL Server|  
|Режим «в сети» группы доступности|[Группа доступности находится в автономном режиме](availability-group-is-offline.md).|Critical|Группа доступности|  
|Готовность группы доступности к автоматическому переходу на другой ресурс при сбое|[Группа доступности не готова к автоматическому переходу на другой ресурс](availability-group-is-not-ready-for-automatic-failover.md).|Critical|Группа доступности|  
|Состояние синхронизации данных реплик доступности|[Некоторые реплики доступности не синхронизируют данные](some-availability-replicas-are-not-synchronizing-data.md).|Предупреждение|Группа доступности|  
|Состояние синхронизации данных синхронных реплик|[Некоторые синхронные реплики не синхронизированы](some-synchronous-replicas-are-not-synchronized.md).|Предупреждение|Группа доступности|  
|Состояние роли реплик доступности|[Некоторые реплики доступности не имеют работоспособной роли](some-availability-replicas-do-not-have-a-healthy-role.md).|Предупреждение|Группа доступности|  
|Состояние соединения с репликами доступности|[Некоторые реплики доступности отключены](some-availability-replicas-are-disconnected.md).|Предупреждение|Группа доступности|  
|Состояние роли реплики доступности|[Реплика доступности не имеет работоспособной роли](availability-replica-does-not-have-a-healthy-role.md).|Critical|реплика доступности|  
|Состояние соединения с репликами доступности|[Реплика доступности отключена](availability-replica-is-disconnected.md).|Critical|реплика доступности|  
|Состояние присоединения реплики доступности|[Реплика доступности не присоединена](availability-replica-is-not-joined.md).|Предупреждение|реплика доступности|  
|Состояние синхронизации данных реплики доступности|[Состояние синхронизации данных некоторых баз данных доступности не является работоспособным](data-synchronization-state-of-some-availability-database-is-not-healthy.md).|Предупреждение|реплика доступности|  
|Состояние приостановки базы данных доступности|[База данных доступности приостановлена](availability-database-is-suspended.md).|Предупреждение|База данных доступности|  
|Состояние присоединения базы данных доступности|[База данных-получатель не присоединена](secondary-database-is-not-joined.md).|Предупреждение|База данных доступности|  
|Состояние синхронизации базы данных доступности|[Состояние синхронизации данных базы данных доступности не является работоспособным](data-synchronization-state-of-availability-database-is-not-healthy.md).|Предупреждение|База данных доступности|  
  
> [!IMPORTANT]  
>  **<sup>*</sup>** Для политик AlwaysOn имена категорий используются в качестве идентификаторов. При изменении имени категории AlwaysOn ее функция оценки работоспособности будет нарушена. Поэтому не следует изменять имена категорий AlwaysOn.  
  
##  <a name="Dashboard"></a>Панель мониторинга AlwaysOn  
 Панель мониторинга AlwaysOn дает обзорное представление исправности группы доступности. На панели мониторинга AlwaysOn имеются следующие функции.  
  
-   Позволяет легко увидеть сведения о данной группе доступности, а также ее реплик доступности и баз данных.  
  
-   Показывает визуальные признаки ключевых состояний, чтобы помочь администраторам баз данных принимать быстрые рабочие решения.  
  
-   Предоставляет точки запуска для сценариев устранения неполадок.  
  
-   Для данной рабочей проблемы выдает в диалоговом окне **Результат оценки политики** сведения о нарушениях определенной политики исправности AlwaysOn и ссылки на справку для исправления.  
  
-   Предоставляет средство просмотра расширенных событий исправности с целью показа предшествующих событий для специфических проблем AlwaysOn.  
  
-   Если автоматическое переключение группы доступности может помочь устранению, предоставляет точку запуска для ссылок[мастера перехода на другой ресурс для группы доступности](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md). Этот мастер помогает администратору базы данных выполнить переход на другой ресурс вручную.  
  
##  <a name="ExtendHealthModel"></a>Расширение модели работоспособности AlwaysOn  
 Расширение модели исправности [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] — это просто создание собственных пользовательских политик и их размещение в категориях по типам наблюдаемых объектов.  После изменения некоторых параметров панель мониторинга AlwaysOn автоматически вычисляет собственные, определяемые пользователем политики, а также стандартные политики AlwaysOn.  
  
 Определяемая пользователем политика может применять доступные аспекты управления на основе политик, включая те из них, которые используются в стандартных политиках AlwaysOn (см. подраздел [Стандартные политики и проблемы](#AlwaysOnPBM) выше). Аспект сервера содержит следующие свойства для мониторинга работоспособности [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]: (`IsHadrEnabled` и `HadrManagerStatus`). Аспект сервера содержит также следующие свойства политики для мониторинга конфигурации кластера WSFC: `ClusterQuorumType` и `ClusterQuorumState`.  
  
 Дополнительные сведения см. в записи [The AlwaysOn Health Model Part 2 -- Extending the Health Model](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/extending-the-alwayson-health-model.aspx) (Модель работоспособности AlwaysOn, часть 2. Расширение модели работоспособности) блога группы разработчиков SQL Server AlwaysOn.  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Используйте политики AlwaysOn для просмотра работоспособности группы доступности &#40;SQL Server&#41;](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)  
  
-   [Использование панели мониторинга AlwaysOn &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [Аварийное восстановление WSFC с помощью принудительного &#40;кворума SQL Server&#41;](../../../sql-server/failover-clusters/windows/wsfc-disaster-recovery-through-forced-quorum-sql-server.md)  
  
-   [Принудительный запуск кластера WSFC без кворума](../../../sql-server/failover-clusters/windows/force-a-wsfc-cluster-to-start-without-a-quorum.md)  
  
-   [Выполнение принудительного перехода на другой ресурс вручную для группы доступности &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [Устранение неполадок при &#40;операции добавления файла группы доступности AlwaysOn&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="RelatedContent"></a> См. также  
  
-   [The AlwaysOn Health Model Part 1 -- Health Model Architecture](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/extending-the-alwayson-health-model.aspx)  
  
-   [The AlwaysOn Health Model Part 2 -- Extending the Health Model](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/extending-the-alwayson-health-model.aspx)  
  
-   [Руководство по решениям режима AlwaysOn в Microsoft SQL Server для обеспечения высокой доступности и аварийного восстановления](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
## <a name="see-also"></a>См. также:  
 [Группы доступности AlwaysOn (SQL Server)](always-on-availability-groups-sql-server.md)   
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Администрирование &#40;SQL Server группы доступности&#41;](administration-of-an-availability-group-sql-server.md)   
 [Мониторинг групп доступности &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)  
  
  
