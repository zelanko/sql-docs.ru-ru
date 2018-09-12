---
title: Реализация заданий | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent]
- SQL Server Agent jobs
- SQL Server Agent jobs, about jobs
- jobs [SQL Server Agent], about jobs
ms.assetid: 69e06724-25c7-4fb3-8a5b-3d4596f21756
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 376669247512c48b21aca1600151c1dac5d6e2f3
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43818880"
---
# <a name="implement-jobs"></a>Реализация заданий
  Задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяют автоматизировать задачи администрирования и сделать их выполнение более эффективным.  
  
 Задание — это определенная цепочка действий, последовательно выполняемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Задание может выполнять различные действия, включая запуск скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] , приложений командной строки, скриптов Microsoft ActiveX, пакетов служб Integration Services, запросов и команд служб Analysis Services или задач репликации. Задание может выполнять повторяющиеся задачи или задачи, запуск которых определяется расписанием; кроме того, оно может автоматически уведомлять пользователей о своем состоянии, значительно упрощая администрирование сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Задания можно запускать вручную, по расписанию или в ответ на оповещения.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
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
  
  
