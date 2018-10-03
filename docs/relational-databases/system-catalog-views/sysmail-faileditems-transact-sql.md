---
title: sysmail_faileditems (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_faileditems
- sysmail_faileditems_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_faileditems database mail view
ms.assetid: a31562c5-358e-4cfc-a72d-b3faccc53851
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 92e8031b42b3b0b54aac09913e7eb54e5be07e86
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47624092"
---
# <a name="sysmailfaileditems-transact-sql"></a>sysmail_faileditems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого сообщения компонента Database Mail с помощью **сбой** состояния. С помощью этого представления можно определить, какие сообщения не удалось успешно отправить.  
  
 Для просмотра всех сообщений, обработанных компонентом Database Mail, используйте [sysmail_allitems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-allitems-transact-sql.md). Чтобы просмотреть только неотправленные сообщения, используйте [sysmail_unsentitems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql.md). Чтобы просмотреть только те сообщения, которые были отправлены, используйте [sysmail_sentitems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-sentitems-transact-sql.md). Чтобы просмотреть вложения электронной почты, используйте [sysmail_mailattachments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-mailattachments-transact-sql.md).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**mailitem_id**|**int**|Идентификатор почтового отправления в очереди почты.|  
|**profile_id**|**int**|Идентификатор профиля, использованного для передачи сообщения.|  
|**Получатели**|**varchar(max)**|Электронные адреса получателей сообщения.|  
|**copy_recipients**|**varchar(max)**|Электронные адреса получателей копий сообщения.|  
|**blind_copy_recipients**|**varchar(max)**|Электронные адреса получателей копий сообщения, чьи имена не будут отображаться в заголовке сообщения.|  
|**Тема**|**nvarchar(510)**|Строка темы сообщения.|  
|**Текст**|**varchar(max)**|Тело сообщения.|  
|**body_format**|**varchar(20)**|Формат тела сообщения. Допустимые значения — TEXT и HTML.|  
|**Важность**|**varchar(6)**|**Важности** параметр сообщения.|  
|**Чувствительность**|**varchar(12)**|**Чувствительности** параметр сообщения.|  
|**file_attachments**|**varchar(max)**|Список имен файлов, разделенных точкой с запятой, который прикреплен к сообщению электронной почты.|  
|**Attachment_encoding**|**varchar(20)**|Тип вложения.|  
|**Запрос**|**varchar(max)**|Запрос, выполненный почтовой программой.|  
|**execute_query_database**|**sysname**|Контекст базы данных, в котором почтовая программа выполнила запрос.|  
|**attach_query_result_as_file**|**bit**|Если значение равно 0, результаты запроса были включены в тело сообщения после его содержимого. Если значение равно 1, результаты были возвращены в виде вложения.|  
|**query_result_header**|**bit**|Если значение равно 1, результаты запроса содержали заголовки столбцов. Если значение равно 0, результаты запроса не включали заголовков столбцов.|  
|**query_result_width**|**int**|**Query_result_width** параметр сообщения.|  
|**query_result_separator**|**char(1)**|Символ, используемый для разделения столбцов в выходных данных запроса.|  
|**exclude_query_output**|**bit**|**Exclude_query_output** параметр сообщения. Дополнительные сведения см. в разделе [sp_send_dbmail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).|  
|**append_query_error**|**bit**|**Append_query_error** параметр сообщения. 0 означает, что компонент Database Mail не отсылает электронное сообщение, если в запросе содержится ошибка.|  
|**send_request_date**|**datetime**|Дата и время помещения сообщения в очередь почты.|  
|**send_request_user**|**sysname**|Пользователь, отправивший сообщение. Это пользовательский контекст процедуры компонента Database Mail, а не поле «От:» с именем отправителя сообщения.|  
|**sent_account_id**|**int**|Идентификатор учетной записи компонента Database Mail, используемой для отсылки этого сообщения. Всегда NULL для этого представления.|  
|**sent_status**|**varchar(8)**|Состояние почты. Всегда **сбой** для этого представления.|  
|**sent_date**|**datetime**|Дата и время удаления сообщения из очереди на отправку.|  
|**last_mod_date**|**datetime**|Дата и время последнего изменения строки.|  
|**last_mod_user**|**sysname**|Пользователь, внесший последнее изменение в строку.|  
  
## <a name="remarks"></a>Примечания  
 Используйте **sysmail_faileditems** представление, чтобы увидеть, какие сообщения, не отправленных компонентом Database Mail. При диагностике проблем, связанных с компонентом Database Mail, это представление может помочь определить причину проблемы, поскольку содержит атрибуты сообщений, которые не удалось отправить. Чтобы просмотреть причину сбоя, см. в записи сбой сообщению в [sysmail_event_log &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sysmail-event-log-transact-sql.md) представления.  
  
## <a name="permissions"></a>Разрешения  
 Предоставленные **sysadmin** предопределенной роли сервера и **databasemailuserrole** роли базы данных. При выполнении членом **sysadmin** предопределенной роли сервера, это представление отображает все сбойные сообщения. Прочие пользователи увидят лишь свои собственные сообщения, которые не удалось отправить.  
  
  
