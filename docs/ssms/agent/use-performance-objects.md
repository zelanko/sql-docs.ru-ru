---
title: Использование объектов производительности | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d5033120057e83f6fd155466a35188be04068ef6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="use-performance-objects"></a>Использование объектов производительности
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Агент включает объекты и счетчики производительности, позволяющие отслеживать работу служб. Эти объекты производительности дают возможность использования системного монитора, средства Windows для определения задач, выполняемых службой агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] в фоновом режиме. Например, можно узнать, сколько активных заданий запущено в данный момент в службе агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , и определить заблокированные задания.  
  
Объекты и счетчики производительности службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] предусмотрены для каждого установленного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . Имена объектам производительности присваиваются в соответствии с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , которые они представляют.  
  
В следующей таблице содержатся правила именования объектов производительности службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
|Тип экземпляра|Имя объекта|  
|-----------------|---------------|  
|По умолчанию|**SQLAgent:***объект*:*счетчик*|  
|Именованный|**SQLAgent$**<br /> **&#42;имя_экземпляра&#42; :***объект*:*счетчик*|  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] содержит следующие объекты производительности для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
|Имя объекта|Description|  
|---------------|---------------|  
|[SQLAgent:Jobs](http://msdn.microsoft.com/en-us/225b5e2d-4a78-4178-b2b6-b419df83c4aa)|Сведения о производительности запущенных заданий, проценте успешных попыток и текущем состоянии.|  
|[SQLAgent:JobSteps](http://msdn.microsoft.com/en-us/44f9983c-1753-4fe0-8475-973aa2460b3a)|Сведения о состоянии шагов заданий.|  
|[SQLAgent:Alerts](http://msdn.microsoft.com/en-us/e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a)|Сведения о количестве предупреждений и уведомлений.|  
|[SQLAgent:Statistics](http://msdn.microsoft.com/en-us/ebe92bfa-0721-48aa-9ba6-e7904ad265a1)|Общие сведения о производительности.|  
  
## <a name="see-also"></a>См. также:  
[Наблюдение и настройка производительности](http://msdn.microsoft.com/en-us/87f23f03-0f19-4b2e-bfae-efa378f7a0d4)  
[Практическое руководство. Запуск системного монитора (Windows)](http://msdn.microsoft.com/en-us/5e51bb79-5737-470b-9c47-fac330c001c5)  
  
