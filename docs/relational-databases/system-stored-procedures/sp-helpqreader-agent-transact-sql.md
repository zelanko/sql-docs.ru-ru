---
title: sp_helpqreader_agent (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_helpqreader_agent_TSQL
- sp_helpqreader_agent
helpviewer_keywords:
- sp_helpqreader_agent
ms.assetid: 8e74e1aa-e95b-4183-8017-bf123439b08d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7689cb7c31415b34abdc2320f47c754e9f749e44
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47702294"
---
# <a name="sphelpqreaderagent-transact-sql"></a>sp_helpqreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает свойства агента чтения очереди. Данная хранимая процедура применяется на распространителе в базе данных распространителя или на издателе в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpqreader_agent [ [ @frompublisher = ] frompublisher ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@frompublisher=** ] *frompublisher*  
 Указывает, где была вызвана хранимая процедура: на издателе или на распространителе. *frompublisher* имеет тип bit и значение по умолчанию 0. **1** означает, что хранимая процедура вызывается на издателе, и **0** означает, что хранимая процедура вызывается из распространителя.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор агента.|  
|**name**|**Nvarchar(100)**|Имя агента.|  
|**job_id**|**uniqueidentifier**|Уникальный идентификатор задания агента.|  
|**job_login**|**nvarchar(512)**|Учетная запись Windows, под которой запускается агент распространителя, который возвращается в формате *домена*\\*username*.|  
|**job_password**|**sysname**|По соображениям безопасности значение **\* \* \* \* \* \* \* \* \* \*** всегда возвращается.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_helpqreader_agent** используется в репликации транзакций.  
  
## <a name="permissions"></a>Разрешения  
 Если значение *frompublisher* — **1**, только члены **sysadmin** предопределенной роли сервера на издателе или члены **db_owner**предопределенной роли базы данных в базе данных публикации могут выполнять процедуру **sp_helpqreader_agent**. В противном случае — только члены **sysadmin** предопределенной роли сервера на распространителе или члены **db_owner** предопределенной роли базы данных в базе данных распространителя могут выполнять процедуру **sp_helpqreader_ агент**.  
  
## <a name="see-also"></a>См. также  
 [Включение обновляемых подписок для публикации транзакций](../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
  
