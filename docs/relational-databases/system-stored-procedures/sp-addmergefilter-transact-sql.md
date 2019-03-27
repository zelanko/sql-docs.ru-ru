---
title: sp_addmergefilter (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergefilter
- sp_addmergefilter_TSQL
helpviewer_keywords:
- sp_addmergefilter
ms.assetid: 4c118cb1-2008-44e2-a797-34b7dc34d6b1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6f2843456f4f95d1019b51f82082d59977ce14d5
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493699"
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
`[ @publication = ] 'publication'` — Имя публикации, в которой добавляется фильтр слияния. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
`[ @article = ] 'article'` — Имя статьи, к которой добавляется фильтр слияния. *статья* — **sysname**, не имеет значения по умолчанию.  
  
`[ @filtername = ] 'filtername'` — Имя фильтра. *FilterName* является обязательным параметром. *FilterName*— **sysname**, не имеет значения по умолчанию.  
  
`[ @join_articlename = ] 'join_articlename'` Родительская статья, к которой дочерняя статья, указанная с *статье*, должны быть соединены с помощью предложения join, указанного по *join_filterclause*, чтобы определить строки дочерней статьи, которые соответствуют критерию фильтрации фильтра слияния. *join_articlename* — **sysname**, не имеет значения по умолчанию. Статья должна находиться в публикации, указанной аргументом *публикации*.  
  
`[ @join_filterclause = ] join_filterclause` Предложение соединения, который должен использоваться для соединения дочерней статьи, определяемое *статье*и родительской статьей, указанной аргументом *join_article*, для определения строк, указывающих фильтр слияния. *join_filterclause* — **nvarchar(1000)**.  
  
`[ @join_unique_key = ] join_unique_key` Указывает, если соединение между дочерней статьей *статье*и родительской статьей *join_article*один ко многим, один к одному, многие к одному или многие ко многим. *join_unique_key* — **int**, значение по умолчанию 0. **0** указывает на соединение многие к одному "или" многие ко многим. **1** указывает на соединение один к одному "или" один ко многим. Это значение равно **1** Если соединяемые столбцы формируют уникальный ключ в *join_article*, или если *join_filterclause* между внешним ключом в *статье* и первичный ключ в *join_article*.  
  
> [!CAUTION]  
>  Этот параметр устанавливается только **1** при наличии ограничения на соединяющийся столбец в базовой таблице для родительской статьи, гарантирующее уникальность. Если *join_unique_key* присваивается **1** неправильно, конвергенции данных может не произойти.  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` Подтверждает, что действие, выполняемое данной хранимой процедурой, может сделать недействительным существующий моментальный снимок. *подписки потребуют* — **бит**, значение по умолчанию **0**.  
  
 **0** указывает, что изменения статьи слияния не приведут к недействительности моментального снимка. Если хранимая процедура определяет, что изменение требует создания нового моментального снимка, то возникает ошибка, и изменение не выполняется.  
  
 **1** указывает, что изменения статьи слияния может привести к недействительности моментального снимка и если существующие подписки потребуют нового моментального снимка, дается разрешение существующий моментальный снимок помечается как устаревший и новый моментальный снимок создан.  
  
`[ @force_reinit_subscription = ] force_reinit_subscription` Подтверждает, что действие, выполняемое данной хранимой процедурой, может сделать необходимой повторную инициализацию текущих подписок. *Этот* — **бит**, значение по умолчанию 0.  
  
 **0** указывает, что изменения статьи слияния не приведут к повторной инициализации подписки. Если хранимая процедура определит, что изменение потребует повторной инициализации подписки, то выдается сообщение об ошибке и изменения не производятся.  
  
 **1** указывает, что изменения в статье слияния приведут к повторной инициализации текущих подписок и дает разрешение произвести повторную инициализацию подписки.  
  
`[ @filter_type = ] filter_type` Указывает тип добавляемого фильтра. *filter_type* — **tinyint**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Только фильтр соединения. Необходим для поддержки подписчиков [!INCLUDE[ssEW](../../includes/ssew-md.md)].|  
|**2**|Только связь логических записей.|  
|**3**|Как фильтр соединения, так и связь логических записей.|  
  
 Дополнительные сведения см. в статье [Группирование изменений в связанных строках с помощью логических записей](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_addmergefilter** используется в репликации слиянием.  
  
 **sp_addmergefilter** может использоваться только со статьями таблиц. Статьи представлений и индексированных представлений не поддерживаются.  
  
 Эта процедура также может быть использована для формирования логической взаимосвязи между двумя статьями, между которыми может существовать или отсутствовать фильтр соединения. *filter_type* используется для указания того, если добавляемый фильтр слияния является фильтром соединения, логическому отношению или оба.  
  
 Для использования логических записей публикация и статьи должны удовлетворять определенным требованиям. Дополнительные сведения см. в статье [Группирование изменений в связанных строках с помощью логических записей](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
 Как правило, этот параметр используется для статьи с внешним ключом, указывающим на опубликованную таблицу первичного ключа, а таблица первичного ключа имеет фильтр, определенный в статье. Подмножество строк первичного ключа используется для определения строк внешнего ключа, реплицируемых в подписчика.  
  
 Между двумя опубликованными статьями можно вставить фильтр соединения, если исходные таблицы обеих статей имеют общее имя объекта таблицы. В этом случае, даже если обе таблицы принадлежат различным схемам и имеют уникальные имена статей, создание фильтра соединения завершится неудачей.  
  
 Если как параметризованный фильтр строк, так и фильтр соединения применяются к статье таблицы, то репликация определяет, принадлежит ли строка к секции подписчика. Она достигается путем расчета функции фильтрации или фильтра соединения (с помощью [OR](../../t-sql/language-elements/or-transact-sql.md) оператор), а не поиском пересечения двух условий (с помощью [AND](../../t-sql/language-elements/and-transact-sql.md) оператор).  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_addmergefilter](../../relational-databases/replication/codesnippet/tsql/sp-addmergefilter-transa_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_addmergefilter**.  
  
## <a name="see-also"></a>См. также  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [Определение и изменение фильтра соединения между статьями публикации слиянием](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [Join Filters](../../relational-databases/replication/merge/join-filters.md)   
 [sp_changemergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_dropmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [sp_helpmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
