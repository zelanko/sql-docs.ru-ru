---
title: sp_marksubscriptionvalidation (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_marksubscriptionvalidation
- sp_marksubscriptionvalidation_TSQL
helpviewer_keywords:
- sp_marksubscriptionvalidation
ms.assetid: e68fe0b9-5993-4880-917a-b0f661f8459b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c440247433404c520559d6609bd4690b425ddd43
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85899342"
---
# <a name="sp_marksubscriptionvalidation-transact-sql"></a>sp_marksubscriptionvalidation (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @subscriber = ] 'subscriber'`Имя подписчика. Аргумент *Subscriber* имеет тип sysname и не имеет значения по умолчанию.  
  
`[ @destination_db = ] 'destination_db'`Имя целевой базы данных. Аргумент *destination_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher = ] 'publisher'`Указывает издателя, отличного от [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  *Издатель* не следует использовать для публикации, которая принадлежит [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателю.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 **sp_marksubscriptionvalidation** используется в репликации транзакций.  
  
 **sp_marksubscriptionvalidation** не поддерживает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков, отличных от.  
  
 Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей, отличных от, нельзя выполнять **sp_marksubscriptionvalidation** в явной транзакции. Это обусловлено тем, что явные транзакции не поддерживаются через соединение связанного сервера, через которое осуществляется подключение к издателю.  
  
 **sp_marksubscriptionvalidation** необходимо использовать вместе с [sp_article_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md), указав значение **1** для *subscription_level*и можно использовать с другими вызовами в **sp_marksubscriptionvalidation** , чтобы отметить текущую открытую транзакцию для других подписчиков.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_marksubscriptionvalidation**.  
  
## <a name="example"></a>Пример  
 Приведенный ниже запрос можно применять к публикующей базе данных для выполнения команд проверки уровня подписки. Эти команды выбираются агентами распространителя указанных подписчиков. Обратите внимание, что первая транзакция проверяет статью "**art1**", а вторая транзакция проверяет "**art2**". Также обратите внимание, что вызовы **sp_marksubscriptionvalidation** и [sp_article_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) были инкапсулированы в транзакции. Рекомендуется только один вызов [sp_article_validation &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) на транзакцию. Это обусловлено тем, что [sp_article_validation &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) содержит блокировку общей таблицы в исходной таблице на протяжении транзакции. Для повышения параллелизма следует добиваться как можно меньшей продолжительности транзакций.  
  
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
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Проверка реплицированных данных](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  
