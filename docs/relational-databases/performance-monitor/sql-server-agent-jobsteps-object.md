---
title: SQL Server, объект JobSteps | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- JobSteps object
- SQLAgent:JobSteps
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 753c7c08164de1583dd8de1aa1720fcad6a98dff
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68093632"
---
# <a name="sql-server-agent-jobsteps-object"></a>Агент SQL Server, объект JobSteps
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Объект производительности агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**JobSteps** содержит счетчики производительности, сообщающие сведения о шагах задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В следующей таблице перечислены счетчики этого объекта.  
  
 В следующей таблице представлены счетчики **SQLAgent:JobSteps** .  
  
|Имя|Description|  
|----------|-----------------|  
|**Активные шаги**|Этот счетчик сообщает о текущем количестве выполняющихся шагов заданий.|  
|**Шаги в очереди**|Этот счетчик сообщает о количестве шагов заданий, готовых к запуску, но еще не выполняющихся агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|**Общее количество попыток выполнить шаг**|Этот счетчик сообщает общее число повторных попыток [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запустить шаг задания с момента последнего перезапуска сервера.|  
  
 Каждый из счетчиков объекта содержит следующие экземпляры.  
  
|Экземпляр|Description|  
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
 [Управление шагами задания](../../ssms/agent/manage-job-steps.md)   
 [Использование объектов производительности](../../ssms/agent/use-performance-objects.md)   
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
