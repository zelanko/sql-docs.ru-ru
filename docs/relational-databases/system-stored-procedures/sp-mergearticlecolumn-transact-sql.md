---
description: sp_mergearticlecolumn (Transact-SQL)
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d1036539564811e25be7764a3afb1106e05b1f37
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473985"
---
# <a name="sp_mergearticlecolumn-transact-sql"></a>sp_mergearticlecolumn (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
`[ @publication = ] 'publication'` Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @article = ] 'article'` Имя статьи в публикации. Аргумент *article* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @column = ] 'column'` Определяет столбцы, по которым создается вертикальная секция. *столбец* имеет тип **sysname**и значение по умолчанию NULL. Если значение равно NULL и `@operation = N'add'`, все столбцы исходной таблицы по умолчанию добавятся к статье. *столбец* не может иметь значение null, если для *операции* задано значение **Drop**. Чтобы исключить столбцы из статьи, выполните **sp_mergearticlecolumn** и укажите *Column* и `@operation = N'drop'` для каждого столбца, который необходимо удалить из указанной *статьи*.  
  
`[ @operation = ] 'operation'` Состояние репликации. *Операция* имеет тип **nvarchar (4)** и значение по умолчанию Add. **Добавить** помечает столбец для репликации. **Drop** очищает столбец.  
  
`[ @schema_replication = ] 'schema_replication'` Указывает, что изменение схемы будет распространяться при выполнении агент слияния. *schema_replication* имеет тип **nvarchar (5)** и значение по умолчанию false.  
  
> [!NOTE]  
>  Для *schema_replication*поддерживается только **значение false** .  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` Включает или отключает возможность недействительности моментального снимка. *force_invalidate_snapshot* является **битом**и имеет значение по умолчанию **0**.  
  
 **0** указывает, что изменения в статье слияния не приведут к недействительности моментального снимка.  
  
 **1** указывает, что изменения в статье слияния могут привести к недействительности моментального снимка, и, если это так, значение **1** дает разрешение на создание нового моментального снимка.  
  
`[ @force_reinit_subscription = ]force_reinit_subscription_` Включает или отключает возможность повторной инициализации подписки. *force_reinit_subscription* является битом со значением по умолчанию **0**.  
  
 **0** указывает, что изменения в статье публикации слиянием не приведут к повторной инициализации подписки.  
  
 **1** указывает, что изменения в статье слияния могут привести к повторной инициализации подписки, и, если это так, значение **1** дает разрешение на повторную инициализацию подписки.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 **sp_mergearticlecolumn** используется в репликации слиянием.  
  
 Если осуществляется автоматическое управление диапазоном идентификаторов, столбец идентификаторов не может быть сброшен из статьи. Дополнительные сведения см. в статье [Репликация столбцов идентификаторов](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
 Если после создания исходного моментального снимка приложение задает новую вертикальную секцию, необходимо сформировать новый моментальный снимок и применить его к каждой подписке. Моментальные снимки применяются к подпискам при выполнении следующего запланированного моментального снимка и агента распространителя или слияния.  
  
 Если для обнаружения конфликтов применяется трассировка на уровне строк (по умолчанию), базовая таблица может содержать не более 1 024 столбцов, однако столбцы из статьи должны быть отфильтрованы, чтобы было опубликовано не более 246 столбцов. Если применяется трассировка на уровне столбцов, базовая таблица может содержать не более 246 столбцов.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_AddMergeArticle](../../relational-databases/replication/codesnippet/tsql/sp-mergearticlecolumn-tr_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_mergearticlecolumn**.  
  
## <a name="see-also"></a>См. также:  
 [Определение и изменение фильтра соединения между статьями публикации слиянием](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Фильтрация опубликованных данных](../../relational-databases/replication/publish/filter-published-data.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
