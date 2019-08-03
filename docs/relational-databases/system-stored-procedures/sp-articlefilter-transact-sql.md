---
title: sp_articlefilter (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_articlefilter_TSQL
- sp_articlefilter
helpviewer_keywords:
- sp_articlefilter
ms.assetid: 4c3fee32-a43f-4757-a029-30aef4696afb
author: stevestein
ms.author: sstein
ms.openlocfilehash: d90cd0ba957da820ce5a937ae687e39ca0302025
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68769060"
---
# <a name="sparticlefilter-transact-sql"></a>sp_articlefilter (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Фильтрует данные, опубликованные на основе статьи таблицы. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_articlefilter [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @filter_name = ] 'filter_name' ]  
    [ , [ @filter_clause = ] 'filter_clause' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации, содержащей статью. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @article = ] 'article'`Имя статьи. Аргумент *article* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @filter_name = ] 'filter_name'`Имя хранимой процедуры Filter, создаваемой из *filter_name*. *filter_name* имеет тип **nvarchar (386)** и значение по умолчанию NULL. Необходимо указать уникальное имя для фильтра статьи.  
  
`[ @filter_clause = ] 'filter_clause'`Предложение ограничения (WHERE), определяющее горизонтальный фильтр. При вводе предложения ограничения опустите ключевое слово WHERE. *filter_clause* является типом **ntext**и ЗНАЧЕНИЕМ по умолчанию NULL.  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot`Подтверждает, что действие, выполняемое этой хранимой процедурой, может сделать существующий моментальный снимок недействительным. параметр *force_invalidate_snapshot* имеет значение **bit**и значение по умолчанию **0**.  
  
 **0** указывает, что изменения в статье не приводят к недействительности моментального снимка. Если хранимая процедура определяет, что изменение требует создания нового моментального снимка, возникает ошибка и изменения не выполняются.  
  
 значение **1** указывает, что изменения в статье могут привести к недействительности моментального снимка, и если существуют подписки, требующие создания нового моментального снимка, предоставляет разрешение на пометку существующего моментального снимка как устаревшего и создание нового моментального снимка.  
  
`[ @force_reinit_subscription = ] force_reinit_subscription`Подтверждает, что действие, выполняемое этой хранимой процедурой, может потребовать повторной инициализации существующих подписок. параметр *force_reinit_subscription* имеет значение **bit**и значение по умолчанию **0**.  
  
 **0** указывает, что изменения в статье не приводят к необходимости повторной инициализации подписок. Если хранимая процедура определяет, что изменение потребует повторной инициализации подписки, то выдается сообщение об ошибке, и изменения не производится.  
  
 **1** указывает, что изменения в статье приводят к повторной инициализации существующих подписок и предоставляют разрешение на повторную инициализацию подписки.  
  
`[ @publisher = ] 'publisher'`Указывает [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя, отличного от. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  *Издатель* не должен использоваться с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателем.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_articlefilter** используется в репликации моментальных снимков и репликации транзакций.  
  
 Для исполнения **sp_articlefilter** для статьи с существующими подписками необходимо повторно инициализировать эти подписки.  
  
 **sp_articlefilter** создает фильтр, вставляет идентификатор хранимой процедуры Filter в столбец **Filter** таблицы [Transact- &#40;&#41; SQL sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md) , а затем вставляет текст предложения ограничения в **фильтр. столбец _clause** .  
  
 Чтобы создать статью с горизонтальным фильтром, выполните [хранимую процедуру &#40;sp_addarticle&#41; Transact-SQL](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) без параметра *Filter* . Выполните **sp_articlefilter**, указав все параметры, включая *filter_clause*, а затем выполните хранимую процедуру [sp_articleview &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md), указав все параметры, включая идентичные *filter_clause*. Если фильтр уже существует и **тип** в **sysarticles** равен **1** (статья на основе журнала), то предыдущий фильтр удаляется и создается новый фильтр.  
  
 Если *filter_name* и *filter_clause* не указаны, предыдущий фильтр удаляется, а идентификатор фильтра устанавливается в **0**.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-articlefilter-transac_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_articlefilter**.  
  
## <a name="see-also"></a>См. также  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [Определение и изменение статического строкового фильтра](../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)   
 [хранимая процедуры sp_addarticle &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [хранимая процедура sp_articleview &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)   
 [sp_changearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
