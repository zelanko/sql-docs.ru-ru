---
title: Создание заданий | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], creating
- SQL Server Agent jobs, creating
ms.assetid: 465fb7fc-7622-4252-a178-ea51691c935b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4f9424846c714070ff6bf22043d174762f873117
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85008944"
---
# <a name="create-jobs"></a>Создание заданий
  Задание — это определенная цепочка действий, последовательно выполняемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Задание может выполнять широкий диапазон действий, например запуск скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] , приложений командной строки, скриптов Microsoft ActiveX, пакетов Integration Services, команд и запросов Analysis Services и задач репликации. Задания могут запускать повторяющиеся или запланированные задачи, они могут автоматически уведомлять пользователей о состоянии задания, формируя предупреждения и тем самым значительно упрощают администрирование [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Чтобы создать задание, пользователь должен быть членом одной из предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или членом предопределенной роли сервера **sysadmin** . Задание может быть изменено его владельцем или членом роли **sysadmin** . Члены роли **sysadmin** могут предоставлять права владения заданием другим пользователям, а также запускать любое задание, независимо от того, кто является его владельцем. Дополнительные сведения о предопределенных ролях базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Предопределенные роли базы данных агента SQL Server](sql-server-agent-fixed-database-roles.md).  
  
 Задания могут выполняться на локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или быть распределены по нескольким экземплярам, работающим на предприятии. Для запуска заданий на нескольких серверах необходимо установить, по крайней мере, один главный сервер и один или несколько целевых. Дополнительные сведения о главных и целевых серверах см. в статье [Автоматизация администрирования в масштабах предприятия](automated-administration-across-an-enterprise.md)  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент записывает сведения о задании и шагах задания в журнал заданий.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|||  
|-|-|  
|**Описание**|**Раздел**|  
|Описывает создание задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[Создание задания](create-a-job.md)|  
|Описывает переназначение владения заданиями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] другому пользователю.|[Give Others Ownership of a Job](give-others-ownership-of-a-job.md)|  
|Описывает настройку журнала заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[Set Up the Job History Log](set-up-the-job-history-log.md)|  
  
## <a name="see-also"></a>См. также:  
 [Управление шагами задания](manage-job-steps.md)   
 [Автоматизированное администрирование в масштабах предприятия](automated-administration-across-an-enterprise.md)   
 [Создание и присоединение расписаний к заданиям](create-and-attach-schedules-to-jobs.md)   
 [Запуск заданий](run-jobs.md)   
 [Просмотр или изменение заданий](view-or-modify-jobs.md)  
  
  
