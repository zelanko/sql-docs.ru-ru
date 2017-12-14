---
title: "Просмотр или изменение заданий | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- jobs [SQL Server Agent], viewing
- modifying jobs
- viewing jobs
- SQL Server Agent jobs, viewing
- SQL Server Agent jobs, modifying
- displaying jobs
ms.assetid: 57f649b8-190c-4304-abd7-7ca5297deab7
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f5612d516ed5aebfc5bdbd05fced0881c499395d
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="view-or-modify-jobs"></a>Просмотр или изменение заданий
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Можно просматривать любые созданные задания. После запуска задания можно также просматривать его журнал. Просмотр журнала задания позволяет видеть, где было запущено задание, состояние задания в целом и состояние каждого шага задания. Можно определить, выполнялось ли ранее это задание с ошибками, когда было последнее успешное завершение задания, какой вывод создавался после каждого запуска задания. Члены предопределенной роли сервера **sysadmin** могут просматривать и изменять любые задания, независимо от того, кто их владелец.  
  
> [!NOTE]  
> Для создания журнала заданий, задание должно быть выполнено хотя бы раз. Можно ограничить общий размер журнала заданий, а также размеры журналов отдельных заданий.  
  
Наконец, можно изменить задание, чтобы оно отвечало новым требованиям. Можно менять:  
  
-   параметры ответа;  
  
-   Расписания  
  
-   шаги задания;  
  
-   владельца;  
  
-   категорию задания;  
  
-   целевые серверы (только для многосерверных заданий).  
  
Чтобы убедиться в том, что изменения многосерверных заданий вступили в силу, отправьте изменения в список загрузки, чтобы целевые серверы могли загрузить обновленное задание. Чтобы убедиться, что на целевых серверах находятся самые последние определения заданий, отправьте инструкцию INSERT после обновления многосерверного задания:  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
Дополнительные сведения см. в разделе [sp_purge_jobhistory (Transact-SQL)](http://msdn.microsoft.com/en-us/237f9bad-636d-4262-9bfb-66c034a43e88).  
  
Члены предопределенной роли сервера **sysadmin** могут просматривать определение и журнал любого задания, а также изменять любое задание.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|||  
|-|-|  
|**Description**|**Раздел**|  
|Описывает, как просмотреть задания агента [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .|[View a Job](../../ssms/agent/view-a-job.md)|  
|Описывает, как просматривать журнал заданий агента [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .|[View the Job History](../../ssms/agent/view-the-job-history.md)|  
|Описывает, как удалить содержимое журнала заданий агента [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .|[Clear the Job History Log](../../ssms/agent/clear-the-job-history-log.md)|  
|Описывает установление ограничений на размер журналов заданий агента [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .|[Resize the Job History Log](../../ssms/agent/resize-the-job-history-log.md)|  
|Описывает, как изменить свойства заданий агента [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .|[Modify a Job](../../ssms/agent/modify-a-job.md)|  
  
## <a name="see-also"></a>См. также:  
[sysjobhistory](http://msdn.microsoft.com/en-us/1b1fcdbb-2af2-45e6-bf3f-e8279432ce13)  
  
