---
title: "Реализация заданий | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent]
- SQL Server Agent jobs
- SQL Server Agent jobs, about jobs
- jobs [SQL Server Agent], about jobs
ms.assetid: 69e06724-25c7-4fb3-8a5b-3d4596f21756
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 30b61e4aa32828763d4531c53cb7f308a926798b
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="implement-jobs"></a>Реализация заданий
Задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] позволяют автоматизировать задачи администрирования и сделать их выполнение более эффективным.  
  
Задание — это определенная цепочка действий, последовательно выполняемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . Задание может выполнять различные действия, включая запуск скриптов [!INCLUDE[tsql](../../includes/tsql_md.md)] , приложений командной строки, скриптов Microsoft ActiveX, пакетов служб Integration Services, запросов и команд служб Analysis Services или задач репликации. Задание может выполнять повторяющиеся задачи или задачи, запуск которых определяется расписанием; кроме того, оно может автоматически уведомлять пользователей о своем состоянии, значительно упрощая администрирование сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
Задания можно запускать вручную, по расписанию или в ответ на оповещения.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|||  
|-|-|  
|**Description**|**Раздел**|  
|Содержит сведения о создании заданий и назначении владельца.|[Создание заданий](../../ssms/agent/create-jobs.md)|  
|Содержит сведения об организации заданий по категориям.|[Упорядочивание заданий](../../ssms/agent/organize-jobs.md)|  
|Содержит сведения о различных видах шагов заданий, их создании и управлении ими.|[Управление шагами задания](../../ssms/agent/manage-job-steps.md)|  
|Содержит сведения о том, как определить время запуска и частоту выполнения заданий.|[Создание и присоединение расписаний к заданиям](../../ssms/agent/create-and-attach-schedules-to-jobs.md)|  
|Содержит сведения о заданиях, запускаемых вручную (не по расписанию).|[Запуск заданий](../../ssms/agent/run-jobs.md)|  
|Содержит сведения о том, как настроить реакцию агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] на задания. Например агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] может уведомлять администраторов о завершении заданий.|[Определение ответов заданий](../../ssms/agent/specify-job-responses.md)|  
|Содержит сведения о том, как просмотреть или изменить существующие задания и просмотреть историю их выполнения.|[Просмотр или изменение заданий](../../ssms/agent/view-or-modify-jobs.md)|  
|Содержит сведения об удалении заданий.|[Удаление заданий](../../ssms/agent/delete-jobs.md)|  
  
## <a name="see-also"></a>См. также:  
[Обеспечение безопасности агента SQL Server](../../ssms/agent/implement-sql-server-agent-security.md)  
  

