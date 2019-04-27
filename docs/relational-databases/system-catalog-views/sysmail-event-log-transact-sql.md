---
title: sysmail_event_log (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_event_log
- sysmail_event_log_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_event_log database mail view
ms.assetid: 440bc409-1188-4175-afc4-c68e31e44fed
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8ac38c2e54fde2beb02e009e00b9f587e9265a43
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62759945"
---
# <a name="sysmaileventlog-transact-sql"></a>sysmail_event_log (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого из сообщений Windows или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], возвращаемых компонентом Database Mail  (Сообщения в этом контексте ссылается на сообщение, например сообщение об ошибке, а не сообщение электронной почты). Настройка **уровень ведения журнала** параметра с помощью **системных параметров** диалоговое окно мастера настройки компонента Database Mail, или [sysmail_configure_sp](../../relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql.md)хранимую процедуру, чтобы определить, какие сообщения возвращаются.  
  
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
  
## <a name="remarks"></a>Примечания  
 При устранении неполадок компонента Database Mail, выполните поиск **sysmail_event_log** представление для событий, связанных с ошибками по электронной почте. Некоторые сообщения, например информирующие о сбоях внешней программы Database Mail, не связаны с конкретными электронными сообщениями. Чтобы найти ошибки, связанные с конкретными электронными сообщениями, поиск **mailitem_id** неудачных сообщений электронной почты в **sysmail_faileditems** просмотра, а затем найдите **sysmail_event_log**для сообщения с тем **mailitem_id**. Если возвращается сообщение об ошибке из **sp_send_dbmail**, сообщения электронной почты не отправляется в системе компонента Database Mail, и ошибка не отображается в этом представлении.  
  
 Если происходит ошибка доставки для определенной учетной записи, при выполнении повторных попыток компонент Database Mail задерживает сообщения об ошибках до тех пор, пока доставка почтового элемента не завершится либо успехом, либо неудачей. Успешно, все накопленные ошибки заносятся в журнал как отдельных предупреждений с указанием **account_id**. Это может привести к появлению предупреждений, несмотря на то, что электронное письмо было отправлено. В случае сбоя доставки ultimate, все имеющиеся предупреждения заносятся в виде одного сообщения об ошибке без **account_id**, так как не удалось выполнить все учетные записи.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом **sysadmin** предопределенной роли сервера или **DatabaseMailUserRole** роли базы данных, доступ к этому представлению. Членами **DatabaseMailUserRole** , не являющиеся членами **sysadmin** роли, можно видеть только события для сообщений электронной почты, которые они отправляют.  
  
## <a name="see-also"></a>См. также  
 [sysmail_faileditems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-faileditems-transact-sql.md)   
 [Внешняя программа компонента Database Mail](../../relational-databases/database-mail/database-mail-external-program.md)  
  
  
