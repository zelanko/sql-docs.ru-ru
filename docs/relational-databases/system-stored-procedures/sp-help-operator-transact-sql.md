---
title: Хранимая процедура sp_help_operator (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_operator
- sp_help_operator_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_operator
ms.assetid: caedc43d-44b8-415a-897e-92923f6de3b8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 48d70126d071879754011fed7342d03dd72185a5
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58534386"
---
# <a name="sphelpoperator-transact-sql"></a>Хранимая процедура sp_help_operator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет сведения об определенных для сервера операторах.  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_operator  
     { [ @operator_name = ] 'operator_name'   
     | [ @operator_id = ] operator_id }  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @operator_name = ] 'operator_name'` Имя оператора. *имя_оператора* — **sysname**. Если *имя_оператора* является не указан, возвращаются сведения обо всех операторах.  
  
`[ @operator_id = ] operator_id` Идентификационный номер оператора, для которого запрашиваются сведения. *operator_id*— **int**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Либо *operator_id* или *имя_оператора* должен быть указан, но не оба аргумента одновременно.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификационный номер оператора.|  
|**name**|**sysname**|Имя оператора.|  
|**включен**|**tinyint**|Доступность оператора для получения уведомлений:<br /><br /> **1** = Да<br /><br /> **0** = Нет|  
|**email_address**|**nvarchar(100)**|Адрес электронной почты оператора.|  
|**last_email_date**|**int**|Дата, когда оператор получил последнее уведомление по электронной почте.|  
|**last_email_time**|**int**|Время, когда оператор получил последнее уведомление по электронной почте.|  
|**pager_address**|**nvarchar(100)**|Адрес пейджера оператора.|  
|**last_pager_date**|**int**|Дата, когда оператор получил последнее уведомление по пейджеру.|  
|**last_pager_time**|**int**|Время, когда оператор получил последнее уведомление по пейджеру.|  
|**weekday_pager_start_time**|**int**|Время начала периода, в течение которого оператор доступен для уведомлений по пейджеру в рабочие дни.|  
|**weekday_pager_end_time**|**int**|Время окончания периода, в течение которого оператор доступен для уведомлений по пейджеру в рабочие дни.|  
|**saturday_pager_start_time**|**int**|Время начала периода, в течение которого оператор доступен для уведомлений по пейджеру по субботам.|  
|**saturday_pager_end_time**|**int**|Время окончания периода, в течение которого оператор доступен для уведомлений по пейджеру по субботам.|  
|**sunday_pager_start_time**|**int**|Время начала периода, в течение которого оператор доступен для уведомлений по пейджеру по воскресеньям.|  
|**sunday_pager_end_time**|**int**|Время окончания периода, в течение которого оператор доступен для уведомлений по пейджеру по воскресеньям.|  
|**pager_days**|**tinyint**|Битовая маска (**1** = воскресенье, **64** = суббота) дней недели, указывающее, когда оператор доступен для уведомлений по пейджеру.|  
|**netsend_address**|**nvarchar(100)**|Адрес оператора для всплывающих сетевых уведомлений.|  
|**last_netsend_date**|**int**|Дата, когда оператор получил последнее всплывающее сетевое уведомление.|  
|**last_netsend_time**|**int**|Время, когда оператор получил последнее всплывающее сетевое уведомление.|  
|**category_name**|**sysname**|Имя категории операторов, к которой принадлежит этот оператор.|  
  
## <a name="remarks"></a>Примечания  
 **Хранимая процедура sp_help_operator** должна запускаться из **msdb** базы данных.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="examples"></a>Примеры  
 Следующий пример предоставляет сведения об операторе `François Ajenstat`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_operator  
    @operator_name = N'François Ajenstat' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_delete_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)   
 [sp_update_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
