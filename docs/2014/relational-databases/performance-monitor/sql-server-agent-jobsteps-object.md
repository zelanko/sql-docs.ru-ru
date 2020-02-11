---
title: SQL Server, объект JobSteps | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- JobSteps object
- SQLAgent:JobSteps
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 323bf0c943d12a2d05e5fde80194d35d9ab733cf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68206564"
---
# <a name="sql-server-agent-jobsteps-object"></a>Агент SQL Server, объект JobSteps
  Объект производительности агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**JobSteps** содержит счетчики производительности, сообщающие сведения о шагах задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В следующей таблице перечислены счетчики этого объекта.  
  
 В следующей таблице представлены счетчики **SQLAgent:JobSteps** .  
  
|Имя|Description|  
|----------|-----------------|  
|**Активные шаги**|Этот счетчик сообщает о текущем количестве выполняющихся шагов заданий.|  
|**Шаги в очереди**|Этот счетчик сообщает о количестве шагов заданий, готовых к запуску, но еще не выполняющихся агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|**Всего повторных попыток**|Этот счетчик сообщает общее число [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] повторных попыток выполнения шага задания с момента последнего перезапуска сервера.|  
  
 Каждый из счетчиков объекта содержит следующие экземпляры.  
  
|Экземпляр|Description|  
|--------------|-----------------|  
|**_Total**|Сведения для всех шагов задания.|  
|**ActiveScripting**|Сведения о шагах задания, использующих подсистему **ActiveScripting** .|  
|**ANALYSISCOMMAND**|Сведения о шагах задания, использующих подсистему ANALYSISCOMMAND.|  
|**ANALYSISQUERY**|Сведения о шагах задания, использующих подсистему ANALYSISQUERY.|  
|**CmdExec**|Сведения о шагах задания, использующих подсистему **CmdExec** .|  
|**Distribution**|Сведения об шагах задания, использующих подсистему **Distribution** .|  
|**Через**|Сведения о шагах задания, использующих подсистему [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
|**Модуля**|Сведения о шагах задания, использующих подсистему **LogReader** .|  
|**AutoMerge**|Сведения о шагах задания, использующих подсистему **Merge** .|  
|**PowerShell**|Сведения о шагах задания, использующих подсистему **PowerShell** .|  
|**QueueReader**|Сведения о шагах задания, использующих подсистему **QueueReader** .|  
|**Моментальный снимок**|Сведения о шагах задания, использующих подсистему **Snapshot** .|  
|**TSQL**|Сведения о шагах задания, выполняющих инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
  
## <a name="see-also"></a>См. также:  
 [Управление шагами заданий](../../ssms/agent/manage-job-steps.md)   
 [Использование объектов производительности](../../ssms/agent/use-performance-objects.md)   
 [Мониторинг использования ресурсов &#40;системном мониторе&#41;](monitor-resource-usage-system-monitor.md)  
  
  
