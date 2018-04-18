---
title: sp_marksubscriptionvalidation (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/16/2017
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
- sp_marksubscriptionvalidation
- sp_marksubscriptionvalidation_TSQL
helpviewer_keywords:
- sp_marksubscriptionvalidation
ms.assetid: e68fe0b9-5993-4880-917a-b0f661f8459b
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 774c796716705a61de3ab0885261a4838357902c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="spmarksubscriptionvalidation-transact-sql"></a>sp_marksubscriptionvalidation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Помечает текущую открытую транзакцию как транзакцию проверки уровня подписки для заданного подписчика. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_marksubscriptionvalidation [ @publication = ] 'publication'  
        , [ @subscriber = ] 'subscriber'  
        , [ @destination_db = ] 'destination_db'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@publication**=] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@subscriber**=] **"***подписчика***"**  
 Имя подписчика. *подписчик* имеет тип sysname и значение по умолчанию.  
  
 [  **@destination_db=**] **"***destination_db***"**  
 Имя целевой базы данных. *destination_db* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@publisher=** ] **"***издатель***"**  
 Указывает значение, отличное от[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не следует использовать для публикации, к которой принадлежит [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_marksubscriptionvalidation** используется в репликации транзакций.  
  
 **sp_marksubscriptionvalidation** не поддерживает отличных[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков.  
  
 Для не -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей, не удается выполнить **sp_marksubscriptionvalidation** из явной транзакции. Это обусловлено тем, что явные транзакции не поддерживаются через соединение связанного сервера, через которое осуществляется подключение к издателю.  
  
 **sp_marksubscriptionvalidation** необходимо использовать вместе с [sp_article_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md), указав значение **1** для  *процедурой*и может использоваться с другими вызовами **sp_marksubscriptionvalidation** Пометить текущую открытую транзакцию для других подписчиков.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_marksubscriptionvalidation**.  
  
## <a name="example"></a>Пример  
 Приведенный ниже запрос можно применять к публикующей базе данных для выполнения команд проверки уровня подписки. Эти команды выбираются агентами распространителя указанных подписчиков. Обратите внимание, что первая транзакция проверяет статью '**art1**, а для второго транзакция проверяет**art2**". Также Обратите внимание, что вызовы **sp_marksubscriptionvalidation** и [sp_article_validation &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) были инкапсулированы в транзакцию. Рекомендуется, чтобы только один вызов [sp_article_validation &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) за одну транзакцию. Это вызвано [sp_article_validation &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) удерживает разделяемую блокировку таблицы для исходной таблицы на время транзакции. Для повышения параллелизма следует добиваться как можно меньшей продолжительности транзакций.  
  
```  
begin tran  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub', @destination_db = 'SubDB'  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub2', @destination_db = 'SubDB'  
  
exec sp_article_validation @publication = 'pub1', @article = 'art1',  
 @rowcount_only = 0, @full_or_fast = 0, @shutdown_agent = 0,  
 @subscription_level = 1  
  
commit tran  
  
begin tran  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub', @destination_db = 'SubDB'  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub2', @destination_db = 'SubDB'  
  
exec sp_article_validation @publication = 'pub1', @article = 'art2',  
 @rowcount_only = 0, @full_or_fast = 0, @shutdown_agent = 0,  
 @subscription_level = 1  
  
commit tran  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Проверка реплицированных данных](../../relational-databases/replication/validate-replicated-data.md)  
  
  
