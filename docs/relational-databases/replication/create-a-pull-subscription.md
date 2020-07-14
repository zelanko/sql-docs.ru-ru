---
title: Создание подписки по запросу | Документация Майкрософт
description: Узнайте, как создать подписку по запросу в SQL Server с помощью SQL Server Management Studio, Transact-SQL или объектов Replication Management Objects.
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- pull subscriptions [SQL Server replication], creating
- merge replication subscribing [SQL Server replication], pull subscriptions
- subscriptions [SQL Server replication], pull
- snapshot replication [SQL Server], subscribing
- transactional replication, subscribing
ms.assetid: 41d1886d-59c9-41fc-9bd6-a59b40e0af6e
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 4f2cf1f98203b89e25fa3b6c5d165c40798163df
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773937"
---
# <a name="create-a-pull-subscription"></a>Создание подписки по запросу

<!--
2019-10-24 , GeneMi:
This article .md file exists in the so-called "2016+" section of repo 'sql-docs-pr'.
No article in 2016+ should ever have the moniker 'sql-server-2014' on its metadata line 'monikerRange:', I think.
Presently 'sql-server-2014' moniker is on this 'monikerRange'. This situation deserves further investigation.
-->

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  В данном разделе описывается процесс создания подписки по запросу в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или объектов RMO.  
  
 Настроить подписку по запросу для репликации P2P возможно с помощью скрипта, но не с помощью мастера.  
 
  ##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Создайте подписку по запросу на издателе или подписчике с помощью мастера создания подписки. Следуйте инструкциям на страницах мастера, чтобы выполнить следующие действия:  
  
-   Указать издателя и публикацию.  
  
-   Выбрать, где будут выполняться агенты репликации. Для подписки по запросу выберите **Выполнять каждый агент на своем подписчике (подписки по запросу)** на странице **Расположение агента распространителя** или на странице **Расположение агента слияния** в зависимости от типа публикации.  
  
-   Указать подписчиков и базы данных подписок.  
  
