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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: cfca5caa10e36196f38817c828cbd4d062763107
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824924"
---
# <a name="sysmail_event_log-transact-sql"></a>sysmail_event_log (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого из сообщений Windows или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], возвращаемых компонентом Database Mail  (Сообщение в этом контексте означает сообщение об ошибке, а не сообщение электронной почты.) Настройте параметр **уровня ведения журнала** с помощью диалогового окна **Настройка системных параметров** мастера настройки Database Mail или хранимой процедуры [sysmail_configure_sp](../../relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql.md) , чтобы определить возвращаемые сообщения.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Log_id**|**int**|Идентификатор элементов в журнале.|  
|**event_type**|**varchar (11)**|Тип уведомления, помещаемого в журнал. Допустимые значения: ошибки, предупреждения, информационные сообщения, сообщения об успешном завершении и дополнительные внутренние сообщения.|  
|**log_date**|**datetime**|Дата и время добавления записи в журнал.|  
|**nописание**|**nvarchar(max)**|Текст добавленного сообщения.|  
|**process_id**|**int**|Идентификатор процесса внешней программы Database Mail. Обычно он изменяется при каждом запуске внешней программы Database Mail.|  
|**mailitem_id**|**int**|Идентификатор почтового отправления в очереди почты. Содержит NULL, если сообщение не относится к определенному элементу электронной почты.|  
|**account_id**|**int**|**Account_id** учетной записи, связанной с событием. Содержит NULL, если сообщение не относится к определенной учетной записи.|  
|**last_mod_date**|**datetime**|Дата и время последнего изменения строки.|  
|**last_mod_user**|**sysname**|Пользователь, внесший последнее изменение в строку. Для электронных сообщений это пользователь, отправивший письмо. Для сообщений, сформированных внешней программой Database Mail, это пользовательский контекст соответствующей программы.|  
  
## <a name="remarks"></a>Примечания  
 При устранении неполадок Database Mail ищите в **sysmail_event_log** представлении события, связанные с ошибками электронной почты. Некоторые сообщения, например информирующие о сбоях внешней программы Database Mail, не связаны с конкретными электронными сообщениями. Чтобы найти ошибки, связанные с конкретными сообщениями электронной почты, найдите **mailitem_id** неудачно отправленного сообщения в **sysmail_faileditems** представлении, а затем найдите в **sysmail_event_log** сообщения, связанные с этим **mailitem_idом**. При возвращении ошибки из **sp_send_dbmail**сообщение электронной почты не отправляется в систему Database Mail, и эта ошибка не отображается в этом представлении.  
  
 Если происходит ошибка доставки для определенной учетной записи, при выполнении повторных попыток компонент Database Mail задерживает сообщения об ошибках до тех пор, пока доставка почтового элемента не завершится либо успехом, либо неудачей. В случае окончательного успеха все накопленные ошибки регистрируются как отдельные предупреждения, включая **account_id**. Это может привести к появлению предупреждений, несмотря на то, что электронное письмо было отправлено. В случае окончательной доставки все предыдущие предупреждения записываются в журнал как одно сообщение об ошибке без **account_id**, так как все учетные записи завершились с ошибкой.  
  
## <a name="permissions"></a>Разрешения  
 Для доступа к этому представлению необходимо быть членом предопределенной роли сервера **sysadmin** или роли базы данных **DatabaseMailUserRole** . Члены роли **DatabaseMailUserRole** , которые не являются членами ролей **sysadmin** , могут просматривать события только для отправленных ими сообщений электронной почты.  
  
## <a name="see-also"></a>См. также  
 [sysmail_faileditems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-faileditems-transact-sql.md)   
 [Внешняя программа компонента Database Mail](../../relational-databases/database-mail/database-mail-external-program.md)  
  
  
