---
title: "sp_addmergefilter (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_addmergefilter
- sp_addmergefilter_TSQL
helpviewer_keywords: sp_addmergefilter
ms.assetid: 4c118cb1-2008-44e2-a797-34b7dc34d6b1
caps.latest.revision: "49"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bae5cbac50c347247bba5b0488a7fb70ad8e71a3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spaddmergefilter-transact-sql"></a>sp_addmergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет новый фильтр слияния для создания секции на базе соединения с другой таблицей. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addmergefilter [ @publication = ] 'publication'   
        , [ @article = ] 'article'   
        , [ @filtername = ] 'filtername'   
        , [ @join_articlename = ] 'join_articlename'   
        , [ @join_filterclause = ] join_filterclause  
    [ , [ @join_unique_key = ] join_unique_key ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @filter_type = ] filter_type ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=** ] **"***публикации***"**  
 Имя публикации, к которой добавляется фильтр слияния. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@article=** ] **"***статьи***"**  
 Имя статьи, к которой добавляется фильтр слияния. *статья* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@filtername=** ] **"***filtername***"**  
 Имя фильтра. *FilterName* является обязательным. *FilterName*— **sysname**, не имеет значения по умолчанию.  
  
 [  **@join_articlename=** ] **"***join_articlename***"**  
 Родительская статья, к которой дочерняя статья, указанная с *статьи*, должны быть соединены с помощью предложения join, указанного по *join_filterclause*, чтобы определить строки дочерней статьи, соответствующие критерию фильтрации фильтра слияния. *join_articlename* — **sysname**, не имеет значения по умолчанию. Статья должна находиться в публикации, указанной аргументом *публикации*.  
  
 [  **@join_filterclause=** ] *join_filterclause*  
 Предложение соединения, который должен использоваться для соединения дочерней статьи, указанной по *статьи*и родительской статьей, указанной аргументом *join_article*, чтобы определить строки, указывающие фильтр слияния. *join_filterclause* — **nvarchar(1000)**.  
  
 [  **@join_unique_key=** ] *join_unique_key*  
 Указывает, если соединение между дочерней статьей *статьи*и родительской статьей *join_article*один ко многим, один к одному, многие к одному или многие ко многим. *join_unique_key* — **int**, значение по умолчанию 0. **0** указывает многие к одному "или" многие ко многим соединения. **1** указывает одному "или" один ко многим соединения. Это значение является **1** при присоединении столбцы формируют уникальный ключ в *join_article*, или если *join_filterclause* между внешним ключом в *статье* и первичный ключ в *join_article*.  
  
> [!CAUTION]  
>  Этот параметр устанавливается только **1** при наличии ограничения на соединяющийся столбец в базовой таблице для родительской статьи, гарантирующее уникальность. Если *join_unique_key* равно **1** неправильно, конвергенции данных может возникнуть.  
  
 [  **@force_invalidate_snapshot=** ] *подписки потребуют*  
 Подтверждает, что действие, выполненное этой хранимой процедурой, может сделать недействительным существующий моментальный снимок. *подписки потребуют* — **бит**, значение по умолчанию **0**.  
  
 **0** указывает, что изменения статьи слияния не приведут к недействительности моментального снимка. Если хранимая процедура определяет, что изменение требует создания нового моментального снимка, то возникает ошибка, и изменение не выполняется.  
  
 **1** указывает, что изменения статьи слияния может привести к недействительности моментального снимка и если существующие подписки потребуют нового моментального снимка, дается разрешение существующий моментальный снимок помечается как устаревший и создания нового моментального снимка создан.  
  
 [  **@force_reinit_subscription=** ] *этот*  
 Подтверждает, что действие, выполняемое данной хранимой процедурой, может сделать необходимой повторную инициализацию текущих подписок. *Этот* — **бит**, значение по умолчанию 0.  
  
 **0** указывает, что изменения статьи слияния не приведут к повторной инициализации подписки. Если хранимая процедура определит, что изменение потребует повторной инициализации подписки, то выдается сообщение об ошибке и изменения не производятся.  
  
 **1** указывает, что изменения в статье слияния приведут существующих подписок для повторной инициализации и дает разрешение произвести повторную инициализацию подписки.  
  
 [  **@filter_type=** ] *filter_type*  
 Указывает тип добавляемого фильтра. *filter_type* — **tinyint**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Только фильтр соединения. Необходим для поддержки подписчиков [!INCLUDE[ssEW](../../includes/ssew-md.md)].|  
|**2**|Только связь логических записей.|  
|**3**|Как фильтр соединения, так и связь логических записей.|  
  
 Дополнительные сведения см. в статье [Группирование изменений в связанных строках с помощью логических записей](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_addmergefilter** используется в репликации слиянием.  
  
 **sp_addmergefilter** может использоваться только со статьями таблиц. Статьи представлений и индексированных представлений не поддерживаются.  
  
 Эта процедура также может быть использована для формирования логической взаимосвязи между двумя статьями, между которыми может существовать или отсутствовать фильтр соединения. *filter_type* используется для указания, если добавляется фильтр слияния является фильтром соединения, логической взаимосвязи или оба.  
  
 Для использования логических записей публикация и статьи должны удовлетворять определенным требованиям. Дополнительные сведения см. в статье [Группирование изменений в связанных строках с помощью логических записей](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
 Как правило, этот параметр используется для статьи с внешним ключом, указывающим на опубликованную таблицу первичного ключа, а таблица первичного ключа имеет фильтр, определенный в статье. Подмножество строк первичного ключа используется для определения строк внешнего ключа, реплицируемых в подписчика.  
  
 Между двумя опубликованными статьями можно вставить фильтр соединения, если исходные таблицы обеих статей имеют общее имя объекта таблицы. В этом случае, даже если обе таблицы принадлежат различным схемам и имеют уникальные имена статей, создание фильтра соединения завершится неудачей.  
  
 Если как параметризованный фильтр строк, так и фильтр соединения применяются к статье таблицы, то репликация определяет, принадлежит ли строка к секции подписчика. Она достигается путем расчета функции фильтрации или фильтра соединения (с помощью [или](../../t-sql/language-elements/or-transact-sql.md) оператор), а не поиском пересечения двух условий (с помощью [AND](../../t-sql/language-elements/and-transact-sql.md) оператор).  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_addmergefilter](../../relational-databases/replication/codesnippet/tsql/sp-addmergefilter-transa_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_addmergefilter**.  
  
## <a name="see-also"></a>См. также:  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [Define and Modify a Join Filter Between Merge Articles](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [Join Filters](../../relational-databases/replication/merge/join-filters.md)   
 [sp_changemergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_dropmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [Хранимая процедура sp_helpmergefilter &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
