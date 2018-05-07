---
title: sp_articleview (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_articleview
- sp_articleview_TSQL
helpviewer_keywords:
- sp_articleview
ms.assetid: a3d63fd6-f360-4a2f-8a82-a0dc15f650b3
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 68d7b62faa098eedb77bf1576020f01c090fcbd5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sparticleview-transact-sql"></a>sp_articleview (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [  **@publication=**] **"***публикации***"**  
 Имя публикации, которая содержит статью. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@article=**] **"***статьи***"**  
 Имя статьи. *статья* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@view_name=**] **"***view_name***"**  
 Имя представления, определяющего опубликованную статью. *view_name* — **nvarchar(386)**, значение по умолчанию NULL.  
  
 [  **@filter_clause=**] **"***filter_clause***"**  
 Предложение ограничения (WHERE), которое задает горизонтальный фильтр. При вводе предложения ограничения опустите ключевое слово WHERE. *filter_clause* — **ntext**, значение по умолчанию NULL.  
  
 [  **@change_active =** ] *change_active*  
 Разрешает изменение столбцов в публикациях, на которые имеются подписки. *change_active* — **int**, значение по умолчанию **0**. Если **0**, столбцы не изменяются. Если **1**, представления может быть создано или повторно создан на активных статей, на которые имеются подписки.  
  
 [  **@force_invalidate_snapshot =** ] *подписки потребуют*  
 Подтверждает, что действие, выполненное этой хранимой процедурой, может сделать недействительным существующий моментальный снимок. *подписки потребуют* — **бит**, значение по умолчанию **0**.  
  
 **0** указывает, что изменение статьи не приводит к недействительности моментального снимка. Если хранимая процедура определяет, что изменение требует создания нового моментального снимка, возникает ошибка и изменения не выполняются.  
  
 **1** указывает, что изменения статьи может привести к недействительности моментального снимка и если существующие подписки потребуют нового моментального снимка, дается разрешение существующий моментальный снимок помечается как устаревшего и создание нового моментального снимка.  
  
 [  **@force_reinit_subscription =]** *этот*  
 Подтверждает, что действие, выполняемое данной хранимой процедурой, может сделать необходимой повторную инициализацию текущих подписок. *Этот* — **бит** значение по умолчанию **0**.  
  
 **0** указывает, что изменения в статье не вызывают повторной инициализации подписки. Если хранимая процедура определяет, что изменение потребует повторной инициализации подписки, то выдается сообщение об ошибке, и изменения не производится.  
  
 **1** указывает на то, что изменения статьи вызывает существующую подписку для повторной инициализации и дает разрешение произвести повторную инициализацию подписки.  
  
 [ **@publisher**=] **"***издатель***"**  
 Указывает значение, отличное от[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не должны использоваться при публикации из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
 [ **@refreshsynctranprocs** =] *refreshsynctranprocs*  
 Указывает, будут ли хранимые процедуры, используемые для синхронизации репликации, автоматически создаваться повторно. *refreshsynctranprocs* — **бит**, значение по умолчанию 1.  
  
 **1** означает, что хранимые процедуры будут создаваться повторно.  
  
 **0** означает, что хранимые процедуры не будут создаваться повторно.  
  
 [ **@internal**=] *внутренний*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_articleview** создает представление, определяющее публикуемую статью, вставляет идентификатор этого представления в **sync_objid** столбец [sysarticles &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/sysarticles-transact-sql.md) таблицы и помещает текст ограничивающего предложения в **filter_clause** столбца. Если все столбцы реплицируются, а не **filter_clause**, **sync_objid** в [sysarticles &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/sysarticles-transact-sql.md) таблицы заданы идентификатор Базовая таблица, а также использование **sp_articleview** не является обязательным.  
  
 Для публикации вертикально фильтруемой таблицы (т.е., для фильтрации столбцов) сначала запустите **sp_addarticle** нет *sync_object* параметра, запустите [sp_articlecolumn &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) один раз для каждого столбца, чтобы быть реплицированы (определяя вертикальный фильтр), а затем запустите **sp_articleview** для создания представления, определяющего опубликованную статью.  
  
 Для публикации горизонтально фильтруемой таблицы (т.е. для фильтрации строк), запустите [sp_addarticle &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) нет *фильтра* параметра. Запустите [sp_articlefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md), указав все аргументы, включая *filter_clause*. Затем запустите **sp_articleview**, указав все аргументы, включая тот же *filter_clause*.  
  
 Для публикации вертикально и горизонтально фильтруемой таблицы, запустите [sp_addarticle &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) нет *sync_object* или *фильтра* параметров. Запустите [sp_articlecolumn &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) один раз для каждого реплицируемого столбца, а затем выполните [sp_articlefilter &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) и **sp_ articleview**.  
  
 Если у статьи уже существовало представление, определяющее публикуемую статью, **sp_articleview** удалит существующее представление и автоматически создаст новое. Если представление было создано вручную (**тип** в [sysarticles &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/sysarticles-transact-sql.md) — **5**), существующее представление не удаляется.  
  
 Если создается хранимая процедура пользовательского фильтра и представление, определяющее публикуемую статью вручную, не запускайте **sp_articleview**. Вместо этого указать их в качестве *фильтра* и *sync_object* параметры [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md), а также соответствующие *тип* значение.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-articleview-transact-_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_articleview**.  
  
## <a name="see-also"></a>См. также  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [Определение и изменение статического строкового фильтра](../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)   
 [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articlefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)   
 [sp_changearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
