---
title: "Удаление статьи | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "статьи [репликация SQL Server], удаление"
  - "sp_droparticle"
  - "sp_dropmergearticle"
  - "удаление статей"
  - "удаление статей"
  - "удаление статей"
ms.assetid: 185b58fc-38c0-4abe-822e-6ec20066c863
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# Удаление статьи
  В данном разделе описывается удаление статьи в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью [!INCLUDE[tsql](../../../includes/tsql-md.md)] или объектов RMO. Сведения об условиях, при которых статьи могут быть удалены и ли удаление статьи требует создания нового моментального снимка или повторной инициализации подписок см. в разделе [Добавление и удаление статей в существующих публикациях](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
 **В этом разделе**  
  
-   **Для удаления статьи используется:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Статьи можно удалять программно, с помощью хранимых процедур репликации. Хранимые процедуры, используемые для этого, зависят от типа публикации, к которой принадлежит статья.  
  
#### Удаление статьи из публикации моментальных снимков или публикации транзакций  
  
1.  Выполнение [sp_droparticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md) Удаление статьи, определяемое **@article**, из публикации, указанной параметром **@publication**. Укажите значение **1** для **@force_invalidate_snapshot**.  
  
2.  (Необязательно) Чтобы полностью удалить опубликованный объект из базы данных, выполните команду `DROP <objectname>` на издателе для базы данных публикации.  
  
#### Удаление статьи из публикации слиянием  
  
1.  Выполнение [sp_dropmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md) Удаление статьи, определяемое **@article**, из публикации, указанной параметром **@publication**. При необходимости укажите значение **1** для **@force_invalidate_snapshot** и значение **1** для **@force_reinit_subscription**.  
  
2.  (Необязательно) Чтобы полностью удалить опубликованный объект из базы данных, выполните команду `DROP <objectname>` на издателе для базы данных публикации.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере удаляется статья из публикации транзакций. Поскольку это изменение делает недействительным существующий моментальный снимок значение **1** указан для **@force_invalidate_snapshot** параметр.  
  
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
  
 В следующем примере две статьи удаляются из публикации слиянием. Так как эти изменения сделать недействительным существующий моментальный снимок значение **1** указан для **@force_invalidate_snapshot** параметр.  
  
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
  
#### Удаление статьи, принадлежащей публикации моментальных снимков или транзакций  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.TransArticle> класса.  
  
3.  Задайте <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, и <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> Свойства.  
  
4.  Задайте соединение из шага 1 для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> свойство.  
  
5.  Проверьте <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> свойство, чтобы убедиться, что статья существует. Если это свойство имеет значение **false**, значит, на шаге 3 были неправильно заданы свойства статьи либо статья не существует.  
  
6.  Вызов <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> метод.  
  
7.  Закройте все соединения.  
  
#### Удаление статьи, принадлежащей публикации слиянием  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergeArticle> класса.  
  
3.  Задайте <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, и <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> Свойства.  
  
4.  Задайте соединение из шага 1 для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> свойство.  
  
5.  Проверьте <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> свойство, чтобы убедиться, что статья существует. Если это свойство имеет значение **false**, значит, на шаге 3 были неправильно заданы свойства статьи либо статья не существует.  
  
6.  Вызов <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> метод.  
  
7.  Закройте все соединения.  
  
## См. также:  
 [Добавление и удаление статей в существующих публикациях](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)   
 [Основные понятия системных хранимых процедур репликации](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  