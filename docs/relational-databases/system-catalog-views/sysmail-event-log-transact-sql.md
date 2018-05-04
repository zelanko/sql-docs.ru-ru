---
title: sysmail_event_log (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysmail_event_log
- sysmail_event_log_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_event_log database mail view
ms.assetid: 440bc409-1188-4175-afc4-c68e31e44fed
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 37844c3d31b603f873f6360aa74af3d91d03e334
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysmaileventlog-transact-sql"></a>sysmail_event_log (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого из сообщений Windows или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], возвращаемых компонентом Database Mail  (под сообщением подразумевается сообщение об ошибке, а не электронное письмо). Настройка **уровень ведения журнала** параметра с помощью **системных параметров** диалоговое окно мастера настройки компонента Database Mail, или [sysmail_configure_sp](../../relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql.md)хранимую процедуру, чтобы определить, какие сообщения возвращаются.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Log_id**|**int**|Идентификатор элементов в журнале.|  
|**event_type**|**varchar(11)**|Тип уведомления, помещаемого в журнал. Допустимые значения: ошибки, предупреждения, информационные сообщения, сообщения об успешном завершении и дополнительные внутренние сообщения.|  
|**log_date**|**datetime**|Дата и время добавления записи в журнал.|  
|**Описание**|**nvarchar(max)**|Текст добавленного сообщения.|  
|**process_id**|**int**|Идентификатор процесса внешней программы Database Mail. Обычно он изменяется при каждом запуске внешней программы Database Mail.|  
|**mailitem_id**|**int**|Идентификатор почтового отправления в очереди почты. Содержит NULL, если сообщение не относится к определенному элементу электронной почты.|  
|**account_id**|**int**|**Account_id** учетной записи, относящиеся к событию. Содержит NULL, если сообщение не относится к определенной учетной записи.|  
|**last_mod_date**|**datetime**|Дата и время последнего изменения строки.|  
|**last_mod_user**|**sysname**|Пользователь, внесший последнее изменение в строку. Для электронных сообщений это пользователь, отправивший письмо. Для сообщений, сформированных внешней программой Database Mail, это пользовательский контекст соответствующей программы.|  
  
## <a name="remarks"></a>Замечания  
 При устранении неполадок компонента Database Mail, поиск **sysmail_event_log** представление событий, связанных с ошибками электронной почты. Некоторые сообщения, например информирующие о сбоях внешней программы Database Mail, не связаны с конкретными электронными сообщениями. Для поиска ошибок, относящихся к конкретному, поиск **mailitem_id** электронному в **sysmail_faileditems** просмотра и выполните поиск **sysmail_event_log**для сообщения, относящиеся к этому **mailitem_id**. Если возвращается сообщение об ошибке из **sp_send_dbmail**, адрес электронной почты не передан в системе компонента Database Mail, и ошибка не отображается в этом представлении.  
  
 Если происходит ошибка доставки для определенной учетной записи, при выполнении повторных попыток компонент Database Mail задерживает сообщения об ошибках до тех пор, пока доставка почтового элемента не завершится либо успехом, либо неудачей. Успешно, все накопленные ошибки заносятся в журнал как отдельные предупреждения, в том числе **account_id**. Это может привести к появлению предупреждений, несмотря на то, что электронное письмо было отправлено. В случае сбоя доставки ultimate все имеющиеся предупреждения заносятся в виде одного сообщения об ошибке без **account_id**, так как произошел сбой всех учетных записей.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом **sysadmin** предопределенной роли сервера или **DatabaseMailUserRole** роли базы данных для доступа к этому представлению. Члены **DatabaseMailUserRole** , не являющиеся членами **sysadmin** роли, можно увидеть только события для электронных сообщений, которые они отправляют.  
  
## <a name="see-also"></a>См. также  
 [sysmail_faileditems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-faileditems-transact-sql.md)   
 [Внешняя программа компонента Database Mail](../../relational-databases/database-mail/database-mail-external-program.md)  
  
  
