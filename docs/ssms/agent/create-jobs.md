---
description: Создание заданий
title: Создание заданий
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], creating
- SQL Server Agent jobs, creating
ms.assetid: 465fb7fc-7622-4252-a178-ea51691c935b
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 3d4559bb32152f7e4ba99f7d598c3f9080caccc9
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92038017"
---
# <a name="create-jobs"></a>Создание заданий
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Задание — это определенная цепочка действий, последовательно выполняемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Задание может выполнять широкий диапазон действий, например запуск скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] , приложений командной строки, скриптов Microsoft ActiveX, пакетов Integration Services, команд и запросов Analysis Services и задач репликации. Задания могут запускать повторяющиеся или запланированные задачи, они могут автоматически уведомлять пользователей о состоянии задания, формируя предупреждения и тем самым значительно упрощают администрирование [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
Чтобы создать задание, пользователь должен быть членом одной из предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или членом предопределенной роли сервера **sysadmin** . Задание может быть изменено его владельцем или членом роли **sysadmin** . Члены роли **sysadmin** могут предоставлять права владения заданием другим пользователям, а также запускать любое задание, независимо от того, кто является его владельцем. Дополнительные сведения о предопределенных ролях базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
Задания могут выполняться на локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или быть распределены по нескольким экземплярам, работающим на предприятии. Для запуска заданий на нескольких серверах необходимо установить, по крайней мере, один главный сервер и один или несколько целевых. Дополнительные сведения о главных и целевых серверах см. в статье [Автоматизация администрирования в масштабах предприятия](../../ssms/agent/automated-administration-across-an-enterprise.md)  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент записывает сведения о задании и шагах задания в журнал заданий.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание|Раздел|  
|-|-|  
|Описывает создание задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[Создание задания](../../ssms/agent/create-a-job.md)|  
|Описывает переназначение владения заданиями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] другому пользователю.|[Give Others Ownership of a Job](../../ssms/agent/give-others-ownership-of-a-job.md)|  
|Описывает настройку журнала заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[Set Up the Job History Log](../../ssms/agent/set-up-the-job-history-log.md)|  
  
## <a name="see-also"></a>См. также:  
[Управление шагами задания](../../ssms/agent/manage-job-steps.md)  
[Автоматизация администрирования в масштабах предприятия](../../ssms/agent/automated-administration-across-an-enterprise.md)  
[Создание и присоединение расписаний к заданиям](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
[Запуск заданий](../../ssms/agent/run-jobs.md)  
[Просмотр или изменение заданий](../../ssms/agent/view-or-modify-jobs.md)  
