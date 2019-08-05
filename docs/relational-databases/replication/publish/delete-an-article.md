---
title: Удаление статьи | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- articles [SQL Server replication], dropping
- sp_droparticle
- sp_dropmergearticle
- deleting articles
- removing articles
- dropping articles
ms.assetid: 185b58fc-38c0-4abe-822e-6ec20066c863
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 7d41bc68aadd9dc2c2ee471a9b14a5dea2ad53d6
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68764220"
---
# <a name="delete-an-article"></a>Удаление статьи
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  В данном разделе описывается удаление статьи в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью [!INCLUDE[tsql](../../../includes/tsql-md.md)] или объектов RMO. Сведения об условиях, при которых статьи могут быть удалены, и о том, требуется ли при удалении статьи создание нового моментального снимка или повторная инициализация подписок, см. в [этой статье](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
 **В этом разделе**  
  
-   **Для удаления статьи используется:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Статьи можно удалять программно, с помощью хранимых процедур репликации. Хранимые процедуры, используемые для этого, зависят от типа публикации, к которой принадлежит статья.  
  
#### <a name="to-delete-an-article-from-a-snapshot-or-transactional-publication"></a>Удаление статьи из публикации моментальных снимков или публикации транзакций  
  
1.  Чтобы удалить статью, указанную в **@article** , из публикации, указанной в **@publication** , выполните процедуру [sp_droparticle (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md). Укажите значение **1** в параметре **@force_invalidate_snapshot** .  
  
2.  (Необязательно) Чтобы полностью удалить опубликованный объект из базы данных, выполните команду `DROP <objectname>` на издателе для базы данных публикации.  

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

#### <a name="to-delete-an-article-from-a-merge-publication"></a>Удаление статьи из публикации слиянием  
  
1.  Чтобы удалить статью, указанную в **@article** , из публикации, указанной в **@publication** , выполните процедуру [sp_dropmergearticle (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md). При необходимости укажите значение **1** в параметре **@force_invalidate_snapshot** и значение **1** в параметре **@force_reinit_subscription** .  
  
2.  (Необязательно) Чтобы полностью удалить опубликованный объект из базы данных, выполните команду `DROP <objectname>` на издателе для базы данных публикации.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере удаляется статья из публикации транзакций. Поскольку это изменение приведет к недопустимости существующего моментального снимка, в параметре **1** указывается значение **@force_invalidate_snapshot** .  
  
```  
DECLARE @publication AS sysname;  
DECLARE @article AS sysname;  
SET @publication = N'AdvWorksProductTran';   
SET @article = N'Product';   
  
-- Drop the transactional article.  
USE [AdventureWorks]  
EXEC sp_droparticle   
  @publication = @publication,   
  @article = @article,  
  @force_invalidate_snapshot = 1;  
GO  
```  
  
 В следующем примере две статьи удаляются из публикации слиянием. Поскольку эти изменения приведут к недействительности существующего моментального снимка, в параметре **1** указывается значение **@force_invalidate_snapshot** .  
  
```  
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
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Удаление статьи можно произвести программным путем с помощью объектов RMO. Какие именно классы RMO будут для этого применяться, зависит от типа публикации, которой принадлежит подписка.  
  
#### <a name="to-delete-an-article-that-belongs-to-a-snapshot-or-transactional-publication"></a>Удаление статьи, принадлежащей публикации моментальных снимков или транзакций  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransArticle> .  
  
3.  Установите свойства <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>и <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> .  
  
4.  Установите полученное на шаге 1 соединение в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
5.  Проверьте свойство <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> , чтобы убедиться, что статья существует. Если это свойство имеет значение **false**, значит, на шаге 3 были неправильно заданы свойства статьи либо статья не существует.  
  
6.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> .  
  
7.  Закройте все соединения.  
  
#### <a name="to-delete-an-article-that-belongs-to-a-merge-publication"></a>Удаление статьи, принадлежащей публикации слиянием  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergeArticle> .  
  
3.  Установите свойства <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>и <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> .  
  
4.  Установите полученное на шаге 1 соединение в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
5.  Проверьте свойство <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> , чтобы убедиться, что статья существует. Если это свойство имеет значение **false**, значит, на шаге 3 были неправильно заданы свойства статьи либо статья не существует.  
  
6.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> .  
  
7.  Закройте все соединения.  
  
## <a name="see-also"></a>См. также:  
 [Добавление и удаление статей в существующих публикациях](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)   
 [Replication System Stored Procedures Concepts](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  
