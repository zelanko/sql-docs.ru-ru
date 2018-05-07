---
title: sp_add_operator (Transact-SQL) | Документы Microsoft
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
- sp_add_operator
- sp_add_operator_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_operator
ms.assetid: 817cd98a-4dff-4ed8-a546-f336c144d1e0
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3821ebe0886dd5a731e0459f3da686125c02a71c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="spaddoperator-transact-sql"></a>sp_add_operator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает оператор (получатель уведомлений) для использования с предупреждениями и заданиями.  
  
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_add_operator [ @name = ] 'name'   
     [ , [ @enabled = ] enabled ]   
     [ , [ @email_address = ] 'email_address' ]   
     [ , [ @pager_address = ] 'pager_address' ]   
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
 [  **@name=** ] **"***имя***"**  
 Имя оператора (получателя уведомлений). Это имя должно быть уникальным и не может содержать символа процента (**%**) символов. *имя* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@enabled=** ] *включена*  
 Отображает текущее состояние оператора. *включить* — **tinyint**, значение по умолчанию **1** (включено). Если **0**, оператор не включен и не получает уведомлений.  
  
 [  **@email_address=** ] **"***email_address***"**  
 Адрес электронной почты оператора. Эта строка передается напрямую в систему электронной почты. *email_address* — **nvarchar(100)**, значение по умолчанию NULL.  
  
 Можно указать физический адрес электронной почты или псевдоним для *email_address*. Например:  
  
 "**jdoe**«или»**jdoe@xyz.com**"  
  
> [!NOTE]  
>  В компоненте Database Mail надо использовать адрес электронной почты.  
  
 [  **@pager_address=** ] **"***pager_address***"**  
 Адрес пейджера оператора. Эта строка передается напрямую в систему электронной почты. *pager_address* — **narchar(100)**, значение по умолчанию NULL.  
  
 [ **@weekday_pager_start_time=** ] *weekday_pager_start_time*  
 Время, по истечении которого агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отправляет уведомления на пейджер указанному оператору в рабочие дни недели (с понедельника по пятницу). *weekday_pager_start_time*— **int**, значение по умолчанию **090000**, которой соответствует 9:00 в 24-часовом формате и должно вводиться в формате ЧЧММСС.  
  
 [ **@weekday_pager_end_time=** ] *weekday_pager_end_time*  
 Время, после которого **SQLServerAgent** служба перестает посылать уведомления на пейджер указанному оператору в рабочие дни, с понедельника по пятницу. *weekday_pager_end_time*— **int**, значение по умолчанию 180000, которое соответствует 18:00. в 24-часовом формате и должно вводиться в формате ЧЧММСС.  
  
 [ **@saturday_pager_start_time =**] *saturday_pager_start_time*  
 Время, после которого **SQLServerAgent** служба отправляет уведомления на пейджер указанному оператору по субботам. *saturday_pager_start_time* — **int**, значение по умолчанию 090000, которое соответствует 9:00:00 в 24-часовом формате и должно вводиться в формате ЧЧММСС.  
  
 [ **@saturday_pager_end_time=** ] *saturday_pager_end_time*  
 Время, после которого **SQLServerAgent** служба перестает посылать уведомления на пейджер указанному оператору по субботам. *saturday_pager_end_time*— **int**, значение по умолчанию **180000**, указывающая на 18:00. в 24-часовом формате и должно вводиться в формате ЧЧММСС.  
  
 [  **@sunday_pager_start_time=** ] *sunday_pager_start_time*  
 Время, после которого **SQLServerAgent** служба отправляет уведомления на пейджер указанному оператору по воскресеньям. *sunday_pager_start_time*— **int**, значение по умолчанию **090000**, которой соответствует 9:00 в 24-часовом формате и должно вводиться в формате ЧЧММСС.  
  
 [ **@sunday_pager_end_time =**] *sunday_pager_end_time*  
 Время, после которого **SQLServerAgent** служба перестает посылать уведомления на пейджер указанному оператору по воскресеньям. *sunday_pager_end_time*— **int**, значение по умолчанию **180000**, указывающая на 18:00. в 24-часовом формате и должно вводиться в формате ЧЧММСС.  
  
 [  **@pager_days=** ] *pager_days*  
 Число, указывающее дни, в которые оператор доступен для сообщений на пейджер (с учетом времени начала/конца работы). *pager_days*— **tinyint**, значение по умолчанию **0** означает, что оператор доступен никогда не пейджинговых сообщений. Допустимые значения: от **0** через **127**. *pager_days*рассчитывается путем сложения отдельных значений для требуемых дней. Например, с понедельника по пятницу — **2**+**4**+**8**+**16** + **32** = **62**. В следующей таблице перечислены значения для каждого дня недели.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Воскресенье|  
|**2**|Понедельник|  
|**4**|Вторник|  
|**8**|Среда|  
|**16**|Четверг|  
|**32**|Пятница|  
|**64**|Суббота|  
  
 [  **@netsend_address=** ] **"***netsend_address***"**  
 Сетевой адрес оператора, которому посылается сетевое сообщение. *netsend_address*— **nvarchar(100)**, значение по умолчанию NULL.  
  
 [  **@category_name=** ] **"***категории***"**  
 Имя категории этого оператора. *Категория* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 **sp_add_operator** должна запускаться из **msdb** базы данных.  
  
 Отправка сообщений на пейджер поддерживается системой электронной почты, в которой должна быть функция отправки пейджинговых сообщений через электронную почту.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] обеспечивает доступный графический способ управления заданиями и рекомендуется для создания и управления инфраструктурой заданий.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_add_operator**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере задаются сведения об операторе для `danwi`. Оператор активен. Агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отправляет уведомления на пейджер с понедельника по пятницу с 8:00 до 17:00.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_operator  
    @name = N'Dan Wilson',  
    @enabled = 1,  
    @email_address = N'danwi',  
    @pager_address = N'5551290AW@pager.Adventure-Works.com',  
    @weekday_pager_start_time = 080000,  
    @weekday_pager_end_time = 170000,  
    @pager_days = 62 ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_delete_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)   
 [Хранимая процедура sp_help_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_update_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
