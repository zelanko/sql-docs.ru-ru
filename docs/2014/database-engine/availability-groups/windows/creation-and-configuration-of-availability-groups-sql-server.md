---
title: Создание и настройка групп доступности (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], creating
ms.assetid: 7f89fab8-6ee2-4273-9de0-e594bfb9407f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c9858638287876d31733035d1a6bb6d95705708f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "75228718"
---
# <a name="creation-and-configuration-of-availability-groups-sql-server"></a>Создание и настройка групп доступности (SQL Server)
  В подразделах этого раздела описано развертывание реализации [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] на экземплярах [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] , расположенных на различных узлах отказоустойчивой кластеризации Windows Server (WSFC), с помощью одного кластера отработки отказа WSFC.  
  
 Перед созданием первой группы доступности настоятельно рекомендуется ознакомиться со сведениями, представленными в следующих темах.  
  
 [Предварительные требования, ограничения и рекомендации для группы доступности AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
 В этом разделе описываются необходимые условия, ограничения и рекомендации для компьютеров, узлы кластеров WSFC, экземпляры [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], группы доступности, реплики и базы данных. В этой теме также содержатся сведения о мерах безопасности.  
  
 [Начало работы с группы доступности AlwaysOn &#40;SQL Server&#41;](getting-started-with-always-on-availability-groups-sql-server.md)  
 Содержит сведения о шагах по настройке экземпляра сервера, созданию группы доступности, настройке группы доступности для подключения клиентов, управлению группами доступности и их отслеживанию.  
  
 
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Настройка экземпляра сервера для[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]**  
  
-   [Включение и отключение группы доступности AlwaysOn &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
-   [Создание конечной точки зеркального отображения базы данных для группы доступности AlwaysOn &#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [Создание конечной точки зеркального отображения базы данных для проверки подлинности Windows &#40;Transact-SQL&#41;](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Разрешить использование сертификатов для исходящих соединений в конечной точке зеркального отображения базы данных &#40;Transact-SQL&#41;](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
 **Сведения о начале настройки групп доступности AlwaysOn**  
  
-   [Начало работы с группы доступности AlwaysOn &#40;SQL Server&#41;](getting-started-with-always-on-availability-groups-sql-server.md)  
  
 **Создание и настройка новой группы доступности**  
  
-   [Использование мастера групп доступности &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Создание группы доступности &#40;&#41;Transact-SQL](create-an-availability-group-transact-sql.md)  
  
-   [Создание SQL Server PowerShell &#40;группы доступности&#41;](../../../powershell/sql-server-powershell.md)  
  
-   [Используйте диалоговое окно Создание группы доступности &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Укажите URL-адрес конечной точки при добавлении или изменении &#40;реплики доступности SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [Создание или настройка прослушивателя группы доступности (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Настройка гибкой политики отработки отказа для обеспечения контроля над автоматическим переходом на другой ресурс (группы доступности AlwaysOn)](configure-flexible-automatic-failover-policy.md)  
  
-   [Настройка резервного копирования на реплики доступности &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [Настройка доступа только для чтения в реплике доступности (SQL Server)](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [Настройка маршрутизации только для чтения в группе доступности (SQL Server)](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [Присоединение вторичной реплики к группе доступности &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Запуск перемещения данных для базы данных-получателя AlwaysOn &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)  
  
-   [Вручную Подготовьте базу данных-получатель для группы доступности &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Присоединение базы данных-получателя к группе доступности &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Управление именами входа и заданиями для баз данных группы доступности &#40;SQL Server&#41;](../../logins-and-jobs-for-availability-group-databases.md)  
  
 **Устранение неполадок**  
  
-   [Устранение неполадок при группы доступности AlwaysOn конфигурации (SQL Server)](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [Устранение неполадок при &#40;операции добавления файла группы доступности AlwaysOn&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="RelatedContent"></a> См. также  
  
-   **Тех**  
  
     [Обучающая серия AlwaysON — HADRON. использование пулов рабочих потоков для баз данных с HADRON](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [Блоги группы разработчиков SQL Server AlwaysOn: официальный блог группы разработчиков SQL Server AlwaysOn](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Блоги SQL Server инженеров CSS](https://blogs.msdn.com/b/psssql/)  
  
-   **Презентации**  
  
     [Microsoft SQL Server с рабочим названием Denali AlwaysOn, часть 1: вводные сведения о решении следующего поколения по обеспечению высокого уровня доступности](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server с рабочим названием Denali AlwaysOn, часть 2: создание критически важного решения по обеспечению высокого уровня доступности с использованием AlwaysOn](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Технические документы**  
  
     [Руководство по решениям режима AlwaysOn в Microsoft SQL Server для обеспечения высокой доступности и аварийного восстановления](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Технические документы Майкрософт для SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Технические документы группы консультирования клиентов SQL Server](http://sqlcat.com/)  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Администрирование &#40;SQL Server группы доступности&#41;](administration-of-an-availability-group-sql-server.md)   
 [Политики AlwaysOn для проблем в работе с группы доступности AlwaysOn (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md)   
 [Мониторинг групп доступности &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)   
 [Группы доступности AlwaysOn: взаимодействие (SQL Server)](always-on-availability-groups-interoperability-sql-server.md)  
  
