---
title: Использование объектов производительности | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, monitoring
- SQL Server Agent service, monitoring
- SQL Server Agent service, performance objects
- SQL Server Agent, performance objects
- performance objects [SQL Server Agent]
- monitoring [SQL Server], SQL Server Agent
- monitoring [SQL Server Agent]
- performance counters [SQL Server], SQL Server Agent
- counters [SQL Server], SQL Server Agent
ms.assetid: 830b843a-6b2a-4620-a51b-98358e9fc54b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2ccba43aa28cadef1995fab001f66e1f4bebacde
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63245851"
---
# <a name="use-performance-objects"></a>Использование объектов производительности
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Агент включает объекты и счетчики производительности для отслеживания работы службы. Эти объекты производительности дают возможность использования системного монитора, средства Windows для определения задач, выполняемых службой агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в фоновом режиме. Например, можно узнать, сколько активных заданий запущено в данный момент в службе агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , и определить заблокированные задания.  
  
 Объекты и счетчики производительности службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предусмотрены для каждого установленного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Имена объектам производительности присваиваются в соответствии с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые они представляют.  
  
 В следующей таблице содержатся правила именования объектов производительности службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Тип экземпляра|Имя объекта|  
|-------------------|-----------------|  
|По умолчанию|**** *Объект объекта*:*Счетчик*|  
|именованная|**SQLAgent$**<br /> ***instance_name* :** *объект*:*Counter*|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]включает следующие объекты производительности для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента.  
  
|Имя объекта|Description|  
|-----------------|-----------------|  
|[SQLAgent:Jobs](../../relational-databases/performance-monitor/sql-server-agent-jobs-object.md)|Сведения о производительности запущенных заданий, проценте успешных попыток и текущем состоянии.|  
|[А: JobSteps](../../relational-databases/performance-monitor/sql-server-agent-jobsteps-object.md)|Сведения о состоянии шагов заданий.|  
|[А: оповещения](../../relational-databases/performance-monitor/sql-server-agent-alerts-object.md)|Сведения о количестве предупреждений и уведомлений.|  
|[Кадр: Статистика](../../relational-databases/performance-monitor/sql-server-agent-statistics-object.md)|Общие сведения о производительности.|  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение и настройка производительности](../../relational-databases/performance/monitor-and-tune-for-performance.md)   
 [Запуск системного монитора &#40;Windows&#41;](../../relational-databases/performance/start-system-monitor-windows.md)  
  
  
