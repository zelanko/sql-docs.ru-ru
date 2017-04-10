---
title: "Агент SQL Server, объект JobSteps | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JobSteps, объект"
  - "SQLAgent:JobSteps"
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
caps.latest.revision: 23
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 23
---
# Агент SQL Server, объект JobSteps
  Объект производительности агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  **JobSteps** содержит счетчики производительности, сообщающие сведения о шагах задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В следующей таблице перечислены счетчики этого объекта.  
  
 В следующей таблице представлены счетчики **SQLAgent:JobSteps** .  
  
|Название|Описание|  
|----------|-----------------|  
|**Активные шаги**|Этот счетчик сообщает о текущем количестве выполняющихся шагов заданий.|  
|**Шаги в очереди**|Этот счетчик сообщает о количестве шагов заданий, готовых к запуску, но еще не выполняющихся агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|**Общее количество попыток выполнить шаг**|Этот счетчик сообщает общее число повторных попыток [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запустить шаг задания с момента последнего перезапуска сервера.|  
  
 Каждый из счетчиков объекта содержит следующие экземпляры.  
  
|Экземпляр|Описание|  
|--------------|-----------------|  
|**_Total**|Сведения для всех шагов задания.|  
|**ActiveScripting**|Сведения о шагах задания, использующих подсистему **ActiveScripting** .|  
|**ANALYSISCOMMAND**|Сведения о шагах задания, использующих подсистему ANALYSISCOMMAND.|  
|**ANALYSISQUERY**|Сведения о шагах задания, использующих подсистему ANALYSISQUERY.|  
|**CmdExec**|Сведения о шагах задания, использующих подсистему **CmdExec** .|  
|**Distribution**|Сведения об шагах задания, использующих подсистему **Distribution** .|  
|**Dts**|Сведения о шагах задания, использующих подсистему [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
|**LogReader**|Сведения о шагах задания, использующих подсистему **LogReader** .|  
|**Объединить**|Сведения о шагах задания, использующих подсистему **Merge** .|  
|**PowerShell**|Сведения о шагах задания, использующих подсистему **PowerShell** .|  
|**QueueReader**|Сведения о шагах задания, использующих подсистему **QueueReader** .|  
|**Моментальный снимок**|Сведения о шагах задания, использующих подсистему **Snapshot** .|  
|**TSQL**|Сведения о шагах задания, выполняющих инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
  
## См. также:  
 [Управление шагами задания](../../ssms/agent/manage-job-steps.md)   
 [Использование объектов производительности](../../ssms/agent/use-performance-objects.md)   
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  