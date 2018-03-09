---
title: "sp_deletetracertokenhistory (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_deletetracertokenhistory
- sp_deletetracertokenhistory_TSQL
helpviewer_keywords:
- sp_deletetracertokenhistory
ms.assetid: 9ae1be14-0d2f-40b1-9d6e-22d79726abf4
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b9e130ffe0853d899bcacd63c35d7987c9981329
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spdeletetracertokenhistory-transact-sql"></a>sp_deletetracertokenhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет записи о трассировочных токенах из [MStracer_tokens &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) и [MStracer_history &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/mstracer-history-transact-sql.md) системных таблиц. Эта хранимая процедура выполняется на издателе в базе данных публикации или на распространителе в базе данных распространителя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_deletetracertokenhistory [ @publication = ] 'publication'   
    [ , [ @tracer_id = ] tracer_id ]  
    [ , [ @cutoff_date = ] cutoff_date ]  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @publisher_db = ] 'publisher_db' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=** ] **"***публикации***"**  
 Имя публикации, в которую была вставлена запись трассировочного токена. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@tracer_id=** ] *tracer_id*  
 Идентификатор трассировочного токена, который требуется удалить. *tracer_id* — **int**, значение по умолчанию NULL. Если **null**, то все трассировочные токены публикации удаляются.  
  
 [  **@cutoff_date=** ] *cutoff_date*  
 Задает конечную дату так, что все трассировочные токены, созданные ранее указанной даты, удаляются. *cutoff_date* имеет тип datetime и значение по умолчанию NULL.  
  
 [  **@publisher=** ] **"***издатель***"**  
 Имя издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Этот параметр должен быть указан только для не -[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей.  
  
 [  **@publisher_db=** ] **"***publisher_db***"**  
 Имя базы данных публикации. *publisher_db* — **sysname**, значение по умолчанию NULL. Этот параметр не учитывается, если хранимая процедура выполняется на издателе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_deletetracertokenhistory** используется в репликации транзакций.  
  
 При выполнении **sp_deletetracertokenhistory**, можно указать только один из *tracer_id* или *cutoff_date*. При задании обоих параметров возвращается ошибка.  
  
 Если не выполнить **sp_deletetracertokenhistory** для удаления метаданных по трассировочным токенам, данные будут удалены при плановой очистки журнала.  
  
 Идентификаторы трассировочных токенов, которые можно определить, выполнив [sp_helptracertokens &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md) или запросив [MStracer_tokens &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) системной таблицы.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера **db_owner** предопределенной роли базы данных в базе данных публикации или **db_owner** базы данных или  **replmonitor** роли в базе данных распространителя могут выполнять процедуру **sp_deletetracertokenhistory**.  
  
## <a name="see-also"></a>См. также:  
 [Измерение задержки и проверка правильности соединений для репликации транзакций](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)   
 [sp_helptracertokenhistory &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md)  
  
  
