---
title: Просмотр или изменение заданий | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
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
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 43ceb49e01a2241ea2bd9b75bcf686c68399275b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098319"
---
# <a name="view-or-modify-jobs"></a>Просмотр или изменение заданий
  Можно просматривать любые созданные задания. После запуска задания можно также просматривать его журнал. Просмотр журнала задания позволяет видеть, где было запущено задание, состояние задания в целом и состояние каждого шага задания. Можно определить, выполнялось ли ранее это задание с ошибками, когда было последнее успешное завершение задания, какой вывод создавался после каждого запуска задания. Члены предопределенной роли сервера **sysadmin** могут просматривать и изменять любые задания, независимо от того, кто их владелец.  
  
> [!NOTE]  
>  Для создания журнала заданий, задание должно быть выполнено хотя бы раз. Можно ограничить общий размер журнала заданий, а также размеры журналов отдельных заданий.  
  
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
  
 Дополнительные сведения см. в разделе [sp_purge_jobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql).  
  
 Члены предопределенной роли сервера **sysadmin** могут просматривать определение и журнал любого задания, а также изменять любое задание.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Описание**|**Раздел**|  
|Описывает, как просмотреть задания агента [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|[View a Job](view-a-job.md)|  
|Описывает, как просматривать журнал заданий агента [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|[View the Job History](view-the-job-history.md)|  
|Описывает, как удалить содержимое журнала заданий агента [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|[Clear the Job History Log](clear-the-job-history-log.md)|  
|Описывает установление ограничений на размер журналов заданий агента [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|[Resize the Job History Log](resize-the-job-history-log.md)|  
|Описывает, как изменить свойства заданий агента [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|[Modify a Job](modify-a-job.md)|  
  
## <a name="see-also"></a>См. также  
 [dbo.sysjobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobhistory-transact-sql)  
  
  
