---
title: sysmail_help_queue_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_queue_sp
- sysmail_help_queue_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_queue_sp
ms.assetid: 94840482-112c-4654-b480-9b456c4c2bca
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 76f51489a449c44dd7d43bab75d504f68e946374
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47796524"
---
# <a name="sysmailhelpqueuesp-transact-sql"></a>sysmail_help_queue_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Существует две очереди в компоненте Database Mail: очередь почты и очередь состояний. Очередь почты содержит почтовые сообщения, ожидающие отправки. Очередь состояний содержит информацию о состоянии сообщений, которые уже были отправлены. Эта хранимая процедура позволяет просмотреть состояние очередей почты и состояний. Если параметр **@queue_type** не указан, хранимая процедура возвращает одну строку для каждого из очереди.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_help_queue_sp  [ @queue_type = ] 'queue_type'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@queue_type** = ] **'***queue_type***'**  
 Дополнительный аргумент удаляет сообщения электронной почты типа, указанного как *queue_type*. *queue_type* — **nvarchar(6)** не имеет значения по умолчанию. Допустимыми значениями являются **mail** и **состояние**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-set"></a>Результирующий набор  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**queue_type**|**nvarchar(6)**|Тип очереди. Возможные значения: **mail** и **состояние**.|  
|**Длина**|**int**|Номер почтового сообщения в указанной очереди.|  
|**state**|**Nvarchar(64)**|Состояние монитора. Возможные значения: **НЕАКТИВНО** (очередь неактивна), **уведомления об** (очередь уведомление запроса о получении возникает), и **RECEIVES_OCCURRING** (очередь получения).|  
|**last_empty_rowset_time**|**ДАТЫ И ВРЕМЕНИ**|Дата и время, когда очередь в последний раз была пуста. Указывается в военном формате времени относительно часового пояса GMT.|  
|**last_activated_time**|**ДАТЫ И ВРЕМЕНИ**|Дата и время, когда очередь в последний раз была активирована. Указывается в военном формате времени относительно часового пояса GMT.|  
  
## <a name="remarks"></a>Примечания  
 При устранении неполадок компонента Database Mail, используйте **sysmail_help_queue_sp** чтобы увидеть, сколько элементов находятся в очереди, состояние очереди, а также время ее последнего активации.  
  
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
  
  
