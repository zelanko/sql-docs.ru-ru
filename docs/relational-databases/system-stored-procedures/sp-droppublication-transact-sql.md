---
title: sp_droppublication (Transact-SQL) | Документация Майкрософт
description: Удаляет публикацию и ассоциированный с ней агент моментальных снимков. Эта хранимая процедура выполняется на издателе в базе данных публикации.
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_droppublication_TSQL
- sp_droppublication
helpviewer_keywords:
- sp_droppublication
ms.assetid: b52b37e6-4fec-40cf-abba-7dce4ff395fd
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5ae91db140ea261a6417cb08eae07cfe2eb7fb79
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89538941"
---
# <a name="sp_droppublication-transact-sql"></a>sp_droppublication (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Удаляет публикацию и ассоциированный с ней агент моментальных снимков. Прежде чем удалять публикацию, необходимо удалить все подписки. Статьи в публикации удаляются автоматически. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_droppublication [ @publication= ] 'publication'   
    [ , [ @ignore_distributor = ] ignore_distributor ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` Имя удаляемой публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию. Если указано значение **ALL** , все публикации удаляются из базы данных публикации, за исключением тех, для которых используются подписки.  
  
`[ @ignore_distributor = ] ignore_distributor` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_droppublication** используется в репликации моментальных снимков и репликации транзакций.  
  
 **sp_droppublication** рекурсивно удаляет все статьи, связанные с публикацией, а затем удаляет саму публикацию. Публикацию нельзя удалить, если у нее есть хотя бы одна подписка. Сведения об удалении подписок см. в разделе [Удаление принудительной подписки](../../relational-databases/replication/delete-a-push-subscription.md) и [Удаление подписки по запросу](../../relational-databases/replication/delete-a-pull-subscription.md).  
  
 При запуске **sp_droppublication** для удаления публикации не удаляются опубликованные объекты из базы данных публикации или соответствующие объекты из базы данных подписки. Используйте инструкцию DROP \<object> для удаления этих объектов вручную при необходимости.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_droppublication**.  
  
## <a name="examples"></a>Примеры  
 [!code-sql[HowTo#sp_droppublication](../../relational-databases/replication/codesnippet/tsql/sp-droppublication-trans_1.sql)]  
  
## <a name="see-also"></a>См. также  
 [Удаление публикации](../../relational-databases/replication/publish/delete-a-publication.md)   
 [sp_addpublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_helppublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
