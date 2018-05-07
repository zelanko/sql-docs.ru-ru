---
title: sp_update_operator (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_update_operator_TSQL
- sp_update_operator
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_operator
ms.assetid: 231750a6-4828-4d03-afe6-b91d38c42ed3
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9f0cdd4e69655ac469e875b37f3e299b89b1be2f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="spupdateoperator-transact-sql"></a>sp_update_operator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Обновляет данные об операторе (получателе уведомлений) для организации оповещений и заданий.  
  
   ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_update_operator   
     [ @name =] 'name'   
     [ , [ @new_name = ] 'new_name' ]   
     [ , [ @enabled = ] enabled]   
     [ , [ @email_address = ] 'email_address' ]  
     [ , [ @pager_address = ] 'pager_number']   
     [ , [ @weekday_pager_start_time = ] weekday_pager_start_time ]  
     [ , [ @weekday_pager_end_time = ] weekday_pager_end_time ]   
     [ , [ @saturday_pager_start_time = ] saturday_pager_start_time ]  
     [ , [ @saturday_pager_end_time = ] saturday_pager_end_time ]   
     [ , [ @sunday_pager_start_time = ] sunday_pager_start_time ]  
     [ , [ @sunday_pager_end_time = ] sunday_pager_end_time ]   
     [ , [ @pager_days = ] pager_days ]   
     [ , [ @netsend_address = ] 'netsend_address' ]   
     [ , [ @category_name = ] 'category' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @name=] '*имя*"  
 Имя оператора для изменения. *имя* — **sysname**, не имеет значения по умолчанию.  
  
 [ @new_name=] '*новое_имя*"  
 Новое имя оператора. Имя должно быть уникальным. *новое_имя* — **sysname**, значение по умолчанию NULL.  
  
 [ @enabled=] *включена*  
 Число, указывающее текущее состояние оператора (**1** включенный в настоящее время **0** в противном случае). *включить* — **tinyint**, значение по умолчанию NULL. Если оператор не включен, он не будет получать предупреждающих оповещений.  
  
 [ @email_address=] '*email_address*"  
 Адрес электронной почты оператора. Эта строка передается напрямую в систему электронной почты. *email_address* — **nvarchar(100)**, значение по умолчанию NULL.  
  
 [ @pager_address=] '*pager_number*"  
 Адрес пейджера оператора. Эта строка передается напрямую в систему электронной почты. *pager_number* — **nvarchar(100)**, значение по умолчанию NULL.  
  
 [ @weekday_pager_start_time=] *weekday_pager_start_time*  
 Указывает время, по истечении которого на пейджер указанному оператору может быть отправлено оповещение (с понедельника по пятницу). *weekday_pager_start_time*— **int**, значение по умолчанию NULL и должны вводиться в формате ЧЧММСС с использованием 24-часового формата времени.  
  
 [ @weekday_pager_end_time=] *weekday_pager_end_time*  
 Указывает время, по истечении которого на пейджер указанному оператору не может быть отправлено оповещение (с понедельника по пятницу). *weekday_pager_end_time*— **int**, значение по умолчанию NULL и должны вводиться в формате ЧЧММСС с использованием 24-часового формата времени.  
  
 [ @saturday_pager_start_time=] *saturday_pager_start_time*  
 Указывает время, по истечении которого на пейджер указанному оператору может быть отправлено оповещение (по субботам). *saturday_pager_start_time*— **int**, значение по умолчанию NULL и должны вводиться в формате ЧЧММСС с использованием 24-часового формата времени.  
  
 [ @saturday_pager_end_time=] *saturday_pager_end_time*  
 Указывает время, по истечении которого на пейджер указанному оператору не может быть отправлено оповещение (по субботам). *saturday_pager_end_time*— **int**, значение по умолчанию NULL и должны вводиться в формате ЧЧММСС с использованием 24-часового формата времени.  
  
 [ @sunday_pager_start_time=] *sunday_pager_start_time*  
 Указывает время, по истечении которого на пейджер указанному оператору может быть отправлено оповещение (по воскресеньям). *sunday_pager_start_time*— **int**, значение по умолчанию NULL и должны вводиться в формате ЧЧММСС с использованием 24-часового формата времени.  
  
 [ @sunday_pager_end_time=] *sunday_pager_end_time*  
 Указывает время, по истечении которого на пейджер указанному оператору не может быть отправлено оповещение (по воскресеньям). *sunday_pager_end_time*— **int**, значение по умолчанию NULL и должны вводиться в формате ЧЧММСС с использованием 24-часового формата времени.  
  
 [ @pager_days=] *pager_days*  
 Указывает дни, в которые оператор доступен для приема сообщений на пейджер (с учетом времени начала и конца работы). *pager_days*— **tinyint**, значение по умолчанию NULL, и должен быть числом от **0** через **127**. *pager_days* рассчитывается путем сложения отдельных значений для требуемых дней. Например, с понедельника по пятницу — **2**+**4**+**8**+**16** + **32** = **64**.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Воскресенье|  
|**2**|Понедельник|  
|**4**|Вторник|  
|**8**|Среда|  
|**16**|Четверг|  
|**32**|Пятница|  
|**64**|Суббота|  
  
 [ @netsend_address=] '*netsend_address*"  
 Сетевой адрес оператора, которому посылается сетевое сообщение. *netsend_address*— **nvarchar(100)**, значение по умолчанию NULL.  
  
 [ @category_name=] '*категории*"  
 Имя категории предупреждения. *Категория* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Инструкцию sp_update_operator нужно выполнять из базы данных msdb.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения на выполнение этой процедуры предоставляются членам предопределенной роли сервера sysadmin.  
  
## <a name="examples"></a>Примеры  
 В следующем примере состояние оператора изменяется на «включен» и назначается время (с понедельника по пятницу, с 8 до 17 часов), когда оператору можно передавать сообщения.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_operator   
    @name = N'François Ajenstat',  
    @enabled = 1,  
    @email_address = N'françoisa',  
    @pager_address = N'5551290AW@pager.Adventure-Works.com',  
    @weekday_pager_start_time = 080000,  
    @weekday_pager_end_time = 170000,  
    @pager_days = 64 ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_delete_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)   
 [Хранимая процедура sp_help_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
