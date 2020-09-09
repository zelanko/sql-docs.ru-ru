---
description: Хранимая процедура sp_help_operator (Transact-SQL)
title: sp_help_operator (Transact-SQL) | Документация Майкрософт
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2cbf7c84c22998b5ee7e43fadad6a42cf02d17b8
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89535476"
---
# <a name="sp_help_operator-transact-sql"></a>Хранимая процедура sp_help_operator (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Предоставляет сведения об определенных для сервера операторах.  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_operator  
     { [ @operator_name = ] 'operator_name'   
     | [ @operator_id = ] operator_id }  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @operator_name = ] 'operator_name'` Имя оператора. *operator_name* имеет тип **sysname**. Если параметр *operator_name* не указан, возвращаются сведения обо всех операторах.  
  
`[ @operator_id = ] operator_id` Идентификационный номер оператора, для которого запрашиваются сведения. *operator_id*имеет **тип int**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  Необходимо указать либо *operator_id* , либо *operator_name* , но нельзя указать оба значения.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификационный номер оператора.|  
|**name**|**sysname**|Имя оператора.|  
|**доступной**|**tinyint**|Доступность оператора для получения уведомлений:<br /><br /> **1** = Да<br /><br /> **0** = Нет|  
|**email_address**|**nvarchar (100)**|Адрес электронной почты оператора.|  
|**last_email_date**|**int**|Дата, когда оператор получил последнее уведомление по электронной почте.|  
|**last_email_time**|**int**|Время, когда оператор получил последнее уведомление по электронной почте.|  
|**pager_address**|**nvarchar (100)**|Адрес пейджера оператора.|  
|**last_pager_date**|**int**|Дата, когда оператор получил последнее уведомление по пейджеру.|  
|**last_pager_time**|**int**|Время, когда оператор получил последнее уведомление по пейджеру.|  
|**weekday_pager_start_time**|**int**|Время начала периода, в течение которого оператор доступен для уведомлений по пейджеру в рабочие дни.|  
|**weekday_pager_end_time**|**int**|Время окончания периода, в течение которого оператор доступен для уведомлений по пейджеру в рабочие дни.|  
|**saturday_pager_start_time**|**int**|Время начала периода, в течение которого оператор доступен для уведомлений по пейджеру по субботам.|  
|**saturday_pager_end_time**|**int**|Время окончания периода, в течение которого оператор доступен для уведомлений по пейджеру по субботам.|  
|**sunday_pager_start_time**|**int**|Время начала периода, в течение которого оператор доступен для уведомлений по пейджеру по воскресеньям.|  
|**sunday_pager_end_time**|**int**|Время окончания периода, в течение которого оператор доступен для уведомлений по пейджеру по воскресеньям.|  
|**pager_days**|**tinyint**|Битовая маска (**1** = воскресенье, **64** = Суббота) дней недели, указывающая, когда оператор доступен для получения уведомлений по пейджеру.|  
|**netsend_address**|**nvarchar (100)**|Адрес оператора для всплывающих сетевых уведомлений.|  
|**last_netsend_date**|**int**|Дата, когда оператор получил последнее всплывающее сетевое уведомление.|  
|**last_netsend_time**|**int**|Время, когда оператор получил последнее всплывающее сетевое уведомление.|  
|**category_name**|**sysname**|Имя категории операторов, к которой принадлежит этот оператор.|  
  
## <a name="remarks"></a>Примечания  
 **sp_help_operator** должны запускаться из базы данных **msdb** .  
  
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
  
## <a name="see-also"></a>См. также раздел  
 [sp_add_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_delete_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)   
 [sp_update_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
