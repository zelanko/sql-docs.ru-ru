---
title: Использование объектов производительности | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
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
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 7e5b353725cda984a65cbbbb35878c6d79ae4bb5
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51698972"
---
# <a name="use-performance-objects"></a>Использование объектов производительности
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент включает объекты и счетчики производительности, позволяющие отслеживать работу служб. Эти объекты производительности дают возможность использования системного монитора, средства Windows для определения задач, выполняемых службой агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в фоновом режиме. Например, можно узнать, сколько активных заданий запущено в данный момент в службе агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , и определить заблокированные задания.  
  
Объекты и счетчики производительности службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предусмотрены для каждого установленного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Имена объектам производительности присваиваются в соответствии с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые они представляют.  
  
В следующей таблице содержатся правила именования объектов производительности службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Тип экземпляра|Имя объекта|  
|-----------------|---------------|  
|По умолчанию|**SQLAgent:**_объект_:_счетчик_|  
|Именованный|**SQLAgent$**<br /> **&#42;имя_экземпляра&#42; :**_объект_:_счетчик_|  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит следующие объекты производительности для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Имя объекта|Описание|  
|---------------|---------------|  
|[SQLAgent:Jobs](../../relational-databases/performance-monitor/sql-server-agent-jobs-object.md)|Сведения о производительности запущенных заданий, проценте успешных попыток и текущем состоянии.|  
|[SQLAgent:JobSteps](../../relational-databases/performance-monitor/sql-server-agent-jobsteps-object.md)|Сведения о состоянии шагов заданий.|  
|[SQLAgent:Alerts](../../relational-databases/performance-monitor/sql-server-agent-alerts-object.md)|Сведения о количестве предупреждений и уведомлений.|  
|[SQLAgent:Statistics](../../relational-databases/performance-monitor/sql-server-agent-statistics-object.md)|Общие сведения о производительности.|  
  
## <a name="see-also"></a>См. также:  
[Наблюдение и настройка производительности](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
[Практическое руководство. Запуск системного монитора (Windows)](https://msdn.microsoft.com/5e51bb79-5737-470b-9c47-fac330c001c5)  
  
