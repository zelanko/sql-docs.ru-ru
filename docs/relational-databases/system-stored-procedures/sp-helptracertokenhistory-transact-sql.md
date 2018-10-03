---
title: sp_helptracertokenhistory (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_helptracertokenhistory_TSQL
- sp_helptracertokenhistory
helpviewer_keywords:
- sp_helptracertokenhistory
ms.assetid: 96910d1c-be76-43eb-9c93-4477e6761749
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7c56ad691f960e083a4fa4f7c655808638215c46
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47725132"
---
# <a name="sphelptracertokenhistory-transact-sql"></a>sp_helptracertokenhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает подробные сведения о задержке для указанных трассировочных токенов, причем для каждого подписчика возвращается одна строка. Эта хранимая процедура выполняется на издателе в базе данных публикации или на распространителе в базе данных распространителя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helptracertokenhistory [ @publication = ] 'publication'   
        , [ @tracer_id = ] tracer_id  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=** ] **"***публикации***"**  
 Имя публикации, в которую была вставлена запись трассировочного токена. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@tracer_id=** ] *tracer_id*  
 Идентификатор трассировочного токена в [MStracer_tokens &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) таблицы, для которых сведения возвращаются из журнала. *tracer_id* — **int**, не имеет значения по умолчанию.  
  
 [  **@publisher=** ] **"***издателя***"**  
 Имя издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Этот параметр должен быть указан только для не -[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей.  
  
 [  **@publisher_db=** ] **"***publisher_db***"**  
 Имя базы данных публикации. *publisher_db* — **sysname**, со значением по умолчанию NULL. Этот параметр не учитывается, если хранимая процедура выполняется на издателе.  
  
## <a name="result-set"></a>Результирующий набор  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**distributor_latency**|**bigint**|Количество секунд между фиксированием записи трассировочного токена у издателя и фиксированием записи у распространителя.|  
|**подписчик**|**sysname**|Имя подписчика, получившего трассировочный токен.|  
|**subscriber_db**|**sysname**|Имя базы данных подписки, в которую была вставлена запись трассировочного токена.|  
|**subscriber_latency**|**bigint**|Количество секунд между фиксированием записи трассировочного токена у распространителя и фиксированием записи у подписчика.|  
|**overall_latency**|**bigint**|Количество секунд между фиксированием записи трассировочного токена у издателя и фиксированием записи трассировочного токена у подписчика.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_helptracertokenhistory** используется в репликации транзакций.  
  
 Выполнение [sp_helptracertokens &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md) для получения списка трассировочных токенов для публикации.  
  
 Значение NULL в результирующем наборе означает, что статистика задержек не может быть определена. Причина этого в том, что трассировочный токен не был получен распространителем или одним из подписчиков.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_tracertokens](../../relational-databases/replication/codesnippet/tsql/sp-helptracertokenhistor_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера, **db_owner** предопределенной роли базы данных в базе данных публикации или **db_owner** базы данных или  **replmonitor** ролей в базе данных распространителя могут выполнять процедуру **sp_helptracertokenhistory**.  
  
## <a name="see-also"></a>См. также  
 [Измерение задержки и проверка правильности соединений для репликации транзакций](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)   
 [sp_deletetracertokenhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql.md)  
  
  
