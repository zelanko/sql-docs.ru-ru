---
title: Создание заданий | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent], creating
- SQL Server Agent jobs, creating
ms.assetid: 465fb7fc-7622-4252-a178-ea51691c935b
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 40ec697eb5093ee690d944e0ec07cc01e2bf8ac6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095831"
---
# <a name="create-jobs"></a>Создание заданий
  Задание — это определенная цепочка действий, последовательно выполняемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Задание может выполнять широкий диапазон действий, например запуск скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] , приложений командной строки, скриптов Microsoft ActiveX, пакетов Integration Services, команд и запросов Analysis Services и задач репликации. Задания могут запускать повторяющиеся или запланированные задачи, они могут автоматически уведомлять пользователей о состоянии задания, формируя предупреждения и тем самым значительно упрощают администрирование [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Чтобы создать задание, пользователь должен быть членом одной из предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или членом предопределенной роли сервера **sysadmin** . Задание может быть изменено его владельцем или членом роли **sysadmin** . Члены роли **sysadmin** могут предоставлять права владения заданием другим пользователям, а также запускать любое задание, независимо от того, кто является его владельцем. Дополнительные сведения о предопределенных ролях базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Предопределенные роли базы данных агента SQL Server](sql-server-agent-fixed-database-roles.md).  
  
 Задания могут выполняться на локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или быть распределены по нескольким экземплярам, работающим на предприятии. Для запуска заданий на нескольких серверах необходимо установить, по крайней мере, один главный сервер и один или несколько целевых. Дополнительные сведения о главных и целевых серверах см. в статье [Автоматизация администрирования в масштабах предприятия](automated-administration-across-an-enterprise.md)  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент записывает сведения о задании и шагах задания в журнал заданий.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Описание**|**Раздел**|  
|Описывает создание задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[Создание задания](create-a-job.md)|  
|Описывает переназначение владения заданиями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] другому пользователю.|[Give Others Ownership of a Job](give-others-ownership-of-a-job.md)|  
|Описывает настройку журнала заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[Set Up the Job History Log](set-up-the-job-history-log.md)|  
  
## <a name="see-also"></a>См. также  
 [Управление шагами задания](manage-job-steps.md)   
 [Автоматизация администрирования в масштабах предприятия](automated-administration-across-an-enterprise.md)   
 [Создание и присоединение расписаний к заданиям](create-and-attach-schedules-to-jobs.md)   
 [Запуск заданий](run-jobs.md)   
 [Просмотр или изменение заданий](view-or-modify-jobs.md)  
  
  