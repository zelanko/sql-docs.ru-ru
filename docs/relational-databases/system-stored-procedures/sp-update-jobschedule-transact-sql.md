---
title: "sp_update_jobschedule (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_update_jobschedule_TSQL
- sp_update_jobschedule
dev_langs: TSQL
helpviewer_keywords: sp_update_jobschedule
ms.assetid: 4df02594-4cd1-49a9-8d97-37c44e4d5423
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 20487d3c9983fffc2cb15f3ef2df7944fd647f39
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="spupdatejobschedule-transact-sql"></a>sp_update_jobschedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет настройки расписания для указанного задания.  
  
 **sp_update_jobschedule** предоставляется только для обратной совместимости.  
  
> [!IMPORTANT]  
>  Дополнительные сведения о синтаксисе, используемом в более ранних версиях Microsoft SQL Server см. в разделе Transact-SQL Referencefor Microsoft SQL Server 2000*.*  
  
## <a name="remarks"></a>Замечания  
 Расписанием задач теперь можно управлять независимо от них самих. Чтобы обновить расписание, используйте **sp_update_schedule**.  
  
## <a name="permissions"></a>Permissions  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Только члены **sysadmin** можно использовать эту хранимую процедуру для обновления расписаний заданий, принадлежащих другим пользователям.  
  
## <a name="see-also"></a>См. также:  
 [Агент SQL Server хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_update_schedule &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-update-schedule-transact-sql.md)  
  
  
