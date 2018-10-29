---
title: Наблюдение за активностью заданий | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
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
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: f83ca887d7028f7ffcdcf0f9fab78155d6ac915c
ms.sourcegitcommit: 9f2edcdf958e6afce9a09fb2e572ae36dfe9edb0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50100035"
---
# <a name="monitor-job-activity"></a>Наблюдение за активностью заданий
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Текущую активность всех определенных заданий экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно контролировать при помощи монитора активности заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="sql-server-agent-sessions"></a>Сеансы агента SQL Server  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент создает новый сеанс при каждом запуске службы. При создании нового сеанса таблица **sysjobactivity** в базе данных **msdb** заполняется всеми существующими определенными заданиями. При перезапуске агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в этой таблице сохраняются данные о последних действиях заданий. В каждом сеансе записываются данные об обычных действиях заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , от начала каждого задания до его завершения. Данные об этих сеансах сохраняются в таблице **syssessions** базы данных **msdb** .  
  
## <a name="job-activity-monitor"></a>Монитор активности заданий  
Монитор активности заданий позволяет просмотреть таблицу **sysjobactivity** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Можно просматривать все задания на сервере или можно определить фильтры, ограничивающие количество отображаемых заданий. Можно также отсортировать данные о заданиях, щелкнув заголовок столбца в сетке **Активность заданий агента** . Например, при выборе заголовка столбца **Последний запуск** можно просмотреть задания в том порядке, в котором они выполнялись в последний раз. При повторном щелчке заголовка столбца производится переключение порядка отображения заданий по дате их последнего выполнения: порядок по возрастанию меняется на порядок по убыванию, и наоборот.  
  
Использование монитора активности заданий позволяет выполнять следующие задачи:  
  
-   Запускать и останавливать задания.  
  
-   Просматривать свойства заданий.  
  
-   Просматривать журнал определенного задания.  
  
-   Обновлять данные в сетке **Активность заданий агента** вручную или задавать интервал автоматического обновления после нажатия кнопки **Просмотреть настройки обновления**.  
  
Монитор активности заданий используется, если необходимо определить, какие задания запланированы на выполнение, результаты последнего выполнения заданий в ходе текущего сеанса, а также для определения того, какие задания в настоящее время выполняются или бездействуют. При неожиданном неуспешном завершении службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно определить, какие задания были наиболее активны, проанализировав данные предыдущего сеанса в мониторе активности заданий.  
  
Чтобы открыть монитор активности заданий, разверните узел **Агент SQL Server** в обозревателе объектов среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] , правой кнопкой мыши щелкните **Монитор активности заданий**и выберите **Просмотр активности заданий**.  
  
Просмотреть активность заданий текущего сеанса также можно с помощью хранимой процедуры **sp_help_jobactivity**.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|||  
|-|-|  
|**Описание**|**Раздел**|  
|Описывает, как просмотреть состояние времени выполнения для заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[Просмотр активности заданий](../../ssms/agent/view-job-activity.md)|  
  
## <a name="see-also"></a>См. также:  
[Просмотр активности заданий](../../ssms/agent/view-job-activity.md)  
[sysjobactivity (Transact-SQL)](http://msdn.microsoft.com/fd17cac9-5d1f-4b44-b2dc-ee9346d8bf1e)  
[syssessions (Transact-SQL)](http://msdn.microsoft.com/187819b6-c7f4-4a26-b74c-0a89e96695cf)  
[sp_help_jobactivity (Transact-SQL)](http://msdn.microsoft.com/d344864f-b4d3-46b1-8933-b81dec71f511)  
  
