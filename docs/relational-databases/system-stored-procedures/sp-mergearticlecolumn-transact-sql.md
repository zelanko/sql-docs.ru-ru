---
title: sp_mergearticlecolumn (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_mergearticlecolumn
- sp_mergearticlecolumn_TSQL
helpviewer_keywords:
- sp_mergearticlecolumn
ms.assetid: b4f2b888-e094-4759-a472-d893638995eb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d28c8da014a3922a9dbd1cba533b4cbf1d7a9215
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2018
ms.locfileid: "53590078"
---
# <a name="spmergearticlecolumn-transact-sql"></a>sp_mergearticlecolumn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выполняет вертикальное секционирование публикации слиянием. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_mergearticlecolumn [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @column = ] 'column'  
    [ , [ @operation = ] 'operation'   
    [ , [ @schema_replication = ] 'schema_replication' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]   
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication =**] **"**_публикации_**"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@article =**] **"**_статье_**"**  
 Имя статьи в публикации. *статья* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@column =**] **"**_столбец_**"**  
 Определяет столбцы, по которым создается вертикальная секция. *столбец* — **sysname**, значение по умолчанию NULL. Если значение равно NULL и `@operation = N'add'`, все столбцы исходной таблицы по умолчанию добавятся к статье. *столбец* не может иметь значение NULL, если *операции* присваивается **drop**. Чтобы исключить столбцы из статьи, выполните **sp_mergearticlecolumn** и укажите *столбец* и `@operation = N'drop'` для каждого столбца, удаляемый из указанного *статье*.  
  
 [  **@operation =**] **"**_операции_**"**  
 Состояние репликации. *Операция* — **nvarchar(4)**, значение по умолчанию ADD. **Добавление** столбец для репликации. **DROP** очищает столбец.  
  
 [  **@schema_replication=**] **"**_schema_replication_**"**  
 Этот аргумент определяет, будут ли распространены изменения схемы при запуске агента слияния. *schema_replication* — **nvarchar(5)**, значение по умолчанию FALSE.  
  
> [!NOTE]  
>  Только **FALSE** поддерживается для *schema_replication*.  
  
 [  **@force_invalidate_snapshot =** ] *подписки потребуют*  
 Определяет возможность недействительности моментального снимка. *подписки потребуют* — **бит**, значение по умолчанию **0**.  
  
 **0** указывает, что изменения статьи слияния не приведут к недействительности моментального снимка.  
  
 **1** изменения статьи слияния могут привести к недействительности моментального снимка; Если это происходит, значение **1** дает разрешение нового моментального снимка.  
  
 [  **@force_reinit_subscription =]**_этот_  
 Включает или отключает возможность повторной инициализации подписки. *Этот* имеет тип bit и значение по умолчанию **0**.  
  
 **0** указывает, что изменения статьи слияния не приведут к повторной инициализации подписки.  
  
 **1** изменения статьи слияния могут привести к повторной инициализации подписки; Если это происходит, значение **1** дает разрешение произвести повторную инициализацию подписки.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_mergearticlecolumn** используется в репликации слиянием.  
  
 Если осуществляется автоматическое управление диапазоном идентификаторов, столбец идентификаторов не может быть сброшен из статьи. Дополнительные сведения см. в статье [Репликация столбцов идентификаторов](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
 Если после создания исходного моментального снимка приложение задает новую вертикальную секцию, необходимо сформировать новый моментальный снимок и применить его к каждой подписке. Моментальные снимки применяются к подпискам при выполнении следующего запланированного моментального снимка и агента распространителя или слияния.  
  
 Если для обнаружения конфликтов применяется трассировка на уровне строк (по умолчанию), базовая таблица может содержать не более 1 024 столбцов, однако столбцы из статьи должны быть отфильтрованы, чтобы было опубликовано не более 246 столбцов. Если применяется трассировка на уровне столбцов, базовая таблица может содержать не более 246 столбцов.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_AddMergeArticle](../../relational-databases/replication/codesnippet/tsql/sp-mergearticlecolumn-tr_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_mergearticlecolumn**.  
  
## <a name="see-also"></a>См. также  
 [Определение и изменение фильтра соединения между статьями публикации слиянием](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Фильтрация опубликованных данных](../../relational-databases/replication/publish/filter-published-data.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
