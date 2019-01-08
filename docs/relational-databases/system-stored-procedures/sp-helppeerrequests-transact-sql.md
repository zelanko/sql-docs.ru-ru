---
title: sp_helppeerrequests (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helppeerrequests_TSQL
- sp_helppeerrequests
helpviewer_keywords:
- sp_helppeerrequests
ms.assetid: 37bd503e-46c4-47c6-996e-be7ffe636fe8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fde5daf72455af7c4c46c9ef19e4975a3f87a2dc
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52802236"
---
# <a name="sphelppeerrequests-transact-sql"></a>sp_helppeerrequests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения обо всех запросах состояния, полученных участниками в топологии репликации peer-to-peer, где эти запросы были инициированы выполнением процедуры [sp_requestpeerresponse &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) ни на одном опубликованной базы данных в топологии. Эта хранимая процедура выполняется в базе данных публикации при участии издателя в топологии одноранговой репликации. Дополнительные сведения см. в разделе [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helppeerrequests [ @publication = ] 'publication'  
    [ , [ @description = ] 'description'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@publication**=] **"***публикации***"**  
 Имя публикации в одноранговой топологии, для которой были отправлены запросы состояния. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@description**=] **"***описание***"**  
 Значение, которое может использоваться для идентификации запросов состояния, позволяющий позволяет фильтровать возвращенные ответы на основе пользовательской информации, предоставленной при вызове [sp_requestpeerresponse &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md). *Описание* — **nvarchar(4000)**, значение по умолчанию **%**. По умолчанию возвращается информация обо всех запросах состояния публикации. Этот параметр используется для возврата только тех запросов состояния с описанием соответствует значению аргумента в *описание*, где символьных строк сопоставляются с помощью [как &#40;Transact-SQL&#41; ](../../t-sql/language-elements/like-transact-sql.md)предложение.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор запроса.|  
|**публикации**|**sysname**|Имя публикации, запрос состояния которой был отправлен.|  
|**sent_date**|**datetime**|Дата и время отправления запроса состояния.|  
|**Описание**|**nvarchar(4000)**|Пользовательская информация, которую можно использовать для идентификации запросов состояния.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_helppeerrequests** используется в репликации транзакций peer-to-peer.  
  
 **sp_helppeerrequests** используется при восстановлении базы данных, опубликованной в топологии peer-to-peer.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_helppeerrequests**.  
  
## <a name="see-also"></a>См. также  
 [sp_deletepeerrequesthistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletepeerrequesthistory-transact-sql.md)   
 [sp_helppeerresponses &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md)  
  
  
