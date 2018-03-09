---
title: "sysmail_help_queue_sp (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmail_help_queue_sp
- sysmail_help_queue_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_queue_sp
ms.assetid: 94840482-112c-4654-b480-9b456c4c2bca
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5e83aba8601f4329a496229eca329035a95b283c
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysmailhelpqueuesp-transact-sql"></a>sysmail_help_queue_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Существует две очереди в компоненте Database Mail: очередь почты и очередь состояний. Очередь почты содержит почтовые сообщения, ожидающие отправки. Очередь состояний содержит информацию о состоянии сообщений, которые уже были отправлены. Эта хранимая процедура позволяет просмотреть состояние очередей почты и состояний. Если параметр  **@queue_type**  не указан, хранимая процедура возвращает одну строку для каждой из очередей.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_help_queue_sp  [ @queue_type = ] 'queue_type'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@queue_type** = ] **'***queue_type***'**  
 Дополнительный аргумент удаляет сообщения электронной почты, тип, указанный как *queue_type*. *queue_type* — **nvarchar(6)** без значения по умолчанию. Допустимыми значениями являются **mail** и **состояние**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-set"></a>Результирующий набор  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**queue_type**|**nvarchar(6)**|Тип очереди. Возможными значениями являются **mail** и **состояние**.|  
|**длина**|**int**|Номер почтового сообщения в указанной очереди.|  
|**state**|**nvarchar(64)**|Состояние монитора. Возможными значениями являются **НЕАКТИВНО** (очередь неактивна), **NOTIFIED** (очередь уведомление запроса), и **RECEIVES_OCCURRING** (очередь получения).|  
|**last_empty_rowset_time**|**ДАТЫ И ВРЕМЕНИ**|Дата и время, когда очередь в последний раз была пуста. Указывается в военном формате времени относительно часового пояса GMT.|  
|**last_activated_time**|**ДАТЫ И ВРЕМЕНИ**|Дата и время, когда очередь в последний раз была активирована. Указывается в военном формате времени относительно часового пояса GMT.|  
  
## <a name="remarks"></a>Remarks  
 При устранении неполадок компонента Database Mail, используйте **sysmail_help_queue_sp** для просмотра, количество элементов в очереди, состояние очереди и во время ее последнего активирован.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию только члены **sysadmin** предопределенной роли сервера можно получить доступ к этой процедуре.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются очередь почты и очередь состояний.  
  
```  
EXECUTE msdb.dbo.sysmail_help_queue_sp ;  
GO  
```  
  
 Образец результирующего набора, отредактированный по длине строк:  
  
```  
queue_type length      state              last_empty_rowset_time  last_activated_time  
---------- -------- ------------------ ----------------------- -----------------------  
mail       0        RECEIVES_OCCURRING 2005-10-07 21:14:47.010 2005-10-10 20:52:51.517  
status     0        INACTIVE           2005-10-07 21:04:47.003 2005-10-10 21:04:47.003  
  
(2 row(s) affected)  
  
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)  
  
  
