---
title: "dbo.sysjobhistory (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/03/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.sysjobhistory_TSQL
- dbo.sysjobhistory
- sysjobhistory
- sysjobhistory_TSQL
dev_langs: TSQL
helpviewer_keywords: sysjobhistory system table
ms.assetid: 1b1fcdbb-2af2-45e6-bf3f-e8279432ce13
caps.latest.revision: "21"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 63d461ff997a9a438965e039a727999876b3d7a3
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysjobhistory-transact-sql"></a>dbo.sysjobhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит сведения о выполнении назначенных заданий агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта таблица хранится в **msdb** базы данных.  
  
> **Примечание:** данные обновляются только после завершения этапов задания.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|Уникальный идентификатор строки.|  
|**Аргумент job_id**|**uniqueidentifier**|Идентификатор задания.|  
|**step_id**|**int**|Идентификатор этапа в задании.|  
|**step_name**|**sysname**|Имя этапа.|  
|**sql_message_id**|**int**|Идентификатор любого сообщения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] об ошибке, возвращенного при сбое задания.|  
|**sql_severity**|**int**|Уровень серьезности любой ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Сообщение**|**nvarchar(4000)**|Текст ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если он имеется.|  
|**run_status**|**int**|Состояние выполнения задания.<br /><br /> **0** = ошибка<br /><br /> **1** = выполнено успешно<br /><br /> **2** = Повтор<br /><br /> **3** = отменено|  
|**run_date**|**int**|Дата начала выполнения задания или этапа. Для внутрипроцессного журнала это дата и время записи журнала.|  
|**run_time**|**int**|Время запуска задания или этапа.|  
|**run_duration**|**int**|Время, затраченное на выполнение задания или этапа в **ЧЧММСС** формат.|  
|**operator_id_emailed**|**int**|Идентификатор оператора, уведомленного о завершении задания.|  
|**operator_id_netsent**|**int**|Идентификатор оператора, уведомленного при помощи сообщения о завершении задания.|  
|**operator_id_paged**|**int**|Идентификатор оператора, уведомленного по пейджеру о завершении задания.|  
|**retries_attempted**|**int**|Количество повторных попыток выполнения задания или этапа.|  
|**сервер**|**sysname**|Имя сервера, на котором выполнялось задание.|  
  
  ## <a name="example"></a>Пример
 Следующие [!INCLUDE[tsql](../../includes/tsql-md.md)] преобразует запрос **run_time** и **run_duration** столбцы в формате более понятное для пользователя.  Выполнение скрипта в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].
 
 ```tsql
 SET NOCOUNT ON;
 
 SELECT sj.name,
        sh.run_date,
        sh.step_name,
        STUFF(STUFF(RIGHT(REPLICATE('0', 6) +  CAST(sh.run_time as varchar(6)), 6), 3, 0, ':'), 6, 0, ':') 'run_time',
        STUFF(STUFF(STUFF(RIGHT(REPLICATE('0', 8) + CAST(sh.run_duration as varchar(8)), 8), 3, 0, ':'), 6, 0, ':'), 9, 0, ':') 'run_duration (DD:HH:MM:SS)  '
FROM msdb.dbo.sysjobs sj
JOIN msdb.dbo.sysjobhistory sh
ON sj.job_id = sh.job_id
```
