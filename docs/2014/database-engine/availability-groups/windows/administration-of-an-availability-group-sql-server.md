---
title: Администрирование группы доступности (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], managing
ms.assetid: 0b7542fa-235e-413d-81bf-3eff9ee07480
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e8d826201f44bb666050f5229b4824b5c2198dc0
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75228999"
---
# <a name="administration-of-an-availability-group-sql-server"></a>Администрирование группы доступности (SQL Server)
  Управление существующей группой доступности AlwaysOn в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] включает в себя одну или несколько следующих задач.  
  
-   Изменение свойств существующей реплики доступности, например для изменения клиентского доступа к соединению (для настройки вторичных реплик, доступных для чтения), изменение режима отработки отказа, режима доступности или задание времени ожидания сеанса.  
  
-   Добавление или удаление вторичных реплик.  
  
-   Добавление или удаление базы данных.  
  
-   Приостановка или возобновление работы базы данных.  
  
-   Выполнение запланированной отработки отказа вручную ( *отработка отказа вручную*) или принудительной отработки отказа вручную ( *принудительная отработка отказа*).  
  
-   Создание или настройка прослушивателя группы доступности.  
  
-   Управление [доступными для чтения вторичными репликами](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) для данной группы доступности. Необходимо настроить доступ для чтения для одной или нескольких реплик, выполняемых под вторичной ролью, и настроить маршрутизацию только для чтения.  
  
-   Управление [резервными копиями вторичных реплик](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) определенной группы доступности. Необходимо настроить место выполнения задач по созданию резервных копий и написать скрипты для этих задач. необходимо создать скрипты заданий резервного копирования для каждой базы данных в группе доступности на каждом экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на котором размещается реплика доступности.  
  
-   Удаление группы доступности.  
  
-   Миграция между кластерами групп доступности AlwaysOn для обновления ОС  
  
  
##  <a name="RelatedTasks"></a>Связанные задачи  
 **Настройка существующей группы доступности**  
  
-   [Добавление вторичной реплики в группу доступности &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Удаление вторичной реплики из группы доступности &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [Добавление базы данных в группу доступности &#40;SQL Server&#41;](availability-group-add-a-database.md)  
  
-   [Удаление базы данных-получателя из группы доступности &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [Удаление базы данных-источника из группы доступности &#40;SQL Server&#41;](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [Настройка гибкой политики отработки отказа для управления условиями автоматического перехода на другой ресурс &#40;группы доступности AlwaysOn&#41;](configure-flexible-automatic-failover-policy.md)  
  
 **Управление группой доступности**  
  
-   [Настройка резервного копирования на реплики доступности &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [Выполнение запланированного перехода на другой ресурс вручную для группы доступности &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [Выполнение принудительного перехода на другой ресурс вручную для группы доступности &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [Удаление SQL Server &#40;группы доступности&#41;](remove-an-availability-group-sql-server.md)  
  
 **Управление репликой доступности**  
  
-   [Добавление вторичной реплики в группу доступности &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Присоединение вторичной реплики к группе доступности &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Удаление вторичной реплики из группы доступности &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [Изменение режима доступности реплики доступности &#40;SQL Server&#41;](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [Изменение режима отработки отказа для реплики доступности &#40;SQL Server&#41;](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [Настройка резервного копирования на реплики доступности &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [Настройка доступа только для чтения в реплике доступности &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [Настройка маршрутизации только для чтения для группы доступности &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [Изменение времени ожидания сеанса для реплики доступности &#40;SQL Server&#41;](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 **Управление базой данных доступности**  
  
-   [Добавление базы данных в группу доступности &#40;SQL Server&#41;](availability-group-add-a-database.md)  
  
-   [Присоединение базы данных-получателя к группе доступности &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Удаление базы данных-источника из группы доступности &#40;SQL Server&#41;](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [Удаление базы данных-получателя из группы доступности &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [Приостановка &#40;базы данных доступности SQL Server&#41;](suspend-an-availability-database-sql-server.md)  
  
-   [Возобновление &#40;базы данных доступности SQL Server&#41;](resume-an-availability-database-sql-server.md)  
  
 **Мониторинг группы доступности**  
  
-   [Мониторинг групп доступности &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)  
  
 **Поддержка миграции групп доступности на новый кластер WSFC (миграция с одного кластера на другой)**  
  
-   [Измените контекст кластера HADR &#40;экземпляра сервера SQL Server&#41;](change-the-hadr-cluster-context-of-server-instance-sql-server.md)  
  
-   [Переведите группу доступности в автономный режим &#40;SQL Server&#41;](../../take-an-availability-group-offline-sql-server.md)  
  
  
##  <a name="RelatedContent"></a>Связанное содержимое  
  
-   **Тех**  
  
     [Блоги группы разработчиков SQL Server AlwaysOn: официальный блог группы разработчиков SQL Server AlwaysOn](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Блоги SQL Server инженеров CSS](https://blogs.msdn.com/b/psssql/)  
  
-   **Презентации**  
  
     [Microsoft SQL Server с рабочим названием Denali AlwaysOn, часть 1: вводные сведения о решении следующего поколения по обеспечению высокого уровня доступности](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server с рабочим названием Denali AlwaysOn, часть 2: создание критически важного решения по обеспечению высокого уровня доступности с использованием AlwaysOn](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Технические документы:**  
  
     [Технические документы Майкрософт для SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Технические документы группы консультирования клиентов SQL Server](http://sqlcat.com/)  
  
  
## <a name="see-also"></a>См. также  
 [Группы доступности AlwaysOn &#40;SQL Server&#41;](always-on-availability-groups-sql-server.md)   
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Конфигурация экземпляра сервера для группы доступности AlwaysOn &#40;SQL Server&#41;](configuration-of-a-server-instance-for-always-on-availability-groups-sql-server.md)  
 [Создание и Настройка групп доступности &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md)   
 [Активные вторичные реплики: &#40;группы доступности AlwaysOn для чтения&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)   
 [Активные вторичные реплики: резервное копирование в &#40;-получателях группы доступности AlwaysOn&#41;](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)  
 [Прослушиватели групп доступности, подключение клиентов и отработка отказа приложений &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)   
 [Политики AlwaysOn для проблем в работе с группы доступности AlwaysOn &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md)   
 [Мониторинг групп доступности &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)   
 [Группы доступности AlwaysOn: взаимодействие &#40;SQL Server&#41;](always-on-availability-groups-interoperability-sql-server.md)   
 [Общие сведения о инструкциях Transact-SQL для группы доступности AlwaysOn &#40;SQL Server&#41;](transact-sql-statements-for-always-on-availability-groups.md)   
 [Общие сведения о командлетах PowerShell для группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
