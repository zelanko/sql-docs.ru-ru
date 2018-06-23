---
title: Реализация заданий | Документация Майкрософт
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
- jobs [SQL Server Agent]
- SQL Server Agent jobs
- SQL Server Agent jobs, about jobs
- jobs [SQL Server Agent], about jobs
ms.assetid: 69e06724-25c7-4fb3-8a5b-3d4596f21756
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3b319ced7f40ec9e1bc45b7e1bb3568e7fb8fd7e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102356"
---
# <a name="implement-jobs"></a>Реализация заданий
  Задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяют автоматизировать задачи администрирования и сделать их выполнение более эффективным.  
  
 Задание — это определенная цепочка действий, последовательно выполняемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Задание может выполнять различные действия, включая запуск скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] , приложений командной строки, скриптов Microsoft ActiveX, пакетов служб Integration Services, запросов и команд служб Analysis Services или задач репликации. Задание может выполнять повторяющиеся задачи или задачи, запуск которых определяется расписанием; кроме того, оно может автоматически уведомлять пользователей о своем состоянии, значительно упрощая администрирование сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Задания можно запускать вручную, по расписанию или в ответ на оповещения.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Описание**|**Раздел**|  
|Содержит сведения о создании заданий и назначении владельца.|[Создание заданий](create-jobs.md)|  
|Содержит сведения об организации заданий по категориям.|[Упорядочивание заданий](organize-jobs.md)|  
|Содержит сведения о различных видах шагов заданий, их создании и управлении ими.|[Управление шагами задания](manage-job-steps.md)|  
|Содержит сведения о том, как определить время запуска и частоту выполнения заданий.|[Создание и присоединение расписаний к заданиям](create-and-attach-schedules-to-jobs.md)|  
|Содержит сведения о заданиях, запускаемых вручную (не по расписанию).|[Запуск заданий](run-jobs.md)|  
|Содержит сведения о том, как настроить реакцию агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на задания. Например агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может уведомлять администраторов о завершении заданий.|[Определение ответов заданий](specify-job-responses.md)|  
|Содержит сведения о том, как просмотреть или изменить существующие задания и просмотреть историю их выполнения.|[Просмотр или изменение заданий](view-or-modify-jobs.md)|  
|Содержит сведения об удалении заданий.|[Удаление заданий](delete-jobs.md)|  
  
## <a name="see-also"></a>См. также  
 [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md)  
  
  