---
title: "sp_help_targetserver (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_targetserver_TSQL
- sp_help_targetserver
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_targetserver
ms.assetid: f841d3bd-901a-4980-ad0b-1c6eeba3f717
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c45b6bc34b8003d78cd60916b9db22557fb0f4b1
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sphelptargetserver-transact-sql"></a>sp_help_targetserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Список всех целевых серверов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_targetserver   
     [ [ @server_name = ] 'server_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@server_name=** ] **'***server_name***'**  
 Имя сервера, сведения о котором требуются. *имя_сервера* — **nvarchar(30)**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Если *имя_сервера* не указан, **sp_help_targetserver** возвращает следующий результирующий набор.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Идентификационный номер сервера.|  
|**server_name**|**nvarchar(30)**|Имя сервера.|  
|**расположение**|**nvarchar(200)**|Расположение указанного сервера.|  
|**time_zone_adjustment**|**int**|Настройка временной зоны в часах, от среднего времени по Гринвичу.|  
|**enlist_date**|**datetime**|Дата прикрепления указанного сервера.|  
|**last_poll_date**|**datetime**|Дата последнего опроса сервером заданий.|  
|**status**|**int**|Состояние указанного сервера.|  
|**unread_instructions**|**int**|Наличие на сервере непрочитанных инструкций. Если все строки были загружены, этот столбец имеет **0**.|  
|**local_time**|**datetime**|Локальная дата и время на целевом сервере, которые основаны на локальном времени целевого сервера после последнего опроса главного сервера.|  
|**enlisted_by_nt_user**|**nvarchar(100)**|Пользователь Microsoft Windows, который прикрепил целевой сервер.|  
|**poll_interval**|**int**|Частота в секундах, с которой целевой сервер опрашивает службу Master SQLServerAgent, чтобы загрузить задания и выгрузить состояние заданий.|  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой хранимой процедуры пользователь должен быть членом предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-information-for-all-registered-target-servers"></a>A. Вывод сведений обо всех зарегистрированных целевых серверах  
 Следующий пример выводит сведения обо всех зарегистрированных целевых серверах.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_targetserver ;  
GO  
```  
  
### <a name="b-listing-information-for-a-specific-target-server"></a>Б. Вывод сведений об указанном целевом сервере  
 Следующий пример выводит сведения о целевом сервере `SEATTLE2`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_targetserver N'SEATTLE2' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_targetservergroup &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql.md)   
 [sp_delete_targetserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql.md)   
 [sp_delete_targetservergroup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql.md)   
 [sp_update_targetservergroup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql.md)   
 [dbo.sysdownloadlist &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-sysdownloadlist-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
