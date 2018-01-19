---
title: "KILL STATS JOB (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- KILL STATS JOB
- KILL_STATS_JOB_TSQL
dev_langs: TSQL
helpviewer_keywords:
- ending statistics update jobs [SQL Server]
- stopping statistics update jobs
- terminating statistics update jobs
- asynchronous statistics updates [SQL Server]
- KILL STATS JOB statement
- statistics update jobs [SQL Server]
ms.assetid: 55a8f9f1-3259-45c0-8ab9-60b9c088b4b4
caps.latest.revision: "18"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2df18cfd1e0803fb937965ecc6c5880614e25df2
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/19/2018
---
# <a name="kill-stats-job-transact-sql"></a>KILL STATS JOB (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Завершает асинхронное задание обновления статистики в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
KILL STATS JOB job_id   
```  
  
## <a name="arguments"></a>Аргументы  
 *job_id*  
 Аргумент job_id, возвращаемый динамическим административным представлением sys.dm_exec_background_job_queue для этого задания.  
  
## <a name="remarks"></a>Remarks  
 Аргумент job_id не имеет отношения к идентификатору сеанса (session_id) или другим единицам работы, используемым в разных формах оператора KILL.  
  
## <a name="permissions"></a>Разрешения  
 У пользователя должно быть разрешение VIEW SERVER STATE для доступа к сведениям в динамическом административном представлении sys.dm_exec_background_job_queue.  
  
 Разрешения KILL STATS JOB присваиваются по умолчанию членам предопределенных ролей баз данных sysadmin и processadmin и не могут передаваться.  
  
## <a name="examples"></a>Примеры  
 Следующий пример показывает, как остановить обновление статистики, связанное с заданием, где *job_id* = `53`.  
  
```  
KILL STATS JOB 53;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [KILL &#40; Transact-SQL &#41;](../../t-sql/language-elements/kill-transact-sql.md)   
 [KILL QUERY NOTIFICATION SUBSCRIPTION &#40; Transact-SQL &#41;](../../t-sql/language-elements/kill-query-notification-subscription-transact-sql.md)   
 [sys.dm_exec_background_job_queue &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-background-job-queue-transact-sql.md)   
 [Статистика](../../relational-databases/statistics/statistics.md)  
  
  
