---
title: sp_requestpeerresponse (Transact-SQL) | Документы Microsoft
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
- sp_requestpeerresponse_TSQL
- sp_requestpeerresponse
helpviewer_keywords:
- sp_requestpeerresponse
ms.assetid: cbe13c22-4d7d-4a36-b194-7a13ce68ef27
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 233189ee46144b4acd6e880f2f5b5875af551ff4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
 [ **@request_id** =] *идентификатор_запроса*  
 Возвращает идентификатор нового запроса. *идентификатор_запроса* — **int** и является ВЫХОДНЫМ параметром. Это значение может использоваться при выполнении [sp_helppeerresponses &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md) для просмотра всех ответов на запрос состояния.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_requestpeerresponse** используется в репликации транзакций, одноранговая сеть.  
  
 **sp_requestpeerresponse** позволяет убедиться, что все команды получены всеми другими узлами перед восстановлением базы данных, опубликованной в топологии одноранговая сеть. Эта процедура используется, если при репликации изменений языка DDL, выполненных, когда узел был в режиме «вне сети», необходимо оценить, когда эти изменения переданы на другие узлы.  
  
 **sp_requestpeerresponse** не может выполняться внутри пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_requestpeerresponse**.  
  
## <a name="see-also"></a>См. также  
 [sp_deletepeerrequesthistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletepeerrequesthistory-transact-sql.md)   
 [sp_helppeerrequests &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerrequests-transact-sql.md)  
  
  
