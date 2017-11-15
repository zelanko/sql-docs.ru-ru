---
title: "SQL Server, объект JobSteps | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JobSteps object
- SQLAgent:JobSteps
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
caps.latest.revision: "23"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1cf950d708d527bdd8199fa39f132410b0c8d699
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="sql-server-agent-jobsteps-object"></a>Агент SQL Server, объект JobSteps
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
  
## <a name="see-also"></a>См. также:  
 [Управление шагами задания](http://msdn.microsoft.com/library/51352afc-a0a4-428b-8985-f9e58bb57c31)   
 [Использование объектов производительности](http://msdn.microsoft.com/library/830b843a-6b2a-4620-a51b-98358e9fc54b)   
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
