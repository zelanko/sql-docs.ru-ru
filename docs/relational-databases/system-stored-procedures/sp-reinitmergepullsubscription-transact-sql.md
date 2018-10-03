---
title: sp_reinitmergepullsubscription (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_reinitmergepullsubscription
- sp_reinitmergepullsubscription_TSQL
helpviewer_keywords:
- sp_reinitmergepullsubscription
ms.assetid: 48464bc9-60aa-4886-b526-163f010102b8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e1f826b48896dda673dc7d34dd13357e169961f4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47756532"
---
# <a name="spreinitmergepullsubscription-transact-sql"></a>sp_reinitmergepullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отмечает объединенные подписки по запросу для повторной инициализации при следующем запуске агента слияния. Эта хранимая процедура выполняется в базе данных подписки на подписчике.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_reinitmergepullsubscription [ [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @upload_first = ] 'upload_first'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@publisher** =] **"***издателя***"**  
 Имя издателя. *издатель* — **sysname**, значение по умолчанию все.  
  
 [ **@publisher_db** =] **"***publisher_db***"**  
 Имя базы данных издателя. *publisher_db* — **sysname**, значение по умолчанию все.  
  
 [ **@publication** =] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, значение по умолчанию все.  
  
 [ **@upload_first** =] **"***upload_first***"**  
 Показывает, будут ли изменения на подписчике переданы перед повторной инициализацией подписки. *upload_first* — **nvarchar(5)**, значение по умолчанию FALSE. Если **true**, изменения передаются перед повторной инициализацией подписки. Если **false**, изменения не передаются.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_reinitmergepullsubscription** используется в репликации слиянием.  
  
 Если добавить, удалить или изменить параметризованный фильтр, ожидающие обработки изменения подписчика нельзя будет передать издателю во время повторной инициализации. Если нужно передать изменения, ожидающие обработки, то перед изменением фильтра необходимо синхронизировать все подписки.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_reinitmergepullsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitmergepullsubscr_1.sql)]  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_reinitmergepullsubwithupload](../../relational-databases/replication/codesnippet/tsql/sp-reinitmergepullsubscr_2.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_reinitmergepullsubscription**.  
  
## <a name="see-also"></a>См. также  
 [Повторная инициализация подписки](../../relational-databases/replication/reinitialize-a-subscription.md)   
 [Повторная инициализация подписок](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
