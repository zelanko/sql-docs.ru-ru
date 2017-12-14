---
title: "Наблюдение за активностью заданий | Документация Майкрософт"
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
- SQL Server Agent, monitoring
- jobs [SQL Server Agent], monitoring
- monitoring [SQL Server], jobs
- activity monitoring [SQL Server Agent]
- monitoring [SQL Server], SQL Server Agent
- monitoring [SQL Server Agent]
- SQL Server Agent Job Activity Monitor
- SQL Server Agent jobs, monitoring
- performance [SQL Server], jobs
- current activity
ms.assetid: 71cb432b-631d-4b8b-9965-e731b3d8266d
caps.latest.revision: "6"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ddc5235281231c8d1aa08a22e7f55fe4131480d5
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="monitor-job-activity"></a>Наблюдение за активностью заданий
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Текущую активность всех определенных заданий экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] можно контролировать при помощи монитора активности заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
## <a name="sql-server-agent-sessions"></a>Сеансы агента SQL Server  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Агент создает новый сеанс при каждом запуске службы. При создании нового сеанса таблица **sysjobactivity** в базе данных **msdb** заполняется всеми существующими определенными заданиями. При перезапуске агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] в этой таблице сохраняются данные о последних действиях заданий. В каждом сеансе записываются данные об обычных действиях заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , от начала каждого задания до его завершения. Данные об этих сеансах сохраняются в таблице **syssessions** базы данных **msdb** .  
  
## <a name="job-activity-monitor"></a>Монитор активности заданий  
Монитор активности заданий позволяет просмотреть таблицу **sysjobactivity** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. Можно просматривать все задания на сервере или можно определить фильтры, ограничивающие количество отображаемых заданий. Можно также отсортировать данные о заданиях, щелкнув заголовок столбца в сетке **Активность заданий агента** . Например, при выборе заголовка столбца **Последний запуск** можно просмотреть задания в том порядке, в котором они выполнялись в последний раз. При повторном щелчке заголовка столбца производится переключение порядка отображения заданий по дате их последнего выполнения: порядок по возрастанию меняется на порядок по убыванию, и наоборот.  
  
Использование монитора активности заданий позволяет выполнять следующие задачи:  
  
-   Запускать и останавливать задания.  
  
-   Просматривать свойства заданий.  
  
-   Просматривать журнал определенного задания.  
  
-   Обновлять данные в сетке **Активность заданий агента** вручную или задавать интервал автоматического обновления после нажатия кнопки **Просмотреть настройки обновления**.  
  
Монитор активности заданий используется, если необходимо определить, какие задания запланированы на выполнение, результаты последнего выполнения заданий в ходе текущего сеанса, а также для определения того, какие задания в настоящее время выполняются или бездействуют. При неожиданном неуспешном завершении службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] можно определить, какие задания были наиболее активны, проанализировав данные предыдущего сеанса в мониторе активности заданий.  
  
Чтобы открыть монитор активности заданий, разверните узел **Агент SQL Server** в обозревателе объектов среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] , правой кнопкой мыши щелкните **Монитор активности заданий**и выберите **Просмотр активности заданий**.  
  
Просмотреть активность заданий текущего сеанса также можно с помощью хранимой процедуры **sp_help_jobactivity**.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|||  
|-|-|  
|**Description**|**Раздел**|  
|Описывает, как просмотреть состояние времени выполнения для заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .|[Просмотр активности заданий](../../ssms/agent/view-job-activity.md)|  
  
## <a name="see-also"></a>См. также:  
[Просмотр активности заданий](../../ssms/agent/view-job-activity.md)  
[sysjobactivity (Transact-SQL)](http://msdn.microsoft.com/en-us/fd17cac9-5d1f-4b44-b2dc-ee9346d8bf1e)  
[syssessions (Transact-SQL)](http://msdn.microsoft.com/en-us/187819b6-c7f4-4a26-b74c-0a89e96695cf)  
[sp_help_jobactivity (Transact-SQL)](http://msdn.microsoft.com/en-us/d344864f-b4d3-46b1-8933-b81dec71f511)  
  
