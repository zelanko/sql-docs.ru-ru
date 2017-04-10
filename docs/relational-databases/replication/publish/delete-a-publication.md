---
title: "Удаление публикации | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "удаление публикаций"
  - "публикации [репликация SQL Server], удаление"
  - "статьи [репликация SQL Server], удаление"
  - "удаление публикаций"
ms.assetid: 408a1360-12ee-4896-ac94-482ae839593b
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Удаление публикации
  В данном разделе описывается удаление публикации в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] или объектов RMO.  
  
 **В этом разделе**  
  
-   **Для удаления публикации используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Удалите публикации из папки **Локальные публикации** в среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
#### Удаление публикации  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Щелкните правой кнопкой мыши публикацию, нужно удалить и нажмите кнопку **Удаление**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Публикации могут быть удалены программно, с помощью хранимых процедур репликации. Какие именно хранимые процедуры для этого применяются, зависит от типа удаляемой публикации.  
  
> [!NOTE]  
>  При удалении публикации опубликованные объекты базы данных публикации и связанные с ними объекты базы данных подписки не удаляются. При необходимости их необходимо удалить вручную, при помощи инструкции `DROP <object>` .  
  
#### Удаление публикации моментальных снимков или транзакций  
  
1.  Выполните одно из следующих действий.  
  
    -   Чтобы удалить отдельную публикацию, выполнить [sp_droppublication](../../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md) на издателе в базе данных публикации.  
  
    -   Чтобы удалить все публикации и удалить все объекты репликации из опубликованной базы данных, выполните [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) на издателе. Укажите значение **tran** в параметре **@type**. (Необязательно) Если распространитель недоступен или находится в состоянии базы данных, подозрительные или в автономном режиме, укажите значение **1** для **@force**. (Необязательно) Укажите имя базы данных для **@dbname** Если [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) не выполняется в базе данных публикации.  
  
        > [!NOTE]  
        >  При значении **1** для **@force** может оставить публикуемые объекты, связанные с репликацией в базе данных.  
  
2.  (Необязательно) Если эта база данных содержит только одну публикацию, выполнить [sp_replicationdboption & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) Чтобы отключить публикацию текущей базы данных с помощью моментальных снимков или репликации транзакций.  
  
3.  (Необязательно) На подписчике в базе данных подписки выполните хранимую процедуру [sp_subscription_cleanup](../../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md) Чтобы удалить все метаданные репликации, оставшиеся в базе данных подписки.  
  
#### Удаление публикации слиянием  
  
1.  Выполните одно из следующих действий.  
  
    -   Чтобы удалить отдельную публикацию, выполнить [sp_dropmergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md) на издателе в базе данных публикации.  
  
    -   Чтобы удалить все публикации и удалить все объекты репликации из опубликованной базы данных, выполните [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) на издателе. Укажите значение **merge** в параметре **@type**. (Необязательно) Если распространитель недоступен или находится в состоянии базы данных, подозрительные или в автономном режиме, укажите значение **1** для **@force**. (Необязательно) Укажите имя базы данных для **@dbname** Если [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) не выполняется в базе данных публикации.  
  
        > [!NOTE]  
        >  При значении **1** для **@force** может оставить публикуемые объекты, связанные с репликацией в базе данных.  
  
2.  (Необязательно) Если эта база данных содержит только одну публикацию, выполнить [sp_replicationdboption & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) Чтобы отключить публикацию текущей базы данных с помощью репликации слиянием.  
  
3.  (Необязательно) На подписчике в базе данных подписки выполните хранимую процедуру [sp_mergesubscription_cleanup & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql.md) Чтобы удалить все метаданные репликации, оставшиеся в базе данных подписки.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере показано удаление публикации транзакций и отключение функции публикации транзакций для базы данных. В этом примере предполагается, что все подписки были удалены ранее. Дополнительные сведения см. в разделе [Delete a Pull Subscription](../../../relational-databases/replication/delete-a-pull-subscription.md) или [Delete a Push Subscription](../../../relational-databases/replication/delete-a-push-subscription.md).  
  
 [!code-sql[HowTo#sp_droppublication](../../../relational-databases/replication/codesnippet/tsql/delete-a-publication_1.sql)]  
  
 В следующем примере показано удаление публикации слиянием и отключение функции публикации слиянием для базы данных. В этом примере предполагается, что все подписки были удалены ранее. Дополнительные сведения см. в разделе [Delete a Pull Subscription](../../../relational-databases/replication/delete-a-pull-subscription.md) или [Delete a Push Subscription](../../../relational-databases/replication/delete-a-push-subscription.md).  
  
 [!code-sql[HowTo#sp_dropmergepublication](../../../relational-databases/replication/codesnippet/tsql/delete-a-publication_2.sql)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Публикации можно удалять программно с помощью объектов RMO. Классы RMO, используемые, чтобы удалить публикацию, зависят от типа удаляемой публикации.  
  
#### Удаление публикации моментальных снимков или публикации транзакций  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.TransPublication> класса.  
  
3.  Задайте <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Свойства для публикации, а также набор <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства подключения, созданной на шаге 1.  
  
4.  Проверьте <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> свойство, чтобы убедиться в существовании данной публикации. Если значение этого свойства равно **false**, то либо на шаге 3 были неверно определены свойства публикации, либо публикация не существует.  
  
5.  Вызов <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> метод.  
  
6.  (Необязательно) Если в базе данных не существует других публикаций транзакций, базу данных можно отключить от публикации транзакций следующим образом.  
  
    1.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> класса. Задайте <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства экземпляра <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1.  
  
    2.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод. Если этот метод возвращает значение **false**, убедитесь, что база данных существует.  
  
    3.  Задайте <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing%2A> Свойства **false**.  
  
    4.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> метод.  
  
7.  Закройте соединения.  
  
#### Удаление публикации слиянием  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergePublication> класса.  
  
3.  Задайте <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Свойства для публикации, а также набор <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства подключения, созданной на шаге 1.  
  
4.  Проверьте <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> свойство, чтобы убедиться в существовании данной публикации. Если значение этого свойства равно **false**, то либо на шаге 3 были неверно определены свойства публикации, либо публикация не существует.  
  
5.  Вызов <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> метод.  
  
6.  (Необязательно) Если в базе данных не существует других публикаций слиянием, базу данных можно отключить от публикации слиянием следующим образом.  
  
    1.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> класса. Задайте <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства экземпляра <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1.  
  
    2.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод. Если этот метод возвращает значение **false**, проверьте, существует ли база данных.  
  
    3.  Задайте <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> Свойства **false**.  
  
    4.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> метод.  
  
7.  Закройте соединения.  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 В следующем примере удаляется публикация транзакций. Если в этой базе данных не существует других публикаций транзакций, публикация транзакций также отключается.  
  
 [!code-csharp[HowTo#rmo_DropTranPub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_droptranpub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_droptranpub)]  
  
 В следующем примере удаляется публикация слиянием. Если в этой базе данных не существует других публикаций слиянием, публикация слиянием также отключается.  
  
 [!code-csharp[HowTo#rmo_DropMergePub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_dropmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_dropmergepub)]  
  
## См. также:  
 [Основные понятия системных хранимых процедур репликации](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Публикация данных и объектов базы данных](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  