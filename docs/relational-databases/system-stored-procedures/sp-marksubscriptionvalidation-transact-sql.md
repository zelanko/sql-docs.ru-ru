---
title: sp_marksubscriptionvalidation (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_marksubscriptionvalidation
- sp_marksubscriptionvalidation_TSQL
helpviewer_keywords:
- sp_marksubscriptionvalidation
ms.assetid: e68fe0b9-5993-4880-917a-b0f661f8459b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c4d649403a04aa48475705059328656d81ae8597
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47748912"
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
  
 [  **@publisher=** ] **"***издателя***"**  
 Указывает, отличный от[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не следует использовать для публикации, к которой принадлежит [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_marksubscriptionvalidation** используется в репликации транзакций.  
  
 **sp_marksubscriptionvalidation** не поддерживает отличных[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков.  
  
 Для не -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей, не удается выполнить **sp_marksubscriptionvalidation** из явной транзакции. Это обусловлено тем, что явные транзакции не поддерживаются через соединение связанного сервера, через которое осуществляется подключение к издателю.  
  
 **sp_marksubscriptionvalidation** должен использоваться вместе с [sp_article_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md), указав значение **1** для  *уровень_подписки*и может использоваться с другими вызовами **sp_marksubscriptionvalidation** Пометить текущую открытую транзакцию для других подписчиков.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_marksubscriptionvalidation**.  
  
## <a name="example"></a>Пример  
 Приведенный ниже запрос можно применять к публикующей базе данных для выполнения команд проверки уровня подписки. Эти команды выбираются агентами распространителя указанных подписчиков. Обратите внимание, что первая транзакция проверяет статью '**art1**«, а вторая транзакция проверяет»**art2**". Также Обратите внимание, что вызовы **sp_marksubscriptionvalidation** и [sp_article_validation &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) инкапсулированы в транзакцию. Мы рекомендуем использовать только один вызов [sp_article_validation &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) за одну транзакцию. Это обусловлено [sp_article_validation &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) удерживает разделяемую блокировку таблицы для исходной таблицы в течение транзакции. Для повышения параллелизма следует добиваться как можно меньшей продолжительности транзакций.  
  
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
  
  
