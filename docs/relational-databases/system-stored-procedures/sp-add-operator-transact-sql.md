---
title: sp_add_operator (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_operator
- sp_add_operator_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_operator
ms.assetid: 817cd98a-4dff-4ed8-a546-f336c144d1e0
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 466cff492c5547357409cee1b11c7a6542971ae5
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85878687"
---
# <a name="sp_add_operator-transact-sql"></a>sp_add_operator (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

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
`[ @name = ] 'name'`Имя оператора (получателя уведомления). Это имя должно быть уникальным и не может содержать символ процента ( **%** ). Аргумент *Name* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @enabled = ] enabled`Указывает текущее состояние оператора. *Enabled* имеет тип **tinyint**и значение по умолчанию **1** (включено). Если значение **равно 0**, то оператор не включен и не получает уведомления.  
  
`[ @email_address = ] 'email_address'`Адрес электронной почты оператора. Эта строка передается напрямую в систему электронной почты. *email_address* имеет тип **nvarchar (100)** и значение по умолчанию NULL.  
  
 Можно указать либо физический адрес электронной почты, либо псевдоним для *email_address*. Пример:  
  
 "**jdoe**" или "**jdoe \@ XYZ.com**"  
  
> [!NOTE]  
>  В компоненте Database Mail надо использовать адрес электронной почты.  
  
`[ @pager_address = ] 'pager_address'`Адрес пейджера оператора. Эта строка передается напрямую в систему электронной почты. *pager_address* имеет тип **nvarchar (100)** и значение по умолчанию NULL.  
  
`[ @weekday_pager_start_time = ] weekday_pager_start_time`Время, по истечении которого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент отправляет уведомление по пейджеру указанному оператору в будним периоде с понедельника по пятницу. *weekday_pager_start_time*имеет **тип int**и значение по умолчанию **090000**, которое указывает на 9:00 утра. в 24-часовом формате и должно вводиться в формате ЧЧММСС.  
  
`[ @weekday_pager_end_time = ] weekday_pager_end_time`Время, по истечении которого служба **SQLServerAgent** больше не отправляет уведомление по пейджеру указанному оператору в будним периоде с понедельника по пятницу. *weekday_pager_end_time*имеет **тип int**и значение по умолчанию 180000, которое указывает на 6:00 вечера. в 24-часовом формате и должно вводиться в формате ЧЧММСС.  
  
`[ @saturday_pager_start_time = ] saturday_pager_start_time`Время, по истечении которого служба **SQLServerAgent** отправляет уведомление по пейджеру указанному оператору по субботам. *saturday_pager_start_time* имеет **тип int**и значение по умолчанию 090000, которое указывает на 9:00 утра. в 24-часовом формате и должно вводиться в формате ЧЧММСС.  
  
`[ @saturday_pager_end_time = ] saturday_pager_end_time`Время, после которого служба **SQLServerAgent** больше не отправляет уведомление по пейджеру указанному оператору в субботу. *saturday_pager_end_time*имеет **тип int**и значение по умолчанию **180000**, которое указывает на 6:00 вечера. в 24-часовом формате и должно вводиться в формате ЧЧММСС.  
  
`[ @sunday_pager_start_time = ] sunday_pager_start_time`Время, по истечении которого служба **SQLServerAgent** отправляет уведомление по пейджеру указанному оператору по воскресеньям. *sunday_pager_start_time*имеет **тип int**и значение по умолчанию **090000**, которое указывает на 9:00 утра. в 24-часовом формате и должно вводиться в формате ЧЧММСС.  
  
`[ @sunday_pager_end_time = ] sunday_pager_end_time`Время, после которого служба **SQLServerAgent** больше не отправляет уведомление по пейджеру указанному оператору по воскресеньям. *sunday_pager_end_time*имеет **тип int**и значение по умолчанию **180000**, которое указывает на 6:00 вечера. в 24-часовом формате и должно вводиться в формате ЧЧММСС.  
  
`[ @pager_days = ] pager_days`Число, указывающее дни, когда оператор доступен для страниц (с учетом указанного времени начала или окончания). *pager_days*имеет тип **tinyint**и значение по умолчанию **0** , указывающее, что оператор никогда не может получить страницу. Допустимые значения: от **0** до **127**. *pager_days*вычисляется путем добавления отдельных значений для требуемых дней. Например, с понедельника по пятницу будет **2** + **4** + **8** + **16** + **32**  =  **62**. В следующей таблице перечислены значения для каждого дня недели.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Воскресенье|  
|**2**|Понедельник|  
|**4**|Вторник|  
|**8**|Среда|  
|**16**|Четверг|  
|**32**|Пятница|  
|**64**|Суббота|  
  
`[ @netsend_address = ] 'netsend_address'`Сетевой адрес оператора, которому отправляется сетевое сообщение. *netsend_address*имеет тип **nvarchar (100)** и значение по умолчанию NULL.  
  
`[ @category_name = ] 'category'`Имя категории для этого оператора. *Category* имеет тип **sysname**и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 **sp_add_operator** должны запускаться из базы данных **msdb** .  
  
 Отправка сообщений на пейджер поддерживается системой электронной почты, в которой должна быть функция отправки пейджинговых сообщений через электронную почту.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] обеспечивает доступный графический способ управления заданиями и рекомендуется для создания и управления инфраструктурой заданий.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_add_operator**.  
  
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
 [sp_help_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_update_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