-   Указать имена входов и пароли, используемые агентами репликации для подключений:  
  
    -   Для подписок на публикации моментальных снимков и публикации транзакций укажите учетные данные на странице **Безопасность агента распространителя** .  
  
    -   Для подписок на публикации слиянием укажите учетные данные на странице **Безопасность агента слияния** .  
  
     Дополнительные сведения о разрешениях, необходимых каждому агенту, см. в разделе [Модель безопасности агента репликации](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
-   Указать расписание синхронизации и время, когда подписчик должен быть инициализирован.  
  
-   Укажите дополнительные параметры для публикаций слиянием: тип подписки, значения параметризированного фильтра и сведения для синхронизации по протоколу HTTPS, если для публикации используется веб-синхронизация.  
  
-   Укажите дополнительные параметры для публикаций транзакций, позволяющих использовать обновляемые подписки: должны ли подписчики фиксировать изменения на издателе немедленно или записывать их в очередь; учетные данные, используемые для подключения подписчика к издателю.  
  
-   При необходимости создайте скрипт для подписки.  
  
#### <a name="to-create-a-pull-subscription-from-the-publisher"></a>Создание подписки по запросу с издателя  
  
1.  Подключитесь к издателю в среде [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Щелкните правой кнопкой мыши публикацию, для которой хотите создать одну или более подписок, затем щелкните **Создать подписку**.  
  
4.  Выполните инструкции на страницах мастера создания подписки.  

#### <a name="to-create-a-pull-subscription-from-the-subscriber"></a>Создание подписки по запросу с подписчика  
  
1.  Подключитесь к подписчику в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** .  
  
3.  Щелкните правой кнопкой мыши папку **Локальные подписки** , затем щелкните **Создать подписку**.  
  
4.  На странице **Публикация** мастера создания подписки выберите **\<Find SQL Server Publisher>** или **\<Find Oracle Publisher>** из раскрывающегося списка **Издатель**.  
  
5.  Соединитесь с издателем в диалоговом окне **Соединение с сервером** .  
  
6.  Выберите публикацию на странице **Публикация** .  
  
7.  Выполните инструкции на страницах мастера создания подписки.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 Подписки по запросу можно создавать программно с помощью хранимых процедур репликации. Какие именно хранимые процедуры будут при этом применяться, зависит от типа публикации, к которой относится подписка.  
  
#### <a name="to-create-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>Создание подписки по запросу на публикацию моментальных снимков или транзакций  
  
1.  Проверьте на издателе, поддерживает ли публикация подписки по запросу. Для этого выполните процедуру [sp_helppublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md).  
  
    -   Если в результирующем наборе значение параметра **allow_pull** равно **1**, подписки по запросу поддерживаются.  
  
    -   Если значение столбца **allow_pull** равно **0**, необходимо выполнить процедуру [sp_changepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), указав значение **allow_pull** в параметре **\@property** и значение **true** в параметре **\@value**.  
  
2.  На подписчике выполните процедуру [sp_addpullsubscription (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md). Укажите значения параметров **\@publisher** и **\@publication**. Сведения об обновлении подписок см. в разделе [Создание обновляемых подписок для публикаций транзакций](publish/create-an-updatable-subscription-to-a-transactional-publication.md).   
  
3.  На подписчике выполните процедуру [sp_addpullsubscription_agent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md). Укажите следующее.  
  
    -   Значения параметров **\@publisher**, **\@publisher_db** и **\@publication**.  
  
    -   Учетные данные пользователя [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, от имени которого на подписчике будет запущен агент распространения, в качестве значений параметров **\@job_login** и **\@job_password**.  
  
        > [!NOTE]  
        >  Для соединений, производимых с использованием встроенной проверки подлинности Windows, в параметрах **\@job_login** и **\@job_password** всегда указываются учетные данные Windows. Агент распространителя всегда создает локальное соединение с подписчиком с использованием встроенной проверки подлинности Windows. По умолчанию агент установит соединение с распространителем с помощью встроенной проверки подлинности Windows.  
  
    -   Значение **0** для параметра **\@distributor_security_mode** и данные учетной записи SQL Server в параметрах **\@distributor_login** и **\@distributor_password**, если для соединения с распространителем нужно использовать проверку подлинности SQL Server (необязательно).  
  
    -   Расписание задания агента распространителя для этой подписки. Дополнительные сведения см. в статье [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
4.  Чтобы зарегистрировать подписку по запросу, выполните на издателе хранимую процедуру [sp_addsubscription (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Укажите значения параметров **\@publication**, **\@subscriber** и **\@destination_db**. Укажите **pull** в качестве значения параметра **\@subscription_type**.  
  
#### <a name="to-create-a-pull-subscription-to-a-merge-publication"></a>Создание подписки по запросу на публикацию слиянием  
  
1.  Проверьте на издателе, поддерживает ли публикация подписки по запросу. Для этого выполните процедуру [sp_helpmergepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md).  
  
    -   Если в результирующем наборе значение параметра **allow_pull** равно **1**, подписки по запросу поддерживаются.  
  
    -   Если значение столбца **allow_pull** равно **0**, необходимо выполнить процедуру [sp_changemergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), указав значение **allow_pull** в параметре **\@property** и значение **true** в параметре **\@value**.  
  
2.  На подписчике выполните процедуру [sp_addmergepullsubscription (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md). Укажите значения параметров **\@publisher**, **\@publisher_db**, **\@publication**, а также следующих:  
  
    -   **\@subscriber_type** — укажите значение **local** для клиентской подписки или **global** — для серверной.  
  
    -   **\@subscription_priority** — укажите приоритет подписки (от **0.00** до **99.99**). Это значение необходимо указывать только для серверной подписки.  
  
         Дополнительные сведения см. в разделе [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
3.  На подписчике выполните процедуру [sp_addmergepullsubscription_agent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md). Укажите значения следующих параметров.  
  
    -   **\@publisher**, **\@publisher_db** и **\@publication**.  
  
    -   Учетные данные пользователя Windows, от имени которого на подписчике будет запущен агент слияния, в качестве значений параметров **\@job_login** и **\@job_password**.  
  
        > [!NOTE]  
        >  Для соединений, производимых с использованием встроенной проверки подлинности Windows, в параметрах **\@job_login** и **\@job_password** всегда указываются учетные данные Windows. Агент слияния всегда создает локальное соединение с подписчиком с использованием встроенной проверки подлинности Windows. По умолчанию агент установит соединение с распространителем и издателем с помощью встроенной проверки подлинности Windows.  
  
    -   Значение **0** для параметра **\@distributor_security_mod**e и данные учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в параметрах **\@distributor_login** и **\@distributor_password**, если для соединения с распространителем нужно использовать проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (необязательно).  
  
    -   Значение **0** для параметра **\@publisher_security_mode** и данные учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в параметрах **\@publisher_login** и **\@publisher_password**, если для соединения с издателем нужно использовать проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (необязательно).  
  
    -   Расписание агента слияния для данной подписки. Дополнительные сведения см. в разделе [Создание обновляемых подписок для публикаций транзакций](publish/create-an-updatable-subscription-to-a-transactional-publication.md).  
  
4.  На издателе выполните процедуру [sp_addmergesubscription (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md). Укажите значения параметров **\@publication**, **\@subscriber**, **\@subscriber_db** и значение **pull** в параметре **\@subscription_type**. После этого подписка по запросу будет зарегистрирована.  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере создается подписка по запросу на публикацию транзакций. Первый пакет выполняется на подписчике, а второй — на издателе. Имя входа и пароль предоставляются во время выполнения переменными сценария sqlcmd.  
  
```  
-- This script uses sqlcmd scripting variables. They are in the form  
-- $(MyVariable). For information about how to use scripting variables    
-- on the command line and in SQL Server Management Studio, see the   
-- "Executing Replication Scripts" section in the topic  
-- "Programming Replication Using System Stored Procedures".  
  
-- Execute this batch at the Subscriber.  
DECLARE @publication AS sysname;  
DECLARE @publisher AS sysname;  
DECLARE @publicationDB AS sysname;  
SET @publication = N'AdvWorksProductTran';  
SET @publisher = $(PubServer);  
SET @publicationDB = N'AdventureWorks';  
  
-- At the subscription database, create a pull subscription   
-- to a transactional publication.  
USE [AdventureWorksReplica]  
EXEC sp_addpullsubscription   
  @publisher = @publisher,   
  @publication = @publication,   
  @publisher_db = @publicationDB;  
  
-- Add an agent job to synchronize the pull subscription.  
EXEC sp_addpullsubscription_agent   
  @publisher = @publisher,   
  @publisher_db = @publicationDB,   
  @publication = @publication,   
  @distributor = @publisher,   
  @job_login = $(Login),   
  @job_password = $(Password);  
GO  
```  
  
```  
-- This script uses sqlcmd scripting variables. They are in the form  
-- $(MyVariable). For information about how to use scripting variables    
-- on the command line and in SQL Server Management Studio, see the   
-- "Executing Replication Scripts" section in the topic  
-- "Programming Replication Using System Stored Procedures".  
  
-- Execute this batch at the Publisher.  
DECLARE @publication AS sysname;  
DECLARE @subscriber AS sysname;  
DECLARE @subscriptionDB AS sysname;  
SET @publication = N'AdvWorksProductTran';  
SET @subscriber = $(SubServer);  
SET @subscriptionDB = N'AdventureWorksReplica';  
  
-- At the Publisher, register the subscription, using the defaults.  
EXEC sp_addsubscription   
  @publication = @publication,   
  @subscriber = @subscriber,   
  @destination_db = @subscriptionDB,   
  @subscription_type = N'pull',  
  @status = N'subscribed';  
GO  
  
```  
  
 В следующем примере создается подписка по запросу на публикацию слиянием. Первый пакет выполняется на подписчике, а второй — на издателе. Значения имени входа и пароля задаются во время выполнения с помощью переменных скриптов **sqlcmd** .  
  
```  
-- This script uses sqlcmd scripting variables. They are in the form  
-- $(MyVariable). For information about how to use scripting variables    
-- on the command line and in SQL Server Management Studio, see the   
-- "Executing Replication Scripts" section in the topic  
-- "Programming Replication Using System Stored Procedures".  
  
-- Execute this batch at the Subscriber.  
DECLARE @publication AS sysname;  
DECLARE @publisher AS sysname;  
DECLARE @publicationDB AS sysname;  
DECLARE @hostname AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge';  
SET @publisher = $(PubServer);  
SET @publicationDB = N'AdventureWorks';  
SET @hostname = N'adventure-works\david8';  
  
-- At the subscription database, create a pull subscription   
-- to a merge publication.  
USE [AdventureWorksReplica]  
EXEC sp_addmergepullsubscription   
  @publisher = @publisher,   
  @publication = @publication,   
  @publisher_db = @publicationDB;  
  
-- Add an agent job to synchronize the pull subscription.   
EXEC sp_addmergepullsubscription_agent   
  @publisher = @publisher,   
  @publisher_db = @publicationDB,   
  @publication = @publication,   
  @distributor = @publisher,   
  @job_login = $(Login),   
  @job_password = $(Password),  
  @hostname = @hostname;  
GO  
```  
  
```  
-- Execute this batch at the Publisher.  
DECLARE @myMergePub  AS sysname;  
DECLARE @mySub       AS sysname;  
DECLARE @mySubDB     AS sysname;  
  
SET @myMergePub = N'AdvWorksSalesOrdersMerge';  
SET @mySub = N'MYSUBSERVER';  
SET @mySubDB = N'AdventureWorksReplica';  
  
-- At the Publisher, register the subscription, using the defaults.  
USE [AdventureWorks]  
EXEC sp_addmergesubscription @publication = @myMergePub,   
@subscriber = @mySub, @subscriber_db = @mySubDB,   
@subscription_type = N'pull';  
GO  
```  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> При помощи объектов RMO  
 Конкретные классы RMO, используемые для этого, зависят от типа репликации, к которой относится подписка.  
  
#### <a name="to-create-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>Создание подписки по запросу на публикацию моментальных снимков или транзакций  
  
1.  Создайте соединения с подписчиком и издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  На основе соединения с издателем, созданного на шаге 1, создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransPublication> . Задайте свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> и <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если метод возвращает значение **false**, то либо неверно определены свойства, указанные на шаге 2, либо публикация не существует на сервере.  
  
4.  Выполните операцию «поразрядное логическое И» ( **&** в Visual C# и **And** в Visual Basic) над свойством <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> и флагом <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull>. Если результат равен <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, присвойте свойству <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> результат операции «поразрядное логическое ИЛИ» ( **|** в Visual C# и **Or** в Visual Basic) над свойством <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> и <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull>. Затем вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> , чтобы включить подписку по запросу.  
  
5.  Если база данных подписки не существует, создайте ее с помощью класса <xref:Microsoft.SqlServer.Management.Smo.Database> . Дополнительные сведения см. в статье [Creating, Altering, and Removing Databases](../../relational-databases/server-management-objects-smo/tasks/creating-altering-and-removing-databases.md) (Создание, изменение и удаление баз данных).  
  
6.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransPullSubscription>.  
  
7.  Укажите следующие свойства подписки:  
  
    -   соединение ( <xref:Microsoft.SqlServer.Management.Common.ServerConnection> ) с подписчиком, созданное на шаге 1, в свойстве <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>;  
  
    -   имя базы данных подписки в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>;  
  
    -   Имя издателя в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.  
  
    -   имя базы данных публикации в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>;  
  
    -   имя публикации в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>;  
  
    -   Значения параметров <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> и <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> или <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> объекта [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Эта учетная запись будет использоваться для создания локальных соединений с подписчиком, а также для удаленных соединений с использованием проверки подлинности Windows.  
  
        > [!NOTE]  
        >  Указывать свойство <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> необязательно, если подписка создается членом предопределенной роли сервера **sysadmin** , однако рекомендуется это сделать. В этом случае агент будет выполнять олицетворение учетную запись агента SQL Server. Дополнительные сведения см. в статье [Модель безопасности агента репликации](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   (Необязательно.) Значение **true** в качестве значения параметра <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> , чтобы создать задание агента, используемое для синхронизации подписки. Если указано значение **false** (значение по умолчанию), подписку можно синхронизировать только программно, и поэтому придется указывать дополнительные свойства <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> при доступе к этому объекту из <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizationAgent%2A> . Дополнительные сведения см. в статье [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
        > [!NOTE]  
        >  Агент SQL Server доступен не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md). При указании значения **true** для подписчиков выпуска Express задание агента не создается. Однако метаданные, существенные для работы подписки, сохраняются на подписчике.  
  
    -   (необязательно) при соединении с распространителем с проверкой подлинности SQL Server укажите значения свойств <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> и <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> или <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> объекта <xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> ;  
  
8.  Вызовите метод <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> .  
  
9. Используя экземпляр класса <xref:Microsoft.SqlServer.Replication.TransPublication> , созданный на шаге 2, вызовите метод <xref:Microsoft.SqlServer.Replication.TransPublication.MakePullSubscriptionWellKnown%2A> , чтобы зарегистрировать подписку по запросу для данного издателя. Если данная регистрация уже существует, возникнет исключение.  
  
#### <a name="to-create-a-pull-subscription-to-a-merge-publication"></a>Создание подписки по запросу на публикацию слиянием  
  
1.  Создайте соединения с подписчиком и издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  На основе соединения с издателем, созданного на шаге 1, создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePublication> . Задайте свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>и <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если метод возвращает значение **false**, то либо неверно определены свойства, указанные на шаге 2, либо публикация не существует на сервере.  
  
4.  Выполните операцию «поразрядное логическое И» ( **&** в Visual C# и **And** в Visual Basic) над свойством <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> и флагом <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull>. Если результат равен <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, присвойте свойству <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> результат операции «поразрядное логическое ИЛИ» ( **|** в Visual C# и **Or** в Visual Basic) над свойством <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> и <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull>. Затем вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> , чтобы включить подписку по запросу.  
  
5.  Если база данных подписки не существует, создайте ее с помощью класса <xref:Microsoft.SqlServer.Management.Smo.Database> . Дополнительные сведения см. в статье [Creating, Altering, and Removing Databases](../../relational-databases/server-management-objects-smo/tasks/creating-altering-and-removing-databases.md) (Создание, изменение и удаление баз данных).  
  
6.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePullSubscription>.  
  
7.  Укажите следующие свойства подписки:  
  
    -   соединение ( <xref:Microsoft.SqlServer.Management.Common.ServerConnection> ) с подписчиком, созданное на шаге 1, в свойстве <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>;  
  
    -   имя базы данных подписки в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>;  
  
    -   Имя издателя в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.  
  
    -   имя базы данных публикации в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>;  
  
    -   имя публикации в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>;  
  
    -   Значения параметров <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> и <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> или <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> объекта [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Эта учетная запись будет использоваться для создания локальных соединений с подписчиком, а также для удаленных соединений с использованием проверки подлинности Windows.  
  
        > [!NOTE]  
        >  Указывать свойство <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> необязательно, если подписка создается членом предопределенной роли сервера **sysadmin** , однако рекомендуется это сделать. В этом случае агент будет выполнять олицетворение учетную запись агента SQL Server. Дополнительные сведения см. в статье [Модель безопасности агента репликации](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   (Необязательно.) Значение **true** в качестве значения параметра <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> , чтобы создать задание агента, используемое для синхронизации подписки. Если указано значение **false** (значение по умолчанию), подписку можно синхронизировать только программно, и поэтому придется указывать дополнительные свойства <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> при доступе к этому объекту из <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizationAgent%2A> . Дополнительные сведения см. в статье [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
    -   (необязательно) при соединении с распространителем с проверкой подлинности SQL Server укажите значения свойств <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> и <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> или <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> объекта <xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> ;  
  
    -   (необязательно) при соединении с издателем с проверкой подлинности SQL Server укажите значения свойств <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> и <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> или <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> объекта <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherSecurity%2A> .  
  
8.  Вызовите метод <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> .  
  
9. Используя экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePublication> , созданный на шаге 2, вызовите метод <xref:Microsoft.SqlServer.Replication.MergePublication.MakePullSubscriptionWellKnown%2A> , чтобы зарегистрировать подписку по запросу для данного издателя. Если данная регистрация уже существует, возникнет исключение.  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a> Пример (объекты RMO)  
 В следующем примере создается подписка по запросу на публикацию транзакций. Данные учетной записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows для задания агента распространителя предоставляются во время выполнения.  
  
```csharp  
// Define the Publisher, publication, and databases.  
string publicationName = "AdvWorksProductTran";  
string publisherName = publisherInstance;  
string subscriberName = subscriberInstance;  
string subscriptionDbName = "AdventureWorksReplica";  
string publicationDbName = "AdventureWorks";  
  
//Create connections to the Publisher and Subscriber.  
ServerConnection subscriberConn = new ServerConnection(subscriberName);  
ServerConnection publisherConn = new ServerConnection(publisherName);  
  
// Create the objects that we need.  
TransPublication publication;  
TransPullSubscription subscription;  
  
try  
{  
    // Connect to the Publisher and Subscriber.  
    subscriberConn.Connect();  
    publisherConn.Connect();  
  
    // Ensure that the publication exists and that   
    // it supports pull subscriptions.  
    publication = new TransPublication();  
    publication.Name = publicationName;  
    publication.DatabaseName = publicationDbName;  
    publication.ConnectionContext = publisherConn;  
  
    if (publication.IsExistingObject)  
    {  
        if ((publication.Attributes & PublicationAttributes.AllowPull) == 0)  
        {  
            publication.Attributes |= PublicationAttributes.AllowPull;  
        }  
  
        // Define the pull subscription.  
        subscription = new TransPullSubscription();  
        subscription.ConnectionContext = subscriberConn;  
        subscription.PublisherName = publisherName;  
        subscription.PublicationName = publicationName;  
        subscription.PublicationDBName = publicationDbName;  
        subscription.DatabaseName = subscriptionDbName;  
  
        // Specify the Windows login credentials for the Distribution Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin;  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword;  
  
        // Make sure that the agent job for the subscription is created.  
        subscription.CreateSyncAgentByDefault = true;  
  
        // By default, subscriptions to transactional publications are synchronized   
        // continuously, but in this case we only want to synchronize on demand.  
        subscription.AgentSchedule.FrequencyType = ScheduleFrequencyType.OnDemand;  
  
        // Create the pull subscription at the Subscriber.  
        subscription.Create();  
  
        Boolean registered = false;  
  
        // Verify that the subscription is not already registered.  
        foreach (TransSubscription existing  
            in publication.EnumSubscriptions())  
        {  
            if (existing.SubscriberName == subscriberName  
                && existing.SubscriptionDBName == subscriptionDbName)  
            {  
                registered = true;  
            }  
        }  
        if (!registered)  
        {  
            // Register the subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown(  
                subscriberName, subscriptionDbName,  
                SubscriptionSyncType.Automatic,  
                TransSubscriberType.ReadOnly);  
        }  
    }  
    else  
    {  
        // Do something here if the publication does not exist.  
        throw new ApplicationException(String.Format(  
            "The publication '{0}' does not exist on {1}.",  
            publicationName, publisherName));  
    }  
}  
catch (Exception ex)  
{  
    // Implement the appropriate error handling here.  
    throw new ApplicationException(String.Format(  
        "The subscription to {0} could not be created.", publicationName), ex);  
}  
finally  
{  
    subscriberConn.Disconnect();  
    publisherConn.Disconnect();  
}  
  
```  
  
```vb  
' Define the Publisher, publication, and databases.  
Dim publicationName As String = "AdvWorksProductTran"  
Dim publisherName As String = publisherInstance  
Dim subscriberName As String = subscriberInstance  
Dim subscriptionDbName As String = "AdventureWorksReplica"  
Dim publicationDbName As String = "AdventureWorks"  
  
'Create connections to the Publisher and Subscriber.  
Dim subscriberConn As ServerConnection = New ServerConnection(subscriberName)  
Dim publisherConn As ServerConnection = New ServerConnection(publisherName)  
  
' Create the objects that we need.  
Dim publication As TransPublication  
Dim subscription As TransPullSubscription  
  
Try  
    ' Connect to the Publisher and Subscriber.  
    subscriberConn.Connect()  
    publisherConn.Connect()  
  
    ' Ensure that the publication exists and that   
    ' it supports pull subscriptions.  
    publication = New TransPublication()  
    publication.Name = publicationName  
    publication.DatabaseName = publicationDbName  
    publication.ConnectionContext = publisherConn  
  
    If publication.IsExistingObject Then  
        If (publication.Attributes And PublicationAttributes.AllowPull) = 0 Then  
            publication.Attributes = publication.Attributes _  
            Or PublicationAttributes.AllowPull  
        End If  
  
        ' Define the pull subscription.  
        subscription = New TransPullSubscription()  
        subscription.ConnectionContext = subscriberConn  
        subscription.PublisherName = publisherName  
        subscription.PublicationName = publicationName  
        subscription.PublicationDBName = publicationDbName  
        subscription.DatabaseName = subscriptionDbName  
        subscription.Description = "Pull subscription to " + publicationDbName _  
        + " on " + subscriberName + "."  
  
        ' Specify the Windows login credentials for the Distribution Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword  
  
        ' Make sure that the agent job for the subscription is created.  
        subscription.CreateSyncAgentByDefault = True  
  
        ' By default, subscriptions to transactional publications are synchronized   
        ' continuously, but in this case we only want to synchronize on demand.  
        subscription.AgentSchedule.FrequencyType = ScheduleFrequencyType.OnDemand  
  
        ' Create the pull subscription at the Subscriber.  
        subscription.Create()  
  
        Dim registered As Boolean = False  
  
        ' Verify that the subscription is not already registered.  
        For Each existing As TransSubscription In publication.EnumSubscriptions()  
            If existing.SubscriberName = subscriberName And _  
                existing.SubscriptionDBName = subscriptionDbName Then  
                registered = True  
            End If  
        Next existing  
        If Not registered Then  
            ' Register the subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown( _  
             subscriberName, subscriptionDbName, _  
             SubscriptionSyncType.Automatic, _  
             TransSubscriberType.ReadOnly)  
        End If  
    Else  
        ' Do something here if the publication does not exist.  
        Throw New ApplicationException(String.Format( _  
         "The publication '{0}' does not exist on {1}.", _  
         publicationName, publisherName))  
    End If  
Catch ex As Exception  
    ' Implement the appropriate error handling here.  
    Throw New ApplicationException(String.Format( _  
        "The subscription to {0} could not be created.", publicationName), ex)  
Finally  
    subscriberConn.Disconnect()  
    publisherConn.Disconnect()  
End Try  
  
```  
  
 В следующем примере создается подписка по запросу на публикацию слиянием. Данные учетной записи  Windows для задания агента слияния предоставляются во время выполнения.  
  
```cpp#  
// Define the Publisher, publication, and databases.  
string publicationName = "AdvWorksSalesOrdersMerge";  
string publisherName = publisherInstance;  
string subscriberName = subscriberInstance;  
string subscriptionDbName = "AdventureWorksReplica";  
string publicationDbName = "AdventureWorks";  
string hostname = @"adventure-works\garrett1";  
  
//Create connections to the Publisher and Subscriber.  
ServerConnection subscriberConn = new ServerConnection(subscriberName);  
ServerConnection publisherConn = new ServerConnection(publisherName);  
  
// Create the objects that we need.  
MergePublication publication;  
MergePullSubscription subscription;  
  
try  
{  
    // Connect to the Subscriber.  
    subscriberConn.Connect();  
  
    // Ensure that the publication exists and that   
    // it supports pull subscriptions.  
    publication = new MergePublication();  
    publication.Name = publicationName;  
    publication.DatabaseName = publicationDbName;  
    publication.ConnectionContext = publisherConn;  
  
    if (publication.LoadProperties())  
    {  
        if ((publication.Attributes & PublicationAttributes.AllowPull) == 0)  
        {  
            publication.Attributes |= PublicationAttributes.AllowPull;  
        }  
  
        // Define the pull subscription.  
        subscription = new MergePullSubscription();  
        subscription.ConnectionContext = subscriberConn;  
        subscription.PublisherName = publisherName;  
        subscription.PublicationName = publicationName;  
        subscription.PublicationDBName = publicationDbName;  
        subscription.DatabaseName = subscriptionDbName;  
        subscription.HostName = hostname;  
  
        // Specify the Windows login credentials for the Merge Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin;  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword;  
  
        // Make sure that the agent job for the subscription is created.  
        subscription.CreateSyncAgentByDefault = true;  
  
        // Create the pull subscription at the Subscriber.  
        subscription.Create();  
  
        Boolean registered = false;  
  
        // Verify that the subscription is not already registered.  
        foreach (MergeSubscription existing  
            in publication.EnumSubscriptions())  
        {  
            if (existing.SubscriberName == subscriberName  
                && existing.SubscriptionDBName == subscriptionDbName  
                && existing.SubscriptionType == SubscriptionOption.Pull)  
            {  
                registered = true;  
            }  
        }  
        if (!registered)  
        {  
            // Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown(  
                subscriberName, subscriptionDbName,  
                SubscriptionSyncType.Automatic,  
                MergeSubscriberType.Local, 0);  
        }  
    }  
    else  
    {  
        // Do something here if the publication does not exist.  
        throw new ApplicationException(String.Format(  
            "The publication '{0}' does not exist on {1}.",  
            publicationName, publisherName));  
    }  
}  
catch (Exception ex)  
{  
    // Implement the appropriate error handling here.  
    throw new ApplicationException(String.Format(  
        "The subscription to {0} could not be created.", publicationName), ex);  
}  
finally  
{  
    subscriberConn.Disconnect();  
    publisherConn.Disconnect();  
}  
  
```  
  
```vb  
' Define the Publisher, publication, and databases.  
Dim publicationName As String = "AdvWorksSalesOrdersMerge"  
Dim publisherName As String = publisherInstance  
Dim subscriberName As String = subscriberInstance  
Dim subscriptionDbName As String = "AdventureWorksReplica"  
Dim publicationDbName As String = "AdventureWorks"  
Dim hostname As String = "adventure-works\garrett1"  
  
'Create connections to the Publisher and Subscriber.  
Dim subscriberConn As ServerConnection = New ServerConnection(subscriberName)  
Dim publisherConn As ServerConnection = New ServerConnection(publisherName)  
  
' Create the objects that we need.  
Dim publication As MergePublication  
Dim subscription As MergePullSubscription  
  
Try  
    ' Connect to the Subscriber.  
    subscriberConn.Connect()  
  
    ' Ensure that the publication exists and that   
    ' it supports pull subscriptions.  
    publication = New MergePublication()  
    publication.Name = publicationName  
    publication.DatabaseName = publicationDbName  
    publication.ConnectionContext = publisherConn  
  
    If publication.LoadProperties() Then  
        If (publication.Attributes And PublicationAttributes.AllowPull) = 0 Then  
            publication.Attributes = publication.Attributes _  
            Or PublicationAttributes.AllowPull  
        End If  
  
        ' Define the pull subscription.  
        subscription = New MergePullSubscription()  
        subscription.ConnectionContext = subscriberConn  
        subscription.PublisherName = publisherName  
        subscription.PublicationName = publicationName  
        subscription.PublicationDBName = publicationDbName  
        subscription.DatabaseName = subscriptionDbName  
        subscription.HostName = hostname  
  
        ' Specify the Windows login credentials for the Merge Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword  
  
        ' Make sure that the agent job for the subscription is created.  
        subscription.CreateSyncAgentByDefault = True  
  
        ' Create the pull subscription at the Subscriber.  
        subscription.Create()  
  
        Dim registered As Boolean = False  
  
        ' Verify that the subscription is not already registered.  
        For Each existing As MergeSubscription In _  
        publication.EnumSubscriptions()  
            If existing.SubscriberName = subscriberName Then  
                registered = True  
            End If  
        Next  
        If Not registered Then  
            ' Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown( _  
             subscriberName, subscriptionDbName, _  
             SubscriptionSyncType.Automatic, _  
             MergeSubscriberType.Local, 0)  
        End If  
    Else  
        ' Do something here if the publication does not exist.  
        Throw New ApplicationException(String.Format( _  
         "The publication '{0}' does not exist on {1}.", _  
         publicationName, publisherName))  
    End If  
Catch ex As Exception  
    ' Implement the appropriate error handling here.  
    Throw New ApplicationException(String.Format( _  
        "The subscription to {0} could not be created.", publicationName), ex)  
Finally  
    subscriberConn.Disconnect()  
    publisherConn.Disconnect()  
End Try  
```  
  
 В следующем примере создается подписка по запросу на публикацию слиянием без создания соответствующего задания агента и метаданных подписки в таблице [MSsubscription_properties](../../relational-databases/system-tables/mssubscription-properties-transact-sql.md). Данные учетной записи  Windows для задания агента слияния предоставляются во время выполнения.  
  
```csharp  
// Define the Publisher, publication, and databases.  
string publicationName = "AdvWorksSalesOrdersMerge";  
string publisherName = publisherInstance;  
string subscriberName = subscriberInstance;  
string subscriptionDbName = "AdventureWorksReplica";  
string publicationDbName = "AdventureWorks";  
  
//Create connections to the Publisher and Subscriber.  
ServerConnection subscriberConn = new ServerConnection(subscriberName);  
ServerConnection publisherConn = new ServerConnection(publisherName);  
  
// Create the objects that we need.  
MergePublication publication;  
MergePullSubscription subscription;  
  
try  
{  
    // Connect to the Subscriber.  
    subscriberConn.Connect();  
  
    // Ensure that the publication exists and that   
    // it supports pull subscriptions.  
    publication = new MergePublication();  
    publication.Name = publicationName;  
    publication.DatabaseName = publicationDbName;  
    publication.ConnectionContext = publisherConn;  
  
    if (publication.LoadProperties())  
    {  
        if ((publication.Attributes & PublicationAttributes.AllowPull) == 0)  
        {  
            publication.Attributes |= PublicationAttributes.AllowPull;  
        }  
  
        // Define the pull subscription.  
        subscription = new MergePullSubscription();  
        subscription.ConnectionContext = subscriberConn;  
        subscription.PublisherName = publisherName;  
        subscription.PublicationName = publicationName;  
        subscription.PublicationDBName = publicationDbName;  
        subscription.DatabaseName = subscriptionDbName;  
  
        // Specify that an agent job not be created for this subscription. The  
        // subscription can only be synchronized by running the Merge Agent directly.  
        // Subscripition metadata stored in MSsubscription_properties will not  
        // be available and must be specified at run time.  
        subscription.CreateSyncAgentByDefault = false;  
  
        // Create the pull subscription at the Subscriber.  
        subscription.Create();  
  
        Boolean registered = false;  
  
        // Verify that the subscription is not already registered.  
        foreach (MergeSubscription existing  
            in publication.EnumSubscriptions())  
        {  
            if (existing.SubscriberName == subscriberName  
                && existing.SubscriptionDBName == subscriptionDbName  
                && existing.SubscriptionType == SubscriptionOption.Pull)  
            {  
                registered = true;  
            }  
        }  
        if (!registered)  
        {  
            // Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown(  
                subscriberName, subscriptionDbName,  
                SubscriptionSyncType.Automatic,  
                MergeSubscriberType.Local, 0);  
        }  
    }  
    else  
    {  
        // Do something here if the publication does not exist.  
        throw new ApplicationException(String.Format(  
            "The publication '{0}' does not exist on {1}.",  
            publicationName, publisherName));  
    }  
}  
catch (Exception ex)  
{  
    // Implement the appropriate error handling here.  
    throw new ApplicationException(String.Format(  
        "The subscription to {0} could not be created.", publicationName), ex);  
}  
finally  
{  
    subscriberConn.Disconnect();  
    publisherConn.Disconnect();  
}  
```  
  
```vb  
' Define the Publisher, publication, and databases.  
Dim publicationName As String = "AdvWorksSalesOrdersMerge"  
Dim publisherName As String = publisherInstance  
Dim subscriberName As String = subscriberInstance  
Dim subscriptionDbName As String = "AdventureWorksReplica"  
Dim publicationDbName As String = "AdventureWorks"  
  
'Create connections to the Publisher and Subscriber.  
Dim subscriberConn As ServerConnection = New ServerConnection(subscriberName)  
Dim publisherConn As ServerConnection = New ServerConnection(publisherName)  
  
' Create the objects that we need.  
Dim publication As MergePublication  
Dim subscription As MergePullSubscription  
  
Try  
    ' Connect to the Subscriber.  
    subscriberConn.Connect()  
  
    ' Ensure that the publication exists and that   
    ' it supports pull subscriptions.  
    publication = New MergePublication()  
    publication.Name = publicationName  
    publication.DatabaseName = publicationDbName  
    publication.ConnectionContext = publisherConn  
  
    If publication.LoadProperties() Then  
        If (publication.Attributes And PublicationAttributes.AllowPull) = 0 Then  
            publication.Attributes = publication.Attributes _  
            Or PublicationAttributes.AllowPull  
        End If  
  
        ' Define the pull subscription.  
        subscription = New MergePullSubscription()  
        subscription.ConnectionContext = subscriberConn  
        subscription.PublisherName = publisherName  
        subscription.PublicationName = publicationName  
        subscription.PublicationDBName = publicationDbName  
        subscription.DatabaseName = subscriptionDbName  
  
        ' Specify that an agent job not be created for this subscription. The  
        ' subscription can only be synchronized by running the Merge Agent directly.  
        ' Subscripition metadata stored in MSsubscription_properties will not  
        ' be available and must be specified at run time.  
        subscription.CreateSyncAgentByDefault = False  
  
        ' Create the pull subscription at the Subscriber.  
        subscription.Create()  
  
        Dim registered As Boolean = False  
  
        ' Verify that the subscription is not already registered.  
        For Each existing As MergeSubscription In _  
        publication.EnumSubscriptions()  
            If existing.SubscriberName = subscriberName Then  
                registered = True  
            End If  
        Next  
        If Not registered Then  
            ' Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown( _  
             subscriberName, subscriptionDbName, _  
             SubscriptionSyncType.Automatic, _  
             MergeSubscriberType.Local, 0)  
        End If  
    Else  
        ' Do something here if the publication does not exist.  
        Throw New ApplicationException(String.Format( _  
         "The publication '{0}' does not exist on {1}.", _  
         publicationName, publisherName))  
    End If  
Catch ex As Exception  
    ' Implement the appropriate error handling here.  
    Throw New ApplicationException(String.Format( _  
     "The subscription to {0} could not be created.", publicationName), ex)  
Finally  
    subscriberConn.Disconnect()  
    publisherConn.Disconnect()  
End Try  
```  
  
 В следующем примере создается подписка по запросу на публикацию слиянием, которую можно синхронизировать через Интернет при помощи веб-синхронизации. Данные учетной записи  Windows для задания агента слияния предоставляются во время выполнения. Дополнительные сведения см. в разделе [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md).  
  
```csharp  
// Define the Publisher, publication, and databases.  
string publicationName = "AdvWorksSalesOrdersMerge";  
string publisherName = publisherInstance;  
string subscriberName = subscriberInstance;  
string subscriptionDbName = "AdventureWorksReplica";  
string publicationDbName = "AdventureWorks";  
string hostname = @"adventure-works\garrett1";  
string webSyncUrl = "https://" + publisherInstance + "/WebSync/replisapi.dll";  
  
//Create connections to the Publisher and Subscriber.  
ServerConnection subscriberConn = new ServerConnection(subscriberName);  
ServerConnection publisherConn = new ServerConnection(publisherName);  
  
// Create the objects that we need.  
MergePublication publication;  
MergePullSubscription subscription;  
  
try  
{  
    // Connect to the Subscriber.  
    subscriberConn.Connect();  
  
    // Ensure that the publication exists and that   
    // it supports pull subscriptions and Web synchronization.  
    publication = new MergePublication();  
    publication.Name = publicationName;  
    publication.DatabaseName = publicationDbName;  
    publication.ConnectionContext = publisherConn;  
  
    if (publication.LoadProperties())  
    {  
        if ((publication.Attributes & PublicationAttributes.AllowPull) == 0)  
        {  
            publication.Attributes |= PublicationAttributes.AllowPull;  
        }  
        if ((publication.Attributes & PublicationAttributes.AllowWebSynchronization) == 0)  
        {  
            publication.Attributes |= PublicationAttributes.AllowWebSynchronization;  
        }  
  
        // Define the pull subscription.  
        subscription = new MergePullSubscription();  
        subscription.ConnectionContext = subscriberConn;  
        subscription.PublisherName = publisherName;  
        subscription.PublicationName = publicationName;  
        subscription.PublicationDBName = publicationDbName;  
        subscription.DatabaseName = subscriptionDbName;  
        subscription.HostName = hostname;  
  
        // Specify the Windows login credentials for the Merge Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin;  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword;  
  
        // Enable Web synchronization.  
        subscription.UseWebSynchronization = true;  
        subscription.InternetUrl = webSyncUrl;  
  
        // Specify the same Windows credentials to use when connecting to the  
        // Web server using HTTPS Basic Authentication.  
        subscription.InternetSecurityMode = AuthenticationMethod.BasicAuthentication;  
        subscription.InternetLogin = winLogin;  
        subscription.InternetPassword = winPassword;  
  
        // Ensure that we create a job for this subscription.  
        subscription.CreateSyncAgentByDefault = true;  
  
        // Create the pull subscription at the Subscriber.  
        subscription.Create();  
  
        Boolean registered = false;  
  
        // Verify that the subscription is not already registered.  
        foreach (MergeSubscription existing  
            in publication.EnumSubscriptions())  
        {  
            if (existing.SubscriberName == subscriberName  
                && existing.SubscriptionDBName == subscriptionDbName  
                && existing.SubscriptionType == SubscriptionOption.Pull)  
            {  
                registered = true;  
            }  
        }  
        if (!registered)  
        {  
            // Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown(  
                subscriberName, subscriptionDbName,  
                SubscriptionSyncType.Automatic,  
                MergeSubscriberType.Local, 0);  
        }  
    }  
    else  
    {  
        // Do something here if the publication does not exist.  
        throw new ApplicationException(String.Format(  
            "The publication '{0}' does not exist on {1}.",  
            publicationName, publisherName));  
    }  
}  
catch (Exception ex)  
{  
    // Implement the appropriate error handling here.  
    throw new ApplicationException(String.Format(  
        "The subscription to {0} could not be created.", publicationName), ex);  
}  
finally  
{  
    subscriberConn.Disconnect();  
    publisherConn.Disconnect();  
}  
```  
  
```vb  
' Define the Publisher, publication, and databases.  
Dim publicationName As String = "AdvWorksSalesOrdersMerge"  
Dim publisherName As String = publisherInstance  
Dim subscriberName As String = subscriberInstance  
Dim subscriptionDbName As String = "AdventureWorksReplica"  
Dim publicationDbName As String = "AdventureWorks"  
Dim hostname As String = "adventure-works\garrett1"  
Dim webSyncUrl As String = "https://" + publisherInstance + "/WebSync/replisapi.dll"  
  
'Create connections to the Publisher and Subscriber.  
Dim subscriberConn As ServerConnection = New ServerConnection(subscriberName)  
Dim publisherConn As ServerConnection = New ServerConnection(publisherName)  
  
' Create the objects that we need.  
Dim publication As MergePublication  
Dim subscription As MergePullSubscription  
  
Try  
    ' Connect to the Subscriber.  
    subscriberConn.Connect()  
  
    ' Ensure that the publication exists and that   
    ' it supports pull subscriptions and Web synchronization.  
    publication = New MergePublication()  
    publication.Name = publicationName  
    publication.DatabaseName = publicationDbName  
    publication.ConnectionContext = publisherConn  
  
    If publication.LoadProperties() Then  
        If (publication.Attributes And PublicationAttributes.AllowPull) = 0 Then  
            publication.Attributes = publication.Attributes _  
            Or PublicationAttributes.AllowPull  
        End If  
        If (publication.Attributes And PublicationAttributes.AllowWebSynchronization) = 0 Then  
            publication.Attributes = publication.Attributes _  
            Or PublicationAttributes.AllowWebSynchronization  
        End If  
  
        ' Define the pull subscription.  
        subscription = New MergePullSubscription()  
        subscription.ConnectionContext = subscriberConn  
        subscription.PublisherName = publisherName  
        subscription.PublicationName = publicationName  
        subscription.PublicationDBName = publicationDbName  
        subscription.DatabaseName = subscriptionDbName  
        subscription.HostName = hostname  
        subscription.CreateSyncAgentByDefault = True  
  
        ' Specify the Windows login credentials for the Merge Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword  
  
        ' Enable Web synchronization.  
        subscription.UseWebSynchronization = True  
        subscription.InternetUrl = webSyncUrl  
  
        ' Specify the same Windows credentials to use when connecting to the  
        ' Web server using HTTPS Basic Authentication.  
        subscription.InternetSecurityMode = AuthenticationMethod.BasicAuthentication  
        subscription.InternetLogin = winLogin  
        subscription.InternetPassword = winPassword  
  
        ' Create the pull subscription at the Subscriber.  
        subscription.Create()  
  
        Dim registered As Boolean = False  
  
        ' Verify that the subscription is not already registered.  
        For Each existing As MergeSubscription In _  
        publication.EnumSubscriptions()  
            If existing.SubscriberName = subscriberName Then  
                registered = True  
            End If  
        Next  
        If Not registered Then  
            ' Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown( _  
             subscriberName, subscriptionDbName, _  
             SubscriptionSyncType.Automatic, _  
             MergeSubscriberType.Local, 0)  
        End If  
    Else  
        ' Do something here if the publication does not exist.  
        Throw New ApplicationException(String.Format( _  
         "The publication '{0}' does not exist on {1}.", _  
         publicationName, publisherName))  
    End If  
Catch ex As Exception  
    ' Implement the appropriate error handling here.  
    Throw New ApplicationException(String.Format( _  
     "The subscription to {0} could not be created.", publicationName), ex)  
Finally  
    subscriberConn.Disconnect()  
    publisherConn.Disconnect()  
End Try  
```  
  
## <a name="see-also"></a>См. также:  
 [Replication Management Objects Concepts](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Просмотр и изменение свойств подписки по запросу](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md)   
 [Subscribe to Publications](../../relational-databases/replication/subscribe-to-publications.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  
