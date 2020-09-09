---
description: sysmail_help_queue_sp (Transact-SQL)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 18e7e8d96a766f628f15dfc747fc3154bc95ea57
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89547270"
---
# <a name="sysmail_help_queue_sp-transact-sql"></a>sysmail_help_queue_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Существует две очереди в компоненте Database Mail: очередь почты и очередь состояний. Очередь почты содержит почтовые сообщения, ожидающие отправки. Очередь состояний содержит информацию о состоянии сообщений, которые уже были отправлены. Эта хранимая процедура позволяет просмотреть состояние очередей почты и состояний. Если параметр ** \@ queue_type** не указан, хранимая процедура возвращает по одной строке для каждой из очередей.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_help_queue_sp  [ @queue_type = ] 'queue_type'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @queue_type = ] 'queue_type'` Необязательный аргумент удаляет адреса электронной почты типа, указанного в качестве *queue_type*. *queue_type* имеет тип **nvarchar (6)** и не имеет значения по умолчанию. Допустимые значения: **mail** и **Status**.  
  
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
  
## <a name="remarks"></a>Примечания  
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
  
  
