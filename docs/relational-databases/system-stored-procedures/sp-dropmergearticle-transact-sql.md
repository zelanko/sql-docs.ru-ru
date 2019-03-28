---
title: sp_dropmergearticle (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergearticle
- sp_dropmergearticle_TSQL
helpviewer_keywords:
- sp_dropmergearticle
ms.assetid: 5ef1fbf7-c03d-4488-9ab2-64aae296fa4f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 13f48722b940c26cda8b29258f16f641f74d15e9
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58531896"
---
# <a name="spdropmergearticle-transact-sql"></a>sp_dropmergearticle (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет статью из публикации слиянием. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropmergearticle [ @publication= ] 'publication'  
        , [ @article= ] 'article'   
    [ , [ @ignore_distributor= ] ignore_distributor   
    [ , [ @reserved= ] reserved   
    [ , [ @force_invalidate_snapshot= ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @ignore_merge_metadata = ] ignore_merge_metadata ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` — Имя публикации, из которой следует удалить статью. *Публикация*— **sysname**, не имеет значения по умолчанию.  
  
`[ @article = ] 'article'` — Имя статьи, которую следует удалить из данной публикации. *статья*— **sysname**, не имеет значения по умолчанию. Если **все**, будут удалены все статьи в указанной публикации слиянием. Даже если *статье* — **все**, публикацию нужно будет удалить отдельно из статьи.  
  
`[ @ignore_distributor = ] ignore_distributor` Указывает, выполняется ли данная хранимая процедура без подключения к распространителю. *ignore_distributor* — **бит**, значение по умолчанию **0**.  
  
`[ @reserved = ] reserved` Зарезервировано для использования в будущем. *зарезервированные* — **nvarchar(20)**, значение по умолчанию NULL.  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` Включает или отключает возможность наличия недействительных моментальных снимков. *подписки потребуют* — **бит**, значение по умолчанию **0**.  
  
 **0** указывает, что изменения статьи слияния не приводят к недействительности моментального снимка.  
  
 **1** означает, что изменения статьи слияния могут сделать моментальный снимок недействительным, и если это так, значение **1** дает разрешение нового моментального снимка.  
  
`[ @force_reinit_subscription = ] force_reinit_subscription` Подтверждает, что удаление статьи требует повторной инициализации существующих подписок. *Этот* — **бит**, значение по умолчанию **0**.  
  
 **0** указывает, что удаление статьи не вызывает повторной инициализации подписки.  
  
 **1** означает, что удаление статьи вызывает повторную инициализацию текущих подписок и дает разрешение произвести повторную инициализацию подписки.  
  
`[ @ignore_merge_metadata = ] ignore_merge_metadata` Только для внутреннего использования.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_dropmergearticle** используется в репликации слиянием. Дополнительные сведения об удалении статей см. в разделе [Добавление и удаление статей в существующих публикациях](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
 Выполнение **sp_dropmergearticle** удаление статьи из публикации не удаляет объект из базы данных публикации или соответствующий объект из базы данных подписки. При необходимости эти объекты могут быть удалены вручную при помощи инструкции `DROP <object>`.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_dropmergearticle**.  
  
## <a name="example"></a>Пример  
  
```sql  
DECLARE @publication AS sysname;  
DECLARE @article1 AS sysname;  
DECLARE @article2 AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge';  
SET @article1 = N'SalesOrderDetail';   
SET @article2 = N'SalesOrderHeader';   
  
-- Remove articles from a merge publication.  
USE [AdventureWorks]  
EXEC sp_dropmergearticle   
  @publication = @publication,   
  @article = @article1,  
  @force_invalidate_snapshot = 1;  
EXEC sp_dropmergearticle   
  @publication = @publication,   
  @article = @article2,  
  @force_invalidate_snapshot = 1;  
GO  
```  
  
```sql  
DECLARE @publication AS sysname;  
DECLARE @table1 AS sysname;  
DECLARE @table2 AS sysname;  
DECLARE @table3 AS sysname;  
DECLARE @salesschema AS sysname;  
DECLARE @hrschema AS sysname;  
DECLARE @filterclause AS nvarchar(1000);  
SET @publication = N'AdvWorksSalesOrdersMerge';   
SET @table1 = N'Employee';   
SET @table2 = N'SalesOrderHeader';   
SET @table3 = N'SalesOrderDetail';   
SET @salesschema = N'Sales';  
SET @hrschema = N'HumanResources';  
SET @filterclause = N'Employee.LoginID = HOST_NAME()';  
  
-- Drop the merge join filter between SalesOrderHeader and SalesOrderDetail.  
EXEC sp_dropmergefilter   
  @publication = @publication,   
  @article = @table3,   
  @filtername = N'SalesOrderDetail_SalesOrderHeader',   
  @force_invalidate_snapshot = 1,   
  @force_reinit_subscription = 1;  
  
-- Drops the merge join filter between Employee and SalesOrderHeader.  
EXEC sp_dropmergefilter   
  @publication = @publication,   
  @article = @table2,   
  @filtername = N'SalesOrderHeader_Employee',   
  @force_invalidate_snapshot = 1,   
  @force_reinit_subscription = 1;  
  
-- Drops the article for the SalesOrderDetail table.  
EXEC sp_dropmergearticle   
  @publication = @publication,   
  @article = @table3,  
  @force_invalidate_snapshot = 1,   
  @force_reinit_subscription = 1;  
  
-- Drops the article for the SalesOrderHeader table.  
EXEC sp_dropmergearticle   
  @publication = @publication,   
  @article = @table2,   
  @force_invalidate_snapshot = 1,   
  @force_reinit_subscription = 1;  
  
-- Drops the article for the Employee table.  
EXEC sp_dropmergearticle   
  @publication = @publication,   
  @article = @table1,  
  @force_invalidate_snapshot = 1,   
  @force_reinit_subscription = 1;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Удаление статьи](../../relational-databases/replication/publish/delete-an-article.md)   
 [Добавление и удаление статей в существующих публикациях](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)   
 [sp_addmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_changemergearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [sp_helpmergearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
