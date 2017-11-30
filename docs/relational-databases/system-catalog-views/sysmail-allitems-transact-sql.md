---
title: "sysmail_allitems (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmail_allitems_TSQL
- sysmail_allitems
dev_langs: TSQL
helpviewer_keywords: sysmail_allitems database mail view
ms.assetid: 21fb8432-7677-4435-902f-64a58bba4cbb
caps.latest.revision: "17"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: ba8deb3b11b01cf9f53e02024815150fa4441b6d
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="sysmailallitems-transact-sql"></a>sysmail_allitems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит одну строку для каждого сообщения, обработанного компонентом Database Mail. Используйте это представление для просмотра состояния всех сообщений.  
  
 Для просмотра только сообщений в состоянии сбоя, используйте [sysmail_faileditems &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-faileditems-transact-sql.md). Чтобы просмотреть только неотправленные сообщения, используйте [sysmail_unsentitems &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql.md). Чтобы просмотреть только те сообщения, которые были отправлены, используйте [sysmail_sentitems &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-sentitems-transact-sql.md).  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**mailitem_id**|**int**|Идентификатор почтового отправления в очереди почты.|  
|**profile_id**|**int**|Идентификатор профиля, используемого для отсылки этого сообщения.|  
|**Получатели**|**varchar(max)**|Электронные адреса получателей сообщения.|  
|**copy_recipients**|**varchar(max)**|Электронные адреса получателей копий сообщения.|  
|**Аргумент blind_copy_recipients**|**varchar(max)**|Электронные адреса получателей копий сообщения, чьи имена не будут отображаться в заголовке сообщения.|  
|**Тема**|**nvarchar(510)**|Строка темы сообщения.|  
|**текст**|**varchar(max)**|Тело сообщения.|  
|**body_format**|**varchar(20)**|Формат тела сообщения. Допустимые значения — TEXT и HTML.|  
|**важность**|**varchar(6)**|**Важность** параметр сообщения.|  
|**чувствительность**|**varchar(12)**|**Чувствительности** параметр сообщения.|  
|**file_attachments**|**varchar(max)**|Список имен файлов, разделенных точкой с запятой, который прикреплен к сообщению электронной почты.|  
|**attachment_encoding**|**varchar(20)**|Тип вложения.|  
|**запрос**|**varchar(max)**|Запрос, выполненный почтовой программой.|  
|**execute_query_database**|**sysname**|Контекст базы данных, в котором почтовая программа выполнила запрос.|  
|**attach_query_result_as_file**|**bit**|Если значение равно 0, результаты запроса были включены в тело сообщения после его содержимого. Если значение равно 1, результаты были возвращены в виде вложения.|  
|**query_result_header**|**bit**|Если значение равно 1, результаты запроса содержали заголовки столбцов. Если значение равно 0, результаты запроса не включали заголовков столбцов.|  
|**query_result_width**|**int**|**Query_result_width** параметр сообщения.|  
|**query_result_separator**|**char(1)**|Символ, используемый для разделения столбцов в выходных данных запроса.|  
|**exclude_query_output**|**bit**|**Exclude_query_output** параметр сообщения. Дополнительные сведения см. в разделе [sp_send_dbmail &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).|  
|**append_query_error**|**bit**|**Append_query_error** параметр сообщения. 0 означает, что компонент Database Mail не отсылает электронное сообщение, если в запросе содержится ошибка.|  
|**send_request_date**|**datetime**|Дата и время помещения сообщения в очередь почты.|  
|**send_request_user**|**sysname**|Пользователь, отправивший сообщение. Это пользовательский контекст процедуры компонента Database Mail, а не поле «От:» с именем отправителя сообщения.|  
|**sent_account_id**|**int**|Идентификатор учетной записи компонента Database Mail, используемой для отсылки этого сообщения.|  
|**sent_status**|**varchar(8)**|Состояние почты. Возможны следующие значения:<br /><br /> **отправлено** — почта была отправлена.<br /><br /> **неотправленные** -компонента Database mail по-прежнему пытается отправить сообщение.<br /><br /> **Повторная попытка** -компонент Database Mail не удалось отправить сообщение, но предпринимает попытку отправки.<br /><br /> **не удалось выполнить** -компонент Database mail не удалось отправить сообщение.|  
|**sent_date**|**datetime**|Дата и время отсылки сообщения.|  
|**last_mod_date**|**datetime**|Дата и время последнего изменения строки.|  
|**last_mod_user**|**sysname**|Пользователь, внесший последнее изменение в строку.|  
  
## <a name="remarks"></a>Замечания  
 Используйте **sysmail_allitems** представление для просмотра состояния всех сообщений, обработанных компонентом Database Mail. Это представление может быть полезным при выявлении неполадок в работе компонента Database Mail. Оно помогает выявлять сущность проблемы, отображая атрибуты отправленных сообщений в сравнении с атрибутами неотправленных сообщений.  
  
 Системные таблицы, отображаемые в данном представлении, содержат все сообщения и может привести к **msdb** рост базы данных. Чтобы уменьшить размеры таблиц, регулярно удаляйте из этого представления старые сообщения. Дополнительные сведения см. в разделе [создания задания агента SQL Server для архива сообщения компонента Database Mail и журналов событий](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md).  
  
## <a name="permissions"></a>Permissions  
 Предоставленные **sysadmin** предопределенной роли сервера и **DatabaseMailUserRole** роли базы данных. При выполнении членом **sysadmin** предопределенной роли сервера, в этом представлении отображаются все сообщения. Все остальные пользователи могут видеть лишь сообщения, отправленные ими.  
  
  
