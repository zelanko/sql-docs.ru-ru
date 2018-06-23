---
title: Удаление статьи | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 41
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: fa5cfaec81c0e2b22e7b66a36907daf57e443bdb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191944"
---
# <a name="delete-an-article"></a>Удаление статьи
  В данном разделе описывается удаление статьи в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью [!INCLUDE[tsql](../../../includes/tsql-md.md)] или объектов RMO. Сведения об условиях, при которых статьи могут быть удалены, и о том, требуется ли при удалении статьи создание нового моментального снимка или повторная инициализация подписок, см. в [этой статье](add-articles-to-and-drop-articles-from-existing-publications.md).  
  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Статьи можно удалять программно, с помощью хранимых процедур репликации. Хранимые процедуры, используемые для этого, зависят от типа публикации, к которой принадлежит статья.  
  
#### <a name="to-delete-an-article-from-a-snapshot-or-transactional-publication"></a>Удаление статьи из публикации моментальных снимков или публикации транзакций  
  
1.  Чтобы удалить статью, указанную в **@article**, из публикации, указанной в **@publication**, выполните процедуру [sp_droparticle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-droparticle-transact-sql). Укажите значение **1** в параметре **@force_invalidate_snapshot**.  
  
2.  (Необязательно) Чтобы полностью удалить опубликованный объект из базы данных, выполните команду `DROP <objectname>` на издателе для базы данных публикации.  
  
#### <a name="to-delete-an-article-from-a-merge-publication"></a>Удаление статьи из публикации слиянием  
  
1.  Чтобы удалить статью, указанную в **@article**, из публикации, указанной в **@publication**, выполните процедуру [sp_dropmergearticle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql). При необходимости укажите значение **1** в параметре **@force_invalidate_snapshot** и значение **1** в параметре **@force_reinit_subscription**.  
  
2.  (Необязательно) Чтобы полностью удалить опубликованный объект из базы данных, выполните команду `DROP <objectname>` на издателе для базы данных публикации.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере удаляется статья из публикации транзакций. Поскольку это изменение приведет к недопустимости существующего моментального снимка, в параметре **1** указывается значение **@force_invalidate_snapshot** .  
  
 [!code-sql[HowTo#sp_droparticle](../../../snippets/tsql/SQL15/replication/howto/tsql/droptranpub.sql#sp_droparticle)]  
  
 В следующем примере две статьи удаляются из публикации слиянием. Поскольку эти изменения приведут к недействительности существующего моментального снимка, в параметре **1** указывается значение **@force_invalidate_snapshot** .  
  
 [!code-sql[HowTo#sp_dropmergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepub.sql#sp_dropmergearticle)]
 [!code-sql[HowTo#sp_dropmergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/dropmergearticles.sql#sp_dropmergearticle)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Удаление статьи можно произвести программным путем с помощью объектов RMO. Какие именно классы RMO будут для этого применяться, зависит от типа публикации, которой принадлежит подписка.  
  
#### <a name="to-delete-an-article-that-belongs-to-a-snapshot-or-transactional-publication"></a>Удаление статьи, принадлежащей публикации моментальных снимков или транзакций  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransArticle> .  
  
3.  Установите свойства <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>и <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> .  
  
4.  Установите полученное на шаге 1 соединение в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
5.  Проверьте свойство <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> , чтобы убедиться, что статья существует. Если значение этого свойства равно `false`, были неправильно заданы свойства статьи на шаге 3, либо статья не существует.  
  
6.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> .  
  
7.  Закройте все соединения.  
  
#### <a name="to-delete-an-article-that-belongs-to-a-merge-publication"></a>Удаление статьи, принадлежащей публикации слиянием  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergeArticle> .  
  
3.  Установите свойства <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>и <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> .  
  
4.  Установите полученное на шаге 1 соединение в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
5.  Проверьте свойство <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> , чтобы убедиться, что статья существует. Если значение этого свойства равно `false`, были неправильно заданы свойства статьи на шаге 3, либо статья не существует.  
  
6.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> .  
  
7.  Закройте все соединения.  
  
## <a name="see-also"></a>См. также  
 [Добавление и удаление статей в существующих публикациях](add-articles-to-and-drop-articles-from-existing-publications.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
