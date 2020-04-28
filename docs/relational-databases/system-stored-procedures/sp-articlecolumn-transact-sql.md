---
title: sp_articlecolumn (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_articlecolumn
- sp_articlecolumn_TSQL
helpviewer_keywords:
- sp_articlecolumn
ms.assetid: 8abaa8c1-d99e-4788-970f-c4752246c577
author: stevestein
ms.author: sstein
ms.openlocfilehash: acbbd043080b107a5d545408fabe271d62015e54
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68105080"
---
# <a name="sp_articlecolumn-transact-sql"></a>sp_articlecolumn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Используется для указания столбцов, включенных в статью, для вертикальной фильтрации данных в опубликованной таблице. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_articlecolumn [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @column = ] 'column' ]  
    [ , [ @operation = ] 'operation' ]  
    [ , [ @refresh_synctran_procs = ] refresh_synctran_procs ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
    [ , [ @change_active = ] change_actve ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @internal = ] 'internal' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации, содержащей эту статью. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @article = ] 'article'`Имя статьи. Аргумент *article* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @column = ] 'column'`Имя добавляемого или удаляемого столбца. *столбец* имеет тип **sysname**и значение по умолчанию NULL. Если значение равно NULL, публикуются все столбцы.  
  
`[ @operation = ] 'operation'`Указывает, следует ли добавлять или удалять столбцы в статье. *Операция* имеет тип **nvarchar (5)** и значение по умолчанию Add. **Добавить** помечает столбец для репликации. **Drop** отмечает столбец.  
  
`[ @refresh_synctran_procs = ] refresh_synctran_procs`Указывает, формируются ли повторно хранимые процедуры, поддерживающие немедленно обновляемые подписки, в соответствии с количеством реплицируемых столбцов. *refresh_synctran_procs* имеет **бит**и значение по умолчанию **1**. Если значение равно **1**, хранимые процедуры создаются повторно.  
  
`[ @ignore_distributor = ] ignore_distributor`Указывает, выполняется ли эта хранимая процедура без соединения с распространителем. *ignore_distributor* имеет **бит**и значение по умолчанию **0**. Если значение **равно 0**, то база данных должна быть включена для публикации, а кэш статей должен быть обновлен для отражения новых столбцов, реплицированных этой статьей. Значение **1**позволяет удалять столбцы статьи для статей, находящихся в неопубликованной базе данных. следует использовать только в ситуациях восстановления.  
  
`[ @change_active = ] change_active`Позволяет изменять столбцы в публикациях, у которых есть подписки. *change_active* является типом **int** и значением по умолчанию **0**. Если значение **равно 0**, то столбцы не изменяются. Если значение равно **1**, то столбцы можно добавлять или удалять из активных статей, у которых есть подписки.  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot`Подтверждает, что действие, выполняемое этой хранимой процедурой, может сделать существующий моментальный снимок недействительным. *force_invalidate_snapshot* является **битом**и имеет значение по умолчанию **0**.  
  
 **0** указывает, что изменения в статье не приводят к недействительности моментального снимка. Если хранимая процедура определяет, что изменение требует создания нового моментального снимка, возникает ошибка и изменения не выполняются.  
  
 значение **1** указывает, что изменения в статье могут привести к недействительности моментального снимка, и если существуют подписки, требующие создания нового моментального снимка, предоставляет разрешение на пометку существующего моментального снимка как устаревшего и создание нового моментального снимка.  
  
 [**@force_reinit_subscription =** ] *force_reinit_subscription*  
 Подтверждает, что действие, выполняемое данной хранимой процедурой, может сделать необходимой повторную инициализацию текущих подписок. *force_reinit_subscription* является **битом**и имеет значение по умолчанию **0**.  
  
 **0** указывает, что изменения в статье не приводят к повторной инициализации подписки. Если хранимая процедура определяет, что изменение потребует повторной инициализации подписки, то выдается сообщение об ошибке, и изменения не производится. **1** указывает, что изменения в статье приводят к повторной инициализации существующих подписок и предоставляют разрешение на повторную инициализацию подписки.  
  
`[ @publisher = ] 'publisher'`Указывает [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя, отличного от. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  *Издатель* не должен использоваться с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателем.  
  
`[ @internal = ] 'internal'`Только для внутреннего использования.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_articlecolumn** используется в репликации моментальных снимков и репликации транзакций.  
  
 Только статья, для которой отменена подписка, может быть отфильтрована с помощью **sp_articlecolumn**.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-articlecolumn-transac_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_articlecolumn**.  
  
## <a name="see-also"></a>См. также:  
 [Определение статьи](../../relational-databases/replication/publish/define-an-article.md)   
 [Определение и изменение фильтра столбцов](../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)   
 [Фильтровать опубликованные данные](../../relational-databases/replication/publish/filter-published-data.md)   
 [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articleview &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sp_helparticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
