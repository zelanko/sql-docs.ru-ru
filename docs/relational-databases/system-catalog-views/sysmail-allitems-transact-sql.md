---
title: sysmail_allitems (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_allitems_TSQL
- sysmail_allitems
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_allitems database mail view
ms.assetid: 21fb8432-7677-4435-902f-64a58bba4cbb
author: stevestein
ms.author: sstein
ms.openlocfilehash: be5c74e58e5c107a804903ab09de38b931f676e1
ms.sourcegitcommit: a97d551b252b76a33606348082068ebd6f2c4c8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70745454"
---
# <a name="sysmail_allitems-transact-sql"></a>sysmail_allitems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Содержит одну строку для каждого сообщения, обработанного компонентом Database Mail. Используйте это представление для просмотра состояния всех сообщений.  
  
 Чтобы просмотреть только сообщения с состоянием Failed, [Используйте &#40;SYSMAIL_FAILEDITEMS Transact-&#41;SQL](../../relational-databases/system-catalog-views/sysmail-faileditems-transact-sql.md). Чтобы просмотреть только неотправленные сообщения, [Используйте &#40;SYSMAIL_UNSENTITEMS Transact-&#41;SQL](../../relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql.md). Чтобы просмотреть только отправленные сообщения, используйте [sysmail_sentitems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-sentitems-transact-sql.md).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**mailitem_id**|**int**|Идентификатор почтового отправления в очереди почты.|  
|**profile_id**|**int**|Идентификатор профиля, используемого для отсылки этого сообщения.|  
|**пользу**|**varchar(max)**|Электронные адреса получателей сообщения.|  
|**copy_recipients**|**varchar(max)**|Электронные адреса получателей копий сообщения.|  
|**blind_copy_recipients**|**varchar(max)**|Электронные адреса получателей копий сообщения, чьи имена не будут отображаться в заголовке сообщения.|  
|**Тема**|**nvarchar (510)**|Строка темы сообщения.|  
|**организм**|**varchar(max)**|Тело сообщения.|  
|**body_format**|**varchar (20)**|Формат тела сообщения. Допустимые значения — TEXT и HTML.|  
|**важный**|**varchar (6)**|Параметр **важности** сообщения.|  
|**чувствительности**|**varchar (12)**|Параметр **чувствительности** сообщения.|  
|**file_attachments**|**varchar(max)**|Список имен файлов, разделенных точкой с запятой, который прикреплен к сообщению электронной почты.|  
|**attachment_encoding**|**varchar (20)**|Тип вложения.|  
|**Выбор**|**varchar(max)**|Запрос, выполненный почтовой программой.|  
|**execute_query_database**|**sysname**|Контекст базы данных, в котором почтовая программа выполнила запрос.|  
|**attach_query_result_as_file**|**bit**|Если значение равно 0, результаты запроса были включены в тело сообщения после его содержимого. Если значение равно 1, результаты были возвращены в виде вложения.|  
|**query_result_header**|**bit**|Если значение равно 1, результаты запроса содержали заголовки столбцов. Если значение равно 0, результаты запроса не включали заголовков столбцов.|  
|**query_result_width**|**int**|Параметр **query_result_width** сообщения.|  
|**query_result_separator**|**char(1)**|Символ, используемый для разделения столбцов в выходных данных запроса.|  
|**exclude_query_output**|**bit**|Параметр **exclude_query_output** сообщения. Дополнительные сведения см. в [разделе &#40;SP_SEND_DBMAIL Transact-&#41;SQL](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).|  
|**append_query_error**|**bit**|Параметр **append_query_error** сообщения. 0 означает, что компонент Database Mail не отсылает электронное сообщение, если в запросе содержится ошибка.|  
|**send_request_date**|**datetime**|Дата и время помещения сообщения в очередь почты.|  
|**send_request_user**|**sysname**|Пользователь, отправивший сообщение. Это пользовательский контекст процедуры компонента Database Mail, а не поле «От:» с именем отправителя сообщения.|  
|**sent_account_id**|**int**|Идентификатор учетной записи компонента Database Mail, используемой для отсылки этого сообщения.|  
|**sent_status**|**varchar (8)**|Состояние почты. Доступны следующие значения:<br /><br /> **Отправлено** — почта отправлена.<br /><br /> **неотправленные** — компонент Database Mail по-прежнему пытается отправить сообщение.<br /><br /> При повторной **попытке** Database Mail не удалось отправить сообщение, но предпринимается попытка его отправки.<br /><br /> **сбой** . компоненту Database Mail не удалось отправить сообщение.|  
|**sent_date**|**datetime**|Дата и время отсылки сообщения.|  
|**last_mod_date**|**datetime**|Дата и время последнего изменения строки.|  
|**last_mod_user**|**sysname**|Пользователь, внесший последнее изменение в строку.|  
  
## <a name="remarks"></a>Примечания  
 Используйте представление **sysmail_allitems** , чтобы просмотреть состояние всех сообщений, обрабатываемых Database Mail. Это представление может быть полезным при выявлении неполадок в работе компонента Database Mail. Оно помогает выявлять сущность проблемы, отображая атрибуты отправленных сообщений в сравнении с атрибутами неотправленных сообщений.  
  
 Системные таблицы, представленные в этом представлении, содержат все сообщения и могут привести к увеличению размера базы данных **msdb** . Чтобы уменьшить размеры таблиц, регулярно удаляйте из этого представления старые сообщения. Дополнительные сведения см. в разделе [создание агент SQL Server задания для архивации Database Mail сообщений и журналов событий](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md).  
  
## <a name="permissions"></a>Разрешения  
 Предоставлено предопределенной роли сервера **sysadmin** и роли базы данных **DatabaseMailUserRole** . При выполнении членом предопределенной роли сервера **sysadmin** в этом представлении отображаются все сообщения. Все остальные пользователи могут видеть лишь сообщения, отправленные ими.  
  
  
