---
title: Удаление публикации| Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- removing publications
- publications [SQL Server replication], deleting
- articles [SQL Server replication], deleting
- deleting publications
ms.assetid: 408a1360-12ee-4896-ac94-482ae839593b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 08623cc2f9bf5d57141644a9f24c01d29d04cbe3
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52771656"
---
# <a name="delete-a-publication"></a>Удаление публикации
  В данном разделе описывается удаление публикации в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]или объектов RMO.  
  
 **В этом разделе**  
  
-   **Для удаления публикации используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Удалите публикации из папки **Локальные публикации** в среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-delete-a-publication"></a>Удаление публикации  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Щелкните правой кнопкой мыши публикацию, которую требуется удалить, и выберите **Удалить**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Публикации могут быть удалены программно, с помощью хранимых процедур репликации. Какие именно хранимые процедуры для этого применяются, зависит от типа удаляемой публикации.  
  
> [!NOTE]  
>  При удалении публикации опубликованные объекты базы данных публикации и связанные с ними объекты базы данных подписки не удаляются. При необходимости их необходимо удалить вручную, при помощи инструкции `DROP <object>` .  
  
#### <a name="to-delete-a-snapshot-or-transactional-publication"></a>Удаление публикации моментальных снимков или транзакций  
  
1.  Выполните одно из следующих действий.  
  
    -   Для удаления отдельной публикации в базе данных публикации на издателе выполните инструкцию [sp_droppublication](/sql/relational-databases/system-stored-procedures/sp-droppublication-transact-sql) .  
  
    -   Чтобы удалить все публикации и удалить все объекты репликации из опубликованной базы данных, выполните процедуру [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) на издателе. Укажите значение `tran` для **@type**. Если распространитель недоступен или база данных находится в подозрительном состоянии или в режиме «вне сети», укажите значение **1** в параметре **@force**. Укажите имя базы данных в параметре **@dbname** , если процедура [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) не выполнялась в базе данных публикации (необязательно).  
  
        > [!NOTE]  
        >  Если задать значение **1** в параметре **@force** , в базе данных могут остаться объекты публикации, связанные с репликацией.  
  
2.  Если база данных содержит только одну публикацию, то для того, чтобы отключить публикацию текущей базы данных с помощью репликации моментальных снимков или транзакций, выполните хранимую процедуру [sp_replicationdboption (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) (необязательно).  
  
3.  (Необязательно) Чтобы удалить все метаданные репликации, оставшиеся в базе данных подписки, на подписчике в базе данных публикации выполните хранимую процедуру [sp_subscription_cleanup](/sql/relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql) .  
  
#### <a name="to-delete-a-merge-publication"></a>Удаление публикации слиянием  
  
1.  Выполните одно из следующих действий.  
  
    -   Чтобы удалить отдельную публикацию, выполните инструкцию [sp_dropmergepublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql) в базе данных публикации на издателе.  
  
    -   Чтобы удалить все публикации и удалить все объекты репликации из опубликованной базы данных, выполните процедуру [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) на издателе. Укажите значение `merge` для **@type**. Если распространитель недоступен или база данных находится в подозрительном состоянии или в режиме «вне сети», укажите значение **1** в параметре **@force**. Укажите имя базы данных в параметре **@dbname** , если процедура [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) не выполнялась в базе данных публикации (необязательно).  
  
        > [!NOTE]  
        >  Если задать значение **1** в параметре **@force** , в базе данных могут остаться объекты публикации, связанные с репликацией.  
  
2.  Если база данных содержит только одну публикацию, то для того, чтобы отключить публикацию текущей базы данных с помощью репликации слияния, выполните хранимую процедуру [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) (необязательно).  
  
3.  Чтобы удалить все метаданные репликации, оставшиеся в базе данных подписки, на подписчике в базе данных публикации выполните хранимую процедуру [sp_mergesubscription_cleanup (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql) (необязательно).  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере показано удаление публикации транзакций и отключение функции публикации транзакций для базы данных. В этом примере предполагается, что все подписки были удалены ранее. Дополнительные сведения см. в разделе [Delete a Pull Subscription](../delete-a-pull-subscription.md) или [Delete a Push Subscription](../delete-a-push-subscription.md).  
  
 [!code-sql[HowTo#sp_droppublication](../../../snippets/tsql/SQL15/replication/howto/tsql/droptranpub.sql#sp_droppublication)]  
  
 В следующем примере показано удаление публикации слиянием и отключение функции публикации слиянием для базы данных. В этом примере предполагается, что все подписки были удалены ранее. Дополнительные сведения см. в разделе [Delete a Pull Subscription](../delete-a-pull-subscription.md) или [Delete a Push Subscription](../delete-a-push-subscription.md).  
  
 [!code-sql[HowTo#sp_dropmergepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepub.sql#sp_dropmergepublication)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Публикации можно удалять программно с помощью объектов RMO. Классы RMO, используемые, чтобы удалить публикацию, зависят от типа удаляемой публикации.  
  
#### <a name="to-remove-a-snapshot-or-transactional-publication"></a>Удаление публикации моментальных снимков или публикации транзакций  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransPublication> .  
  
3.  Задайте для публикации свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> , а также установите созданное на шаге 1 соединение <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> в качестве значения для свойства.  
  
4.  Чтобы убедиться в существовании публикации, проверьте свойство <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> . Если значение этого свойства равно `false`, то либо на шаге 3 были неверно определены свойства публикации, либо публикация не существует.  
  
5.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A>.  
  
6.  (Необязательно) Если в базе данных не существует других публикаций транзакций, базу данных можно отключить от публикации транзакций следующим образом.  
  
    1.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> . В качестве значения для свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> укажите экземпляр соединения <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданный на шаге 1.  
  
    2.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A>. Если этот метод возвращает значение `false`, убедитесь, что база данных существует.  
  
    3.  Задайте для свойства <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing%2A> значение `false`.  
  
    4.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>.  
  
7.  Закройте соединения.  
  
#### <a name="to-remove-a-merge-publication"></a>Удаление публикации слиянием  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePublication> .  
  
3.  Задайте для публикации свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> , а также установите созданное на шаге 1 соединение <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> в качестве значения для свойства.  
  
4.  Чтобы убедиться в существовании публикации, проверьте свойство <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> . Если значение этого свойства равно `false`, то либо на шаге 3 были неверно определены свойства публикации, либо публикация не существует.  
  
5.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A>.  
  
6.  (Необязательно) Если в базе данных не существует других публикаций слиянием, базу данных можно отключить от публикации слиянием следующим образом.  
  
    1.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> . Присвойте свойству <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> значение экземпляра <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1.  
  
    2.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A>. Если этот метод возвращает значение `false`, проверьте, существует ли база данных.  
  
    3.  Установите свойство <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> в значение `false`.  
  
    4.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>.  
  
7.  Закройте соединения.  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 В следующем примере удаляется публикация транзакций. Если в этой базе данных не существует других публикаций транзакций, публикация транзакций также отключается.  
  
 [!code-csharp[HowTo#rmo_DropTranPub](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_droptranpub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPub](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_droptranpub)]  
  
 В следующем примере удаляется публикация слиянием. Если в этой базе данных не существует других публикаций слиянием, публикация слиянием также отключается.  
  
 [!code-csharp[HowTo#rmo_DropMergePub](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePub](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropmergepub)]  
  
## <a name="see-also"></a>См. также  
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [Публикация данных и объектов базы данных](publish-data-and-database-objects.md)  
  
  
