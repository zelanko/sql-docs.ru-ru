---
title: sysmail_sentitems (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_sentitems_TSQL
- sysmail_sentitems
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_sentitems database mail view
ms.assetid: 16eb2a44-cebb-4cec-93ac-e2498c39989f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 57fee409bbaa286f052c2fa11e15a956fcd7d540
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47699232"
---
# <a name="sysmailsentitems-transact-sql"></a>sysmail_sentitems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке на каждое сообщение, отправленное компонентом Database Mail. Используйте **sysmail_sentitems** Если вы хотите просмотреть, какие сообщения были успешно отправлены.  
  
 Для просмотра всех сообщений, обработанных компонентом Database Mail, используйте [sysmail_allitems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-allitems-transact-sql.md). Для просмотра только сообщений с состоянием ошибки, используйте [sysmail_faileditems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-faileditems-transact-sql.md). Чтобы просмотреть только неотправленные или ожидающие повторной отправки сообщения, используйте [sysmail_unsentitems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql.md). Чтобы просмотреть вложения электронной почты, используйте [sysmail_mailattachments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-mailattachments-transact-sql.md).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**mailitem_id**|**int**|Идентификатор почтового отправления в очереди почты.|  
|**profile_id**|**int**|Идентификатор профиля, используемого для отсылки этого сообщения.|  
|**Получатели**|**varchar(max)**|Электронные адреса получателей сообщения.|  
|**copy_recipients**|**varchar(max)**|Электронные адреса получателей копий сообщения.|  
|**blind_copy_recipients**|**varchar(max)**|Электронные адреса получателей копий сообщения, чьи имена не будут отображаться в заголовке сообщения.|  
|**Тема**|**nvarchar(510)**|Строка темы сообщения.|  
|**Текст**|**varchar(max)**|Тело сообщения.|  
|**body_format**|**varchar(20)**|Формат тела сообщения. Возможные значения: **текст** и **HTML**.|  
|**Важность**|**varchar(6)**|**Важности** параметр сообщения.|  
|**Чувствительность**|**varchar(12)**|**Чувствительности** параметр сообщения.|  
|**file_attachments**|**varchar(max)**|Список имен файлов, разделенных точкой с запятой, который прикреплен к сообщению электронной почты.|  
|**attachment_encoding**|**varchar(20)**|Тип вложения.|  
|**Запрос**|**varchar(max)**|Запрос, выполненный почтовой программой.|  
|**execute_query_database**|**sysname**|Контекст базы данных, в котором почтовая программа выполнила запрос.|  
|**attach_query_result_as_file**|**bit**|Если значение равно 0, результаты запроса были включены в тело сообщения после его содержимого. Если значение равно 1, результаты были возвращены в виде вложения.|  
|**query_result_header**|**bit**|Если значение равно 1, результаты запроса содержали заголовки столбцов. Если значение равно 0, результаты запроса не включали заголовков столбцов.|  
|**query_result_width**|**int**|**Query_result_width** параметр сообщения.|  
|**query_result_separator**|**char(1)**|Символ, используемый для разделения столбцов в выходных данных запроса.|  
|**exclude_query_output**|**bit**|**Exclude_query_output** параметр сообщения. Дополнительные сведения см. в разделе [sp_send_dbmail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).|  
|**append_query_error**|**bit**|**Append_query_error** параметр сообщения. 0 означает, что компонент Database Mail не отсылает электронное сообщение, если в запросе содержится ошибка.|  
|**send_request_date**|**datetime**|Дата и время помещения сообщения в очередь почты.|  
|**send_request_user**|**sysname**|Пользователь, передавший сообщение. Это пользовательский контекст процедуры компонента Database Mail, а не поле «От:» с именем отправителя сообщения.|  
|**sent_account_id**|**int**|Идентификатор учетной записи компонента Database Mail, используемой для отсылки этого сообщения.|  
|**sent_status**|**varchar(8)**|Состояние почты. Всегда **отправленных** для этого представления.|  
|**sent_date**|**datetime**|Дата и время отсылки сообщения.|  
|**last_mod_date**|**datetime**|Дата и время последнего изменения строки.|  
|**last_mod_user**|**sysname**|Пользователь, внесший последнее изменение в строку.|  
  
## <a name="remarks"></a>Примечания  
 При устранении неполадок в работе компонента Database Mail в этом представлении будут отображаться атрибуты успешно отправленных сообщений, что может помочь в определении причин неполадки. Компонент Database Mail помечает сообщения как отправленные, если они успешно переданы на почтовый SMTP-сервер. Как правило, электронная почта доходит за несколько минут, однако она может задерживаться из-за неполадок на SMTP-сервере. Компонент Database Mail помечает сообщения как отправленные, когда их принимает SMTP-сервер. Неполадки, возникающие на SMTP-сервере, например электронные адреса получателей, доставка на которые невозможна, не возвращаются в компонент Database Mail. Эти электронные письма помечаются как отправленные, несмотря на то, что они не были доставлены. Этот тип неполадок следует устранять на SMTP-сервере. Кроме того, SMTP-сервер может отправить уведомление о невозможности доставить сообщение по соответствующему электронному адресу, указанному в учетной записи компонента Database Mail.  
  
## <a name="permissions"></a>Разрешения  
 Предоставленные **sysadmin** предопределенной роли сервера и **databasemailuserrole** роли базы данных. При выполнении членом **sysadmin** предопределенной роли сервера, в этом представлении отображаются все сообщения. Все остальные пользователи видят только собственные отправленные сообщения.  
  
## <a name="see-also"></a>См. также  
 [Объекты обмена сообщениями компонента Database Mail](../../relational-databases/database-mail/database-mail-messaging-objects.md)  
  
  
