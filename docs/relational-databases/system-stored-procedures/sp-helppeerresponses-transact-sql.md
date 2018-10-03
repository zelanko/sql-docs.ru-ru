---
title: sp_helppeerresponses (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_helppeerresponses_TSQL
- sp_helppeerresponses
helpviewer_keywords:
- sp_helppeerresponses
ms.assetid: e55789d1-43fb-4a37-9e5e-60ccef122a5d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 43c76c0fff2cdf9e7c3af0c747002da0d17ebe22
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47719732"
---
# <a name="sphelppeerresponses-transact-sql"></a>sp_helppeerresponses (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает все ответы на запрос о состоянии, полученный от участника в топологии репликации peer-to-peer, где запрос был инициирован выполнением процедуры [sp_helppeerrequests](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) в любой публикуемой базе данных в топологии. Эта хранимая процедура выполняется в базе данных публикации при участии издателя в топологии одноранговой репликации. Дополнительные сведения см. в разделе [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helppeerresponses [ @request_id = ] request_id  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@request_id**=] *request_id*  
 Идентификатор запроса конкретного состояния. *Идентификатор request_id* — **int**, не имеет значения по умолчанию.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**request_id**|**int**|Идентификатор запроса состояния.|  
|**однорангового узла**|**sysname**|Имя узла, сформировавшего ответ.|  
|**peer_db**|**sysname**|Имя базы данных узла, сформировавшего ответ.|  
|**received_date**|**datetime**|Дата и время, когда запрашивающий объект получил ответ от однорангового узла, который отправил этот ответ.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_helppeerresponses** используется в репликации транзакций peer-to-peer.  
  
 **sp_helppeerresponses** процедура используется при восстановлении базы данных, опубликованной в топологии peer-to-peer.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_helppeerresponses**.  
  
## <a name="see-also"></a>См. также  
 [sp_deletepeerrequesthistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletepeerrequesthistory-transact-sql.md)   
 [sp_helppeerrequests &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerrequests-transact-sql.md)  
  
  
