---
title: хранимая процедура sp_articleview (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_articleview
- sp_articleview_TSQL
helpviewer_keywords:
- sp_articleview
ms.assetid: a3d63fd6-f360-4a2f-8a82-a0dc15f650b3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7cc40187ccafebee672214a0926a3ca0d0bc4176
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68768992"
---
# <a name="sp_articleview-transact-sql"></a>sp_articleview (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Создает представление, определяющее публикуемую статью, когда таблица фильтруется горизонтально или вертикально. Представление используется как фильтруемый источник схемы и данных для целевых таблиц. Эта хранимая процедура может изменять только те статьи, на которые нет подписки. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_articleview [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @view_name = ] 'view_name']  
    [ , [ @filter_clause = ] 'filter_clause']  
    [ , [ @change_active = ] change_active ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @refreshsynctranprocs = ] refreshsynctranprocs ]  
    [ , [ @internal = ] internal ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации, содержащей статью. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @article = ] 'article'`Имя статьи. Аргумент *article* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @view_name = ] 'view_name'`Имя представления, определяющего опубликованную статью. *view_name* имеет тип **nvarchar (386)** и значение по умолчанию NULL.  
  
`[ @filter_clause = ] 'filter_clause'`Предложение ограничения (WHERE), определяющее горизонтальный фильтр. При вводе предложения ограничения опустите ключевое слово WHERE. *filter_clause* является типом **ntext**и ЗНАЧЕНИЕМ по умолчанию NULL.  
  
`[ @change_active = ] change_active`Позволяет изменять столбцы в публикациях, у которых есть подписки. *change_active* имеет **тип int**и значение по умолчанию **0**. Если значение **равно 0**, столбцы не изменяются. Если значение равно **1**, то можно создать или повторно создать представления в активных статьях с подписками.  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot`Подтверждает, что действие, выполняемое этой хранимой процедурой, может сделать существующий моментальный снимок недействительным. параметр *force_invalidate_snapshot* имеет значение **bit**и значение по умолчанию **0**.  
  
 **0** указывает, что изменения в статье не приводят к недействительности моментального снимка. Если хранимая процедура определяет, что изменение требует создания нового моментального снимка, возникает ошибка и изменения не выполняются.  
  
 значение **1** указывает, что изменения в статье могут привести к недействительности моментального снимка, и если существуют подписки, требующие создания нового моментального снимка, предоставляет разрешение на пометку существующего моментального снимка как устаревшего и создание нового моментального снимка.  
  
`[ @force_reinit_subscription = ] _force_reinit_subscription_`Подтверждает, что действие, выполняемое этой хранимой процедурой, может потребовать повторной инициализации существующих подписок. параметр *force_reinit_subscription* имеет **бит** и значение по умолчанию **0**.  
  
 **0** указывает, что изменения в статье не приводят к повторной инициализации подписки. Если хранимая процедура определяет, что изменение потребует повторной инициализации подписки, то выдается сообщение об ошибке, и изменения не производится.  
  
 **1** указывает, что изменения в статье приводят к повторной инициализации существующей подписки и предоставляют разрешение на повторную инициализацию подписки.  
  
`[ @publisher = ] 'publisher'`Указывает [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя, отличного от. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  при публикации с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя не следует использовать издатель.  
  
`[ @refreshsynctranprocs = ] refreshsynctranprocs`Имеет значение, если хранимые процедуры, используемые для синхронизации репликации, автоматически создаются повторно. *рефрешсинктранпрокс* имеет **бит**и значение по умолчанию 1.  
  
 **1** означает, что хранимые процедуры созданы повторно.  
  
 **0** означает, что хранимые процедуры не создаются повторно.  
  
`[ @internal = ] internal` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 хранимая процедура **sp_articleview** создает представление, определяющее опубликованную статью, и вставляет идентификатор этого представления в столбец **sync_objid** таблицы [Transact &#40;&#41; -SQL sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md) и вставляет текст предложения ограничения в столбец **filter_clause** . Если все столбцы реплицируются и отсутствует **filter_clause**, **sync_objid** в таблице [Transact- &#40;SQL&#41; sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md) имеет идентификатор базовой таблицы, а использование хранимой инструкции **sp_articleview** не требуется.  
  
 Чтобы опубликовать таблицу с вертикальным фильтром (то есть для фильтрации столбцов), сначала выполните хранимую процедуру **sp_addarticle** без параметра *sync_object* , а затем выполните [sp_articlecolumn &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) по одному разу для каждого столбца, который будет реплицирован (определение вертикальный фильтр), а затем выполните хранимую процедуру **sp_articleview** , чтобы создать представление, определяющее опубликованную статью.  
  
 Чтобы опубликовать таблицу с горизонтальным фильтром (то есть для фильтрации строк), [выполните &#40;хранимую процедуру&#41; sp_addarticle Transact-SQL](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) без параметра *Filter* . Запустите [sp_articlefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md), указав все параметры, включая *filter_clause*. Затем запустите хранимую процедуру **sp_articleview**, указав все параметры, включая идентичные *filter_clause*.  
  
 Чтобы опубликовать вертикальную и горизонтально отфильтрованную таблицу, выполните хранимую процедуру [sp_addarticle &#40;Transact-&#41; SQL](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) без параметров *sync_object* или *Filter* . Запустите [sp_articlecolumn &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) один раз для каждого реплицируемого столбца, а затем выполните [инструкции sp_articlefilter &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) и **sp_articleview**.  
  
 Если статья уже содержит представление, определяющее опубликованную статью, хранимая процедура **sp_articleview** удаляет существующее представление и автоматически создает новый. Если представление было создано вручную (**введите** [sysarticles &#40;Transact&#41; -SQL](../../relational-databases/system-tables/sysarticles-transact-sql.md) — **5**), существующее представление не удаляется.  
  
 Если вы создаете хранимую процедуру настраиваемого фильтра и представление, которое определяет опубликованную статью вручную, не запускайте **sp_articleview**. Вместо этого укажите их в качестве параметров *Filter* и *sync_object* для хранимой процедуры [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)вместе с соответствующим значением *типа* .  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-articleview-transact-_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять хранимую процедуру **sp_articleview**.  
  
## <a name="see-also"></a>См. также  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [Определение и изменение статического строкового фильтра](../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)   
 [хранимая процедуры sp_addarticle &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articlefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)   
 [sp_changearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
