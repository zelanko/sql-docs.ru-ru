---
title: sp_reinitmergesubscription (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_reinitmergesubscription_TSQL
- sp_reinitmergesubscription
helpviewer_keywords:
- sp_reinitmergesubscription
ms.assetid: 249a4048-e885-48e0-a92a-6577f59de751
author: stevestein
ms.author: sstein
ms.openlocfilehash: 27c10f9d5fa04ae449bdcca84891f0f28376eeb6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68075702"
---
# <a name="spreinitmergesubscription-transact-sql"></a>sp_reinitmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Помечает подписку слиянием для повторной инициализации при следующем запуске агента слияния. Эта хранимая процедура запущена на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_reinitmergesubscription [ [ @publication = ] 'publication'  
    [ , [ @subscriber = ] 'subscriber'  
    [ , [ @subscriber_db = ] 'subscriber_db'  
    [ , [ @upload_first = ] 'upload_first'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` — Имя публикации. *Публикация* — **sysname**, значение по умолчанию **все**.  
  
`[ @subscriber = ] 'subscriber'` — Имя подписчика. *подписчик* — **sysname**, значение по умолчанию **все**.  
  
`[ @subscriber_db = ] 'subscriber_db'` — Имя базы данных подписчика. *subscriber_db* — **sysname**, значение по умолчанию **все**.  
  
`[ @upload_first = ] 'upload_first'` — Будут ли изменения на подписчике переданы перед повторной инициализацией подписки. *upload_first* — **nvarchar(5)** , значение по умолчанию FALSE. Если **true**, изменения передаются перед повторной инициализацией подписки. Если **false**, изменения не передаются.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_reinitmergesubscription** используется в репликации слиянием.  
  
 **sp_reinitmergesubscription** могут вызываться из издателя для повторной инициализации подписок на публикацию слиянием. Также рекомендуется перезапустить агент моментальных снимков.  
  
 Если добавить, удалить или изменить параметризованный фильтр, ожидающие обработки изменения подписчика нельзя будет передать издателю во время повторной инициализации. Если нужно передать изменения, ожидающие обработки, то перед изменением фильтра необходимо синхронизировать все подписки.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_reinitmergepushsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitmergesubscripti_1.sql)]  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_reinitmergepushsubwithupload](../../relational-databases/replication/codesnippet/tsql/sp-reinitmergesubscripti_2.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_reinitmergesubscription**.  
  
## <a name="see-also"></a>См. также  
 [Повторная инициализация подписок](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
