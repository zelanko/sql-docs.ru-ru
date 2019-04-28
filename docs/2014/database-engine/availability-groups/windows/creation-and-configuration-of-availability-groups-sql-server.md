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
ms.openlocfilehash: 14dea0c618f754024a18ca24d64b98b08aa99f64
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62789282"
---
# <a name="creation-and-configuration-of-availability-groups-sql-server"></a>Создание и настройка групп доступности (SQL Server)
  В подразделах этого раздела описано развертывание реализации [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] на экземплярах [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] , расположенных на различных узлах отказоустойчивой кластеризации Windows Server (WSFC), с помощью одного кластера отработки отказа WSFC.  
  
 Перед созданием первой группы доступности настоятельно рекомендуется ознакомиться со сведениями, представленными в следующих темах.  
  
 [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
 В этом разделе описываются необходимые условия, ограничения и рекомендации для компьютеров, узлы кластеров WSFC, экземпляры [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], группы доступности, реплики и базы данных. В этой теме также содержатся сведения о мерах безопасности.  
  
 [Приступая к работе с группами доступности AlwaysOn &#40;SQL Server&#41;](getting-started-with-always-on-availability-groups-sql-server.md)  
 Содержит сведения о шагах по настройке экземпляра сервера, созданию группы доступности, настройке группы доступности для подключения клиентов, управлению группами доступности и их отслеживанию.  
  
 
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Настройка экземпляра сервера для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]**  
  
-   [Включение и отключение групп доступности AlwaysOn (SQL Server)](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
-   [Создание базы данных конечной точки зеркального отображения для групп доступности AlwaysOn &#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [Создание конечной точки зеркального отображения базы данных с проверкой подлинности Windows (Transact-SQL)](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Включение использования сертификатов для исходящих соединений в конечной точке зеркального отображения базы данных (Transact-SQL)](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
 **Чтобы приступить к работе с настройкой группы доступности AlwaysOn**  
  
-   [Приступая к работе с группами доступности AlwaysOn &#40;SQL Server&#41;](getting-started-with-always-on-availability-groups-sql-server.md)  
  
 **Создание и настройка новой группы доступности**  
  
-   [Использование мастера групп доступности (среда SQL Server Management Studio)](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Создание группы доступности (Transact-SQL)](create-an-availability-group-transact-sql.md)  
  
-   [Создание группы доступности (SQL Server PowerShell)](../../../powershell/sql-server-powershell.md)  
  
-   [Использование диалогового окна "Создание группы доступности" (среда SQL Server Management Studio)](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Укажите URL-адрес конечной точки при добавлении или изменении реплики доступности (SQL Server)](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [Создание или настройка прослушивателя группы доступности (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Настройка гибкой политики отработки отказа для обеспечения контроля над для автоматической отработки отказа (группы доступности AlwaysOn)](configure-flexible-automatic-failover-policy.md)  
  
-   [Настройка резервного копирования в репликах доступности (SQL Server)](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [Настройка доступа только для чтения в реплике доступности (SQL Server)](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [Настройка маршрутизации только для чтения в группе доступности (SQL Server)](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [Присоединение вторичной реплики к группе доступности (SQL Server)](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Запуск перемещения данных для базы данных-получателя AlwaysOn &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)  
  
-   [Подготовка базы данных-получателя для присоединения к группе доступности вручную (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Присоединение базы данных-получателя к группе доступности (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Управление именами входа и заданиями для баз данных группы доступности (SQL Server)](../../logins-and-jobs-for-availability-group-databases.md)  
  
 **Сведения для поиска и устранения неполадок**  
  
-   [Устранение неполадок конфигурации групп доступности AlwaysOn (SQL Server) удалена](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [Устранение неполадок с операцией добавления файла, завершившейся сбоем &#40;группы доступности AlwaysOn&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="RelatedContent"></a> См. также  
  
-   **Блоги**  
  
     [AlwaysON — HADRON обучающая серия. Использование рабочего пула для баз данных с HADRON](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [Блоги группы AlwaysOn SQL Server: Официальный блог по SQL Server AlwaysOn Team](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Блоги инженеров CSS SQL Server](https://blogs.msdn.com/b/psssql/)  
  
-   **Видеоролики**  
  
     [Серия Microsoft SQL Server с кодовым названием «Denali» AlwaysOn, часть 1: вводные сведения о решении следующего поколения по обеспечению высокого уровня доступности](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Серия Microsoft SQL Server с кодовым названием «Denali» AlwaysOn, часть 2: Создание решения критически важных высокого уровня доступности с помощью AlwaysOn](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Технические документы**  
  
     [Microsoft SQL Server AlwaysOn Solutions Guide for высокий уровень доступности и аварийного восстановления](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Технические документы Майкрософт Microsoft по SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Технические документы группы консультантов по SQL Server](http://sqlcat.com/)  
  
## <a name="see-also"></a>См. также  
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Администрирование группы доступности (SQL Server)](administration-of-an-availability-group-sql-server.md)   
 [Политики AlwaysOn на случай проблем в работе с группами доступности AlwaysOn (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md)   
 [Отслеживание групп доступности (SQL Server)](monitoring-of-availability-groups-sql-server.md)   
 [Группы доступности AlwaysOn: Взаимодействие (SQL Server)](always-on-availability-groups-interoperability-sql-server.md)  
  
  
