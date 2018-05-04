---
title: sp_helppeerrequests (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helppeerrequests_TSQL
- sp_helppeerrequests
helpviewer_keywords:
- sp_helppeerrequests
ms.assetid: 37bd503e-46c4-47c6-996e-be7ffe636fe8
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: ee270d9434bea19eea08f7473dd4a6b103cb7651
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sphelppeerrequests-transact-sql"></a>sp_helppeerrequests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения обо всех запросах состояния, полученных участниками в топологии репликации одноранговая сеть, где эти запросы были инициированы выполнением [sp_requestpeerresponse &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) на любом этапе База данных, опубликованной в топологии. Эта хранимая процедура выполняется в базе данных публикации при участии издателя в топологии одноранговой репликации. Дополнительные сведения см. в разделе [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
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
 Значение, которое можно использовать для идентификации запросов состояния, который дает возможность позволяет фильтровать возвращенные ответы на основе пользовательской информации, предоставленной при вызове [sp_requestpeerresponse &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md). *Описание* — **nvarchar(4000)**, значение по умолчанию **%**. По умолчанию возвращается информация обо всех запросах состояния публикации. Этот параметр используется для возврата только тех запросов состояния с описанием соответствующих значению, переданному в *описание*, где сопоставлении строк символов с помощью [как &#40;Transact-SQL&#41; ](../../t-sql/language-elements/like-transact-sql.md)предложения.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор запроса.|  
|**Публикации**|**sysname**|Имя публикации, запрос состояния которой был отправлен.|  
|**sent_date**|**datetime**|Дата и время отправления запроса состояния.|  
|**Описание**|**nvarchar(4000)**|Пользовательская информация, которую можно использовать для идентификации запросов состояния.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_helppeerrequests** используется в репликации транзакций, одноранговая сеть.  
  
 **sp_helppeerrequests** используется при восстановлении базы данных, опубликованной в топологии одноранговая сеть.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_helppeerrequests**.  
  
## <a name="see-also"></a>См. также  
 [sp_deletepeerrequesthistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletepeerrequesthistory-transact-sql.md)   
 [sp_helppeerresponses &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md)  
  
  
