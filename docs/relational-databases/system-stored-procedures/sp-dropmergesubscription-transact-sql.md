---
title: sp_dropmergesubscription (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergesubscription_TSQL
- sp_dropmergesubscription
helpviewer_keywords:
- sp_dropmergesubscription
ms.assetid: 34244ae6-bd98-4a6a-bbd3-85f50edfcdc0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 34ba40387c246fe5f7f2de8dd74197b7cd43c0f5
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2019
ms.locfileid: "54130744"
---
# <a name="spdropmergesubscription-transact-sql"></a>sp_dropmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет подписку на публикацию слиянием и соответствующий агент слияния. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropmergesubscription [ [ @publication= ] 'publication' ]   
    [ , [ @subscriber= ] 'subscriber'    
    [ , [ @subscriber_db= ] 'subscriber_db' ]   
    [ , [ @subscription_type= ] 'subscription_type' ]   
    [ , [ @ignore_distributor = ] ignore_distributor ]   
    [ , [ @reserved = ] reserved ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=** ] **"**_публикации_**"**  
 Имя публикации. *Публикация* — **sysname**, значение по умолчанию NULL. Публикация уже должна существовать и соответствовать правилам идентификаторов.  
  
 [  **@subscriber=**] **"**_подписчика_**"**  
 Имя подписчика. *подписчик* — **sysname**, значение по умолчанию NULL.  
  
 [  **@subscriber_db=** ] **"**_subscriber_db_**"**  
 Имя базы данных подписки. *subscription_database*— **sysname**, значение по умолчанию NULL.  
  
 [  **@subscription_type=** ] **"**_subscription_type_**"**  
 Тип подписки. *subscription_type*— **nvarchar(15)**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Все**|Принудительные подписки, подписки по запросу и анонимные подписки.|  
|**Анонимный**|Анонимная подписка.|  
|**Push-уведомлений**|Принудительная подписка.|  
|**По запросу**|Подписка по запросу.|  
|**оба** (по умолчанию)|Как принудительная подписка, так и подписка по запросу.|  
  
 [  **@ignore_distributor =** ] *ignore_distributor*  
 Указывает, исполняется ли данная хранимая процедура без подключения к распространителю. *ignore_distributor* — **бит**, значение по умолчанию **0**. Этот аргумент может использоваться для удаления подписки без выполнения задач очистки на распространителе. Это полезно и в тех случаях, когда требуется переустановить распространитель.  
  
 [  **@reserved=** ] *зарезервированные*  
 Зарезервировано для использования в будущем. *зарезервированные* — **бит**, значение по умолчанию **0**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_dropmergesubscription** используется в репликации слиянием.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_dropmergesubscription](../../relational-databases/replication/codesnippet/tsql/sp-dropmergesubscription_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_dropmergesubscription**.  
  
## <a name="see-also"></a>См. также  
 [Удаление принудительной подписки](../../relational-databases/replication/delete-a-push-subscription.md)   
 [Удаление подписки по запросу](../../relational-databases/replication/delete-a-pull-subscription.md)   
 [sp_addmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_changemergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_helpmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)  
  
  
