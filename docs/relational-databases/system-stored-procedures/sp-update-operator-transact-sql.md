---
description: sp_update_operator (Transact-SQL)
title: sp_update_operator (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_operator_TSQL
- sp_update_operator
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_operator
ms.assetid: 231750a6-4828-4d03-afe6-b91d38c42ed3
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 4dbc3c382ecd1c58e9bd76624700a1c62804a82c
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545915"
---
# <a name="sp_update_operator-transact-sql"></a>sp_update_operator (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
 [ @name =] "*имя*"  
 Имя оператора для изменения. Аргумент *Name* имеет тип **sysname**и не имеет значения по умолчанию.  
  
 [ @new_name =] "*new_name*"  
 Новое имя оператора. Имя должно быть уникальным. Аргумент *new_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
 [ @enabled =] *включено*  
 Число, указывающее текущее состояние оператора (**1** , если в настоящее время включено, **0** , если нет). *Enabled* имеет тип **tinyint**и значение по умолчанию NULL. Если оператор не включен, он не будет получать предупреждающих оповещений.  
  
 [ @email_address =] "*email_address*"  
 Адрес электронной почты оператора. Эта строка передается напрямую в систему электронной почты. *email_address* имеет тип **nvarchar (100)** и значение по умолчанию NULL.  
  
 [ @pager_address =] "*pager_number*"  
 Адрес пейджера оператора. Эта строка передается напрямую в систему электронной почты. *pager_number* имеет тип **nvarchar (100)** и значение по умолчанию NULL.  
  
 [ @weekday_pager_start_time =] *weekday_pager_start_time*  
 Указывает время, по истечении которого на пейджер указанному оператору может быть отправлено оповещение (с понедельника по пятницу). *weekday_pager_start_time*имеет **тип int**, значение по умолчанию NULL и должно быть указано в формате ЧЧММСС для использования с 24-часовым часами.  
  
 [ @weekday_pager_end_time =] *weekday_pager_end_time*  
 Указывает время, по истечении которого на пейджер указанному оператору не может быть отправлено оповещение (с понедельника по пятницу). *weekday_pager_end_time*имеет **тип int**, значение по умолчанию NULL и должно быть указано в формате ЧЧММСС для использования с 24-часовым часами.  
  
 [ @saturday_pager_start_time =] *saturday_pager_start_time*  
 Указывает время, по истечении которого на пейджер указанному оператору может быть отправлено оповещение (по субботам). *saturday_pager_start_time*имеет **тип int**, значение по умолчанию NULL и должно быть указано в формате ЧЧММСС для использования с 24-часовым часами.  
  
 [ @saturday_pager_end_time =] *saturday_pager_end_time*  
 Указывает время, по истечении которого на пейджер указанному оператору не может быть отправлено оповещение (по субботам). *saturday_pager_end_time*имеет **тип int**, значение по умолчанию NULL и должно быть указано в формате ЧЧММСС для использования с 24-часовым часами.  
  
 [ @sunday_pager_start_time =] *sunday_pager_start_time*  
 Указывает время, по истечении которого на пейджер указанному оператору может быть отправлено оповещение (по воскресеньям). *sunday_pager_start_time*имеет **тип int**, значение по умолчанию NULL и должно быть указано в формате ЧЧММСС для использования с 24-часовым часами.  
  
 [ @sunday_pager_end_time =] *sunday_pager_end_time*  
 Указывает время, по истечении которого на пейджер указанному оператору не может быть отправлено оповещение (по воскресеньям). *sunday_pager_end_time*имеет **тип int**, значение по умолчанию NULL и должно быть указано в формате ЧЧММСС для использования с 24-часовым часами.  
  
 [ @pager_days =] *pager_days*  
 Указывает дни, в которые оператор доступен для приема сообщений на пейджер (с учетом времени начала и конца работы). *pager_days*имеет тип **tinyint**, значение по умолчанию NULL и должно быть значением от **0** до **127**. *pager_days* вычисляется путем добавления отдельных значений для требуемых дней. Например, с понедельника по пятницу будет **2** + **4** + **8** + **16** + **32**  =  **64**.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Воскресенье|  
|**2**|Понедельник|  
|**4**|Вторник|  
|**8**|Среда|  
|**16**|Четверг|  
|**32**|Пятница|  
|**64**|Суббота|  
  
 [ @netsend_address =] "*netsend_address*"  
 Сетевой адрес оператора, которому посылается сетевое сообщение. *netsend_address*имеет тип **nvarchar (100)** и значение по умолчанию NULL.  
  
 [ @category_name =] "*Категория*"  
 Имя категории предупреждения. *Category* имеет тип **sysname**и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
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
 [sp_help_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
