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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0ac36d85a08763903cb42a5b48d0280a6366a1e9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85716574"
---
# <a name="sp_addmergefilter-transact-sql"></a>sp_addmergefilter (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

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
`[ @publication = ] 'publication'`Имя публикации, в которую добавляется фильтр слияния. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @article = ] 'article'`Имя статьи, в которую добавляется фильтр слияния. Аргумент *article* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @filtername = ] 'filtername'`Имя фильтра. *filtername* является обязательным параметром. *filtername*имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @join_articlename = ] 'join_articlename'`Родительская статья, к которой дочерняя статья, указанная в *статье*, должна быть соединена с помощью предложения JOIN, заданного *join_filterclause*, чтобы определить строки дочерней статьи, соответствующие критерию фильтра фильтра слияния. Аргумент *join_articlename* имеет тип **sysname**и не имеет значения по умолчанию. Статья должна быть в публикации, заданной в *публикации*.  
  
`[ @join_filterclause = ] join_filterclause`Предложение join, которое должно использоваться для объединения дочерней статьи, указанной в *статье*и родительской статье, указанной в *join_article*, для определения строк, соответствующих фильтру слияния. *join_filterclause* имеет тип **nvarchar (1000)**.  
  
`[ @join_unique_key = ] join_unique_key`Указывает, является ли соединение между дочерней *статьей и*родительской статьей *join_article*"один ко многим", "один к одному", "многие к одному" или "многие ко многим". *join_unique_key* имеет **тип int**и значение по умолчанию 0. значение **0** указывает на соединение типа «многие к одному» или «многие ко многим». **1** указывает на соединение типа «один к одному» или «один ко многим». Это значение равно **1** , если соединяемые столбцы формируют уникальный ключ в *join_article*или если *join_filterclause* между внешним ключом в *статье* и первичным ключом в *join_article*.  
  
> [!CAUTION]  
>  Присвойте этому параметру значение **1** , если имеется ограничение на соединяемый столбец в базовой таблице для родительской статьи, что гарантирует уникальность. Если *join_unique_key* имеет неверное значение **1** , может произойти неконвергенция данных.  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot`Подтверждает, что действие, выполняемое этой хранимой процедурой, может сделать существующий моментальный снимок недействительным. *force_invalidate_snapshot* является **битом**и имеет значение по умолчанию **0**.  
  
 **0** указывает, что изменения в статье слияния не приведут к недействительности моментального снимка. Если хранимая процедура определяет, что изменение требует создания нового моментального снимка, то возникает ошибка, и изменение не выполняется.  
  
 значение **1** указывает, что изменения в статье слияния могут привести к недействительности моментального снимка, и если существуют подписки, требующие нового моментального снимка, предоставляет разрешение на пометку существующего моментального снимка как устаревшего и создание нового моментального снимка.  
  
`[ @force_reinit_subscription = ] force_reinit_subscription`Подтверждает, что действие, выполняемое этой хранимой процедурой, может потребовать повторной инициализации существующих подписок. *force_reinit_subscription* является **битом**и имеет значение по умолчанию 0.  
  
 **0** указывает, что изменения в статье публикации слиянием не приведут к повторной инициализации подписки. Если хранимая процедура определит, что изменение потребует повторной инициализации подписки, то выдается сообщение об ошибке и изменения не производятся.  
  
 **1** указывает, что изменения в статье слияния приведут к повторной инициализации существующих подписок и предложит разрешение на повторную инициализацию подписки.  
  
`[ @filter_type = ] filter_type`Указывает тип добавляемого фильтра. *filter_type* имеет тип **tinyint**и может принимать одно из следующих значений.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**1**|Только фильтр соединения. Необходим для поддержки подписчиков [!INCLUDE[ssEW](../../includes/ssew-md.md)].|  
|**2**|Только связь логических записей.|  
|**3**|Как фильтр соединения, так и связь логических записей.|  
  
 Дополнительные сведения см. в статье [Группирование изменений в связанных строках с помощью логических записей](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_addmergefilter** используется в репликации слиянием.  
  
 **sp_addmergefilter** можно использовать только с статьями таблицы. Статьи представлений и индексированных представлений не поддерживаются.  
  
 Эта процедура также может быть использована для формирования логической взаимосвязи между двумя статьями, между которыми может существовать или отсутствовать фильтр соединения. *filter_type* используется для указания, является ли добавляемый фильтр слияния фильтром объединения, логической связью или обоими.  
  
 Для использования логических записей публикация и статьи должны удовлетворять определенным требованиям. Дополнительные сведения см. в статье [Группирование изменений в связанных строках с помощью логических записей](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
 Как правило, этот параметр используется для статьи с внешним ключом, указывающим на опубликованную таблицу первичного ключа, а таблица первичного ключа имеет фильтр, определенный в статье. Подмножество строк первичного ключа используется для определения строк внешнего ключа, реплицируемых в подписчика.  
  
 Между двумя опубликованными статьями можно вставить фильтр соединения, если исходные таблицы обеих статей имеют общее имя объекта таблицы. В этом случае, даже если обе таблицы принадлежат различным схемам и имеют уникальные имена статей, создание фильтра соединения завершится неудачей.  
  
 Если как параметризованный фильтр строк, так и фильтр соединения применяются к статье таблицы, то репликация определяет, принадлежит ли строка к секции подписчика. Это делается путем вычисления функции фильтрации или фильтра соединений (с помощью оператора [or](../../t-sql/language-elements/or-transact-sql.md) ) вместо вычисления пересечения двух условий (с помощью оператора [and](../../t-sql/language-elements/and-transact-sql.md) ).  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_addmergefilter](../../relational-databases/replication/codesnippet/tsql/sp-addmergefilter-transa_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_addmergefilter**.  
  
## <a name="see-also"></a>См. также  
 [Определение статьи](../../relational-databases/replication/publish/define-an-article.md)   
 [Определение и изменение фильтра соединений между статьями публикации слиянием](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [Фильтры соединений](../../relational-databases/replication/merge/join-filters.md)   
 [sp_changemergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_dropmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [sp_helpmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
