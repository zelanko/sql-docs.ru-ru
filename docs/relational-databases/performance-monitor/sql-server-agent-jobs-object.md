---
title: "Объект заданий (агент SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLAgent:Jobs
- Jobs object
ms.assetid: 225b5e2d-4a78-4178-b2b6-b419df83c4aa
caps.latest.revision: "21"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 077245e1ece089fa0a0b4ef98f2dd1fa6b9ec0d9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sql-server-agent-jobs-object"></a>Агент SQL Server, объект Jobs
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Объект производительности **Задания** агента SQL Server содержит счетчики производительности, сообщающие сведения о заданиях агента SQL Server. В следующей таблице перечислены счетчики этого объекта.  
  
 Приведенная ниже таблица содержит счетчики объекта **SQLAgent:Jobs** .  
  
|Название|Описание|  
|----------|-----------------|  
|**Активные задания**|Данный счетчик отображает количество выполняемых в данный момент заданий.|  
|**Невыполненные задания**|Этот счетчик отображает количество заданий, завершенных с ошибкой.|  
|**Эффективность выполнения заданий**|Этот счетчик отображает процентное соотношение успешно завершенных заданий от общего количества выполняемых заданий.|  
|**Задания, запускаемые за минуту**|Данный счетчик отображает количество заданий, запущенных в течение последней минуты.|  
|**Задания в очереди**|Данный счетчик отображает количество заданий, готовых к выполнению агентом SQL Server, но еще не запущенных.|  
|**Успешно выполненные задания**|Данный счетчик отображает количество успешно завершенных заданий.|  
  
 Каждый из счетчиков объекта содержит следующие экземпляры.  
  
|Экземпляр|Описание|  
|--------------|-----------------|  
|**_Total**|Сведения обо всех заданиях.|  
|**Предупреждения**|Сведения о заданиях, запущенных по предупреждению.|  
|**Прочие**|Сведения о заданиях, запущенных не по предупреждению и не по расписанию. Обычно это задания, запущенные вручную с помощью процедуры **sp_start_job**.|  
|**Расписания**|Сведения о заданиях, запущенных по расписанию.|  
  
## <a name="see-also"></a>См. также:  
 [Реализация заданий](http://msdn.microsoft.com/library/69e06724-25c7-4fb3-8a5b-3d4596f21756)   
 [Использование объектов производительности](http://msdn.microsoft.com/library/830b843a-6b2a-4620-a51b-98358e9fc54b)   
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
