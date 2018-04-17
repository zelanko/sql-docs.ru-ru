---
title: Базы данных в таблицы плана обслуживания (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- database maintenance plans [SQL Server]
- maintenance plans [SQL Server], system tables
- system tables [SQL Server], database maintenance plans
ms.assetid: f264554c-5514-4df2-aadb-6dcdc2dfcfea
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cc48ab97d774583f9a9e25edd2cc55c9f2758957
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="database-maintenance-plan-tables-transact-sql"></a>Таблицы плана обслуживания базы данных (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Подразделы данного раздела описывают системные таблицы, хранящие данные, используемые планами обслуживания баз данных. Эти таблицы хранят данные об экземплярах, обновленных из предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
## <a name="in-this-section"></a>В этом разделе  
 [sysdbmaintplan_databases](../../relational-databases/system-tables/sysdbmaintplan-databases-transact-sql.md)  
 Содержит по одной строке для каждой базы данных, которая имеет соответствующий обновленный план обслуживания базы данных.  
  
 [sysdbmaintplan_history](../../relational-databases/system-tables/sysdbmaintplan-history-transact-sql.md)  
 Содержит по одной строке для каждого выполненного действия обновленного плана обслуживания базы данных.  
  
 [sysdbmaintplan_jobs](../../relational-databases/system-tables/sysdbmaintplan-jobs-transact-sql.md)  
 Содержит по одной строке для каждого задания обновленного плана обслуживания базы данных.  
  
 [sysdbmaintplans](../../relational-databases/system-tables/sysdbmaintplans-transact-sql.md)  
 Содержит по одной строке для каждого обновленного плана обслуживания базы данных.  
  
## <a name="see-also"></a>См. также  
 [Планы обслуживания](../../relational-databases/maintenance-plans/maintenance-plans.md)  
  
  
