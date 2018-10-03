---
title: sp_requestpeerresponse (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_requestpeerresponse_TSQL
- sp_requestpeerresponse
helpviewer_keywords:
- sp_requestpeerresponse
ms.assetid: cbe13c22-4d7d-4a36-b194-7a13ce68ef27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 300ff762ee7fbcefcd593cf3d7dd9ff0e81fcfed
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47821642"
---
# <a name="sprequestpeerresponse-transact-sql"></a>sp_requestpeerresponse (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  При выполнении на узле в одноранговой топологии эта процедура запрашивает ответ от всех остальных узлов в топологии. Выполнив эту процедуру и просмотрев соответствующие ответы, пользователь может быть уверен, что все предыдущие команды были доставлены в узлы, из которых получены ответы. Эта хранимая процедура выполняется в запрашивающем узле в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_requestpeerresponse [ @publication = ] 'publication'  
    [ , [ @description = ] 'description'  
    [ , [ @request_id = ] request_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@publication**=] **"***публикации***"**  
 Имя публикации в одноранговой топологии, для которой проверяется состояние. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@description**=] **"***описание***"**  
 Определяемые пользователем данные, которые могут использоваться для идентификации отдельных запросов состояния. *Описание* — **nvarchar(4000)**, значение по умолчанию NULL.  
  
 [ **@request_id** =] *request_id*  
 Возвращает идентификатор нового запроса. *Идентификатор request_id* — **int** и является ВЫХОДНЫМ параметром. Это значение может быть использовано при выполнении [sp_helppeerresponses &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md) для просмотра всех ответов на запрос состояния.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_requestpeerresponse** используется в репликации транзакций peer-to-peer.  
  
 **sp_requestpeerresponse** позволяют гарантировать, что все команды были получены всеми другими узлами перед восстановлением базы данных, опубликованной в топологии peer-to-peer. Эта процедура используется, если при репликации изменений языка DDL, выполненных, когда узел был в режиме «вне сети», необходимо оценить, когда эти изменения переданы на другие узлы.  
  
 **sp_requestpeerresponse** не может выполняться внутри пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_requestpeerresponse**.  
  
## <a name="see-also"></a>См. также  
 [sp_deletepeerrequesthistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletepeerrequesthistory-transact-sql.md)   
 [sp_helppeerrequests &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerrequests-transact-sql.md)  
  
  
