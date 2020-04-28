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
ms.openlocfilehash: d506d7ea841e211d9ab6fb0715a6a9359cefa83d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "79289952"
---
# <a name="sysmail_help_queue_sp-transact-sql"></a>sysmail_help_queue_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Существует две очереди в компоненте Database Mail: очередь почты и очередь состояний. Очередь почты содержит почтовые сообщения, ожидающие отправки. Очередь состояний содержит информацию о состоянии сообщений, которые уже были отправлены. Эта хранимая процедура позволяет просмотреть состояние очередей почты и состояний. Если параметр ** \@queue_type** не указан, хранимая процедура возвращает по одной строке для каждой из очередей.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_help_queue_sp  [ @queue_type = ] 'queue_type'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @queue_type = ] 'queue_type'`Необязательный аргумент удаляет адреса электронной почты типа, указанного в качестве *queue_type*. *queue_type* имеет тип **nvarchar (6)** и не имеет значения по умолчанию. Допустимые значения: **mail** и **Status**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-set"></a>Результирующий набор  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**queue_type**|**nvarchar (6)**|Тип очереди. Возможные значения: **mail** и **Status**.|  
|**length**|**int**|Номер почтового сообщения в указанной очереди.|  
|**state**|**nvarchar (64)**|Состояние монитора. Возможные значения: **неактивные** (очередь неактивна), **уведомление** (уведомление о поступлении в очередь) и **RECEIVES_OCCURRING** (получение очереди).|  
|**last_empty_rowset_time**|**DATETIME**|Дата и время, когда очередь в последний раз была пуста. Указывается в военном формате времени относительно часового пояса GMT.|  
|**last_activated_time**|**DATETIME**|Дата и время, когда очередь в последний раз была активирована. Указывается в военном формате времени относительно часового пояса GMT.|  
  
## <a name="remarks"></a>Remarks  
 При устранении неполадок Database Mail используйте **sysmail_help_queue_sp** , чтобы увидеть количество элементов в очереди, состояние очереди и время последней активации.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию доступ к этой процедуре имеют только члены предопределенной роли сервера **sysadmin** .  
  
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
  
## <a name="see-also"></a>См. также:  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)  
  
  
