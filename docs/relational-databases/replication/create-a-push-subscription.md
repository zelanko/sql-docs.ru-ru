---
title: "Создание принудительной подписки | Microsoft Docs"
ms.custom: ""
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "принудительные подписки [репликация SQL Server], создание"
  - "подписка репликации слиянием [репликация SQL Server], принудительные подписки"
  - "принудительные подписки [репликация SQL Server], отправка"
  - "репликация моментальных снимков [SQL Server], подписка"
  - "репликация транзакций, подписка"
ms.assetid: adfbbc61-58d1-4330-9ad6-b14ab1142e2b
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# Создание принудительной подписки
  В этом разделе описывается создание принудительной подписки в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], или объекты управления репликацией (RMO). Дополнительные сведения о создании принудительной подписки для не -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчика, в разделе [Создать подписку для подписчика не SQL Server](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md).  
  
 
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Для создания принудительной подписки на издателе или подписчике используется мастера создания подписки. Следуйте инструкциям на страницах мастера, чтобы выполнить следующие действия:  
  
-   Указать издателя и публикацию.  
  
-   Выбрать, где будут выполняться агенты репликации. Для принудительной подписки выберите **выполнять все агенты на распространителе (принудительные подписки)** на **Расположение агента распространителя** страницы или **Расположение агента слияния** страницы, в зависимости от типа публикации.  
  
-   Указать подписчиков и базы данных подписок.  
  
-   Указать имена входов и пароли, используемые агентами репликации для подключений:  
  
    -   Для подписок на публикации моментальных снимков и публикации транзакций укажите учетные данные на странице **Безопасность агента распространителя** .  
  
    -   Для подписок на публикации слиянием укажите учетные данные на странице **Безопасность агента слияния** .  
  
     Сведения о разрешениях, необходимых для каждого агента см. в разделе [модель безопасности агента репликации](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
-   Указать расписание синхронизации и время, когда подписчик должен быть инициализирован.  
  
-   Указать дополнительные параметры для публикаций слиянием (тип подписки) и значения для параметризованного фильтра.  
  
-   Укажите дополнительные параметры для публикаций транзакций, позволяющих использовать обновляемые подписки: должны ли подписчики фиксировать изменения на издателе немедленно или записывать их в очередь; учетные данные, используемые для подключения подписчика к издателю.  
  
-   При необходимости создайте скрипт для подписки.  
  
#### Создание принудительной подписки с издателя.  
  
1.  Подключитесь к издателю в среде [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Щелкните правой кнопкой мыши публикацию, для которой нужно создать одну или несколько подписок и нажмите кнопку **новые подписки**.  
  
4.  Выполните инструкции на страницах мастера создания подписки.  
  
#### Создание принудительной подписки с подписчика  
  
1.  Подключитесь к подписчику в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** .  
  
3.  Щелкните правой кнопкой мыши **Локальные подписки** папку и выберите пункт **новые подписки**.  
  
4.  На **публикации** страницы мастера создания подписки, выберите **\< найти издатель SQL Server>** или **\< найти издатель Oracle>** из **издателя** раскрывающегося списка.  
  
5.  Соединитесь с издателем в диалоговом окне **Соединение с сервером** .  
  
6.  Выберите публикацию на странице **Публикация** .  
  
7.  Выполните инструкции на страницах мастера создания подписки.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Принудительные подписки могут быть созданы программно, с помощью хранимых процедур репликации. Какие именно хранимые процедуры будут при этом применяться, зависит от типа публикации, к которой относится подписка.  
  
> **ВАЖНО!** По возможности следует предлагать пользователям вводить учетные данные безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
#### Создание принудительной подписки на публикацию моментальных снимков или транзакций  
  
1.  На издателе в базе данных публикации, убедитесь, что публикация поддерживает принудительные подписки, выполнив [sp_helppublication](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md).  
  
    -   Если значение **allow_push** — **1**, то принудительная подписка поддерживается.  
  
    -   Если значение **allow_push** — **0**, выполнение [sp_changepublication](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), указав **allow_push** для **@property** и **true** для **@value**.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addsubscription](https://msdn.microsoft.com/library/ms181702.aspx). Укажите **@publication**, **@subscriber** и **@destination_db**. Укажите значение **push** для **@subscription_type**. Сведения об обновлении подписок см. в разделе [Создание обновляемых подписок на публикацию транзакций](https://msdn.microsoft.com/library/ms152769.aspx).  
  
3.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addpushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md). Укажите следующее.  
  
    -    **@Subscriber**, **@subscriber_db**, и **@publication** параметров.  
  
    -   [!INCLUDE[msCoName](../../includes/msconame-md.md)] Учетные данные Windows, под которыми агент распространителя на распространителе **@job_login** и **@job_password**.  
  
        > **Примечание:** соединения с использованием встроенной проверки подлинности Windows всегда использовать учетные данные Windows, заданные **@job_login** и **@job_password**. Агент распространителя всегда создает локальные соединения с распространителем через встроенную систему проверки подлинности Windows. По умолчанию агент подключается к подписчику через встроенную систему проверки подлинности Windows;  
  
    -   (Необязательно) Значение **0** для **@subscriber_security_mode** и [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сведения об имени входа **@subscriber_login** и **@subscriber_password**. Эти параметры указываются в том случае, если при соединении с подписчиком необходимо использовать проверку подлинности SQL Server.  
  
    -   Расписание задания агента распространителя для этой подписки. Дополнительные сведения см. в статье [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
    > **ВАЖНО!** При создании принудительной подписки на издателе с удаленным распространителем значения, указываемые для всех параметров, включая *job_login* и *job_password*, отправляются распространителю в виде обычного текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
#### Создание принудительной подписки на публикацию слиянием  
  
1.  На издателе в базе данных публикации, убедитесь, что публикация поддерживает принудительные подписки, выполнив [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md).  
  
    -   Если значение **allow_push** — **1**, публикация поддерживает принудительные подписки.  
  
    -   Если значение **allow_push** не **1**, выполнение [sp_changemergepublication](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), указав **allow_push** для **@property** и **true** для **@value**.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergesubscription](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md), указав следующие параметры:  
  
    -   **@publication**. Имя публикации.  
  
    -   **@subscriber_type**. Для клиентской подписки укажите **local** , а для серверной — **global**.  
  
    -   **@subscription_priority**. Для серверной подписки укажите приоритет подписки (**0,00** для **99,99**).  
  
         Дополнительные сведения см. в статье [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
3.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergepushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md). Укажите следующее.  
  
    -   **@Subscriber**, **@subscriber_db**, и **@publication** параметров.  
  
    -   Учетные данные Windows, с которыми работает агент слияния на распространителе **@job_login** и **@job_password**.  
  
        > **Примечание:**  соединения с использованием встроенной проверки подлинности Windows всегда использовать учетные данные Windows, заданные **@job_login** и **@job_password**. Агент слияния всегда создает локальные соединения с распространителем через встроенную систему проверки подлинности Windows. По умолчанию агент подключается к подписчику через встроенную систему проверки подлинности Windows;  
  
    -   (Необязательно) Значение **0** для **@subscriber_security_mode** и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сведения об имени входа **@subscriber_login** и **@subscriber_password**. Эти параметры указываются в том случае, если при соединении с подписчиком необходимо использовать проверку подлинности SQL Server.  
  
    -   (Необязательно) Значение **0** для **@publisher_security_mode** и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сведения об имени входа **@publisher_login** и **@publisher_password**. Эти параметры указываются в том случае, если при соединении с издателем необходимо использовать проверку подлинности SQL Server.  
  
    -   Расписание агента слияния для данной подписки. Дополнительные сведения см. в статье [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
    > **ВАЖНО!** При создании принудительной подписки на издателе с удаленным распространителем значения, указываемые для всех параметров, включая *job_login* и *job_password*, отправляются распространителю в виде обычного текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере создается принудительная подписка на публикацию транзакций. Значения для имени входа и пароля передаются во время выполнения в переменных скрипта **sqlcmd** .  
  
 [!code-sql[HowTo#sp_addtranpushsubscription_agent](../../relational-databases/replication/codesnippet/tsql/create-a-push-subscription_1.sql)]  
  
 В следующем примере создается принудительная подписка на публикацию слиянием. Значения для имени входа и пароля передаются во время выполнения в переменных скрипта **sqlcmd** .  
  
 [!code-sql[HowTo#sp_addmergepushsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/create-a-push-subscription_2.sql)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Принудительные подписки можно создавать программно с помощью объектов RMO. Конкретные классы объектов RMO, используемые для этого, зависят от типа публикации, для которой создается подписка.  
  
> **ВАЖНО!** По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если необходимо хранить учетные данные, используйте [службы шифрования](http://go.microsoft.com/fwlink/?LinkId=34733) , предоставляемые платформой [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
#### Создание принудительной подписки на публикацию моментальных снимков или транзакций  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.TransPublication> класса с помощью соединения с издателем из шага 1. Укажите <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>, и <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод. Если этот метод возвращает значение **false**, то на шаге 2 свойствам были присвоены неверные значения, или публикация на сервере не существует.  
  
4.  Выполните побитовую логическую операцию и (**&** в Visual C# и **и** в Visual Basic) между <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> свойство и <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. Если результатом является <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, задайте <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> результат битовой операции логического или (**|** в Visual C# и **или** в Visual Basic) между <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> и <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. Затем вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> Чтобы включить принудительные подписки.  
  
5.  Если база данных подписки не существует, создайте его с помощью <xref:Microsoft.SqlServer.Management.Smo.Database> класса. Дополнительные сведения см. в разделе [Создание, изменение и удаление баз данных](../../relational-databases/server-management-objects-smo/tasks/creating-altering-and-removing-databases.md).  
  
6.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.TransSubscription> класса.  
  
7.  Укажите следующие свойства подписки:  
  
    -    <xref:Microsoft.SqlServer.Management.Common.ServerConnection> издателем, созданное на шаге 1, для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   Имя базы данных подписки для <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>.  
  
    -   Имя подписчика для <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>.  
  
    -   Имя базы данных публикации для <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>.  
  
    -   Имя публикации, для <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>.  
  
    -   <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> и <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> или <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> поля <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> учетные данные для [!INCLUDE[msCoName](../../includes/msconame-md.md)] учетной записи Windows, под которой агент распространителя запускается на распространителе. Эта учетная запись будет использоваться для создания локальных соединений с распространителем и удаленных с использованием проверки подлинности Windows.  
  
        > **Примечание:** параметр <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> не является обязательным, если подписка создается членом **sysadmin** предопределенной роли сервера, однако рекомендуется. В этом случае агент будет выполнять олицетворение учетную запись агента SQL Server. Дополнительные сведения см. в статье [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   (Необязательно) Значение **true** (по умолчанию) для <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A> Создать задание агента, который используется для синхронизации подписки. Если будет присвоено значение **false**, подписку можно будет синхронизировать только программно.  
  
    -   (Необязательно) Задайте <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> и <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> или <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> поля <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> при использовании проверки подлинности SQL Server для подключения к подписчику.  
  
8.  Вызов <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> метод.  
  
    > **Важно!**При создании принудительной подписки на издателе с удаленным распространителем значения, заданные для всех свойств, включая <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A>, отправляются распространителю в виде обычного текста. Необходимо зашифровать соединение между издателем и его удаленным распространителем перед вызовом метода <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> метод. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
#### Создание принудительной подписки на публикацию слиянием  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergePublication> класса с помощью соединения с издателем из шага 1. Укажите <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>, и <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод. Если этот метод возвращает значение **false**, то на шаге 2 свойствам были присвоены неверные значения, или публикация на сервере не существует.  
  
4.  Выполните побитовую логическую операцию и (**&** в Visual C# и **и** в Visual Basic) между <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> свойство и <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. Если результатом является <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, задайте <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> результат битовой операции логического или (**|** в Visual C# и **или** в Visual Basic) между <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> и <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. Затем вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> Чтобы включить принудительные подписки.  
  
5.  Если база данных подписки не существует, создайте его с помощью <xref:Microsoft.SqlServer.Management.Smo.Database> класса. Дополнительные сведения см. в разделе [Создание, изменение и удаление баз данных](../../relational-databases/server-management-objects-smo/tasks/creating-altering-and-removing-databases.md).  
  
6.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergeSubscription> класса.  
  
7.  Укажите следующие свойства подписки:  
  
    -    <xref:Microsoft.SqlServer.Management.Common.ServerConnection> издателем, созданное на шаге 1, для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   Имя базы данных подписки для <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>.  
  
    -   Имя подписчика для <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>.  
  
    -   Имя базы данных публикации для <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>.  
  
    -   Имя публикации, для <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>.  
  
    -   <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> и <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> или <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> поля <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> учетные данные для [!INCLUDE[msCoName](../../includes/msconame-md.md)] учетной записи Windows, под которой выполняется агент слияния на распространителе. Эта учетная запись будет использоваться для создания локальных соединений с распространителем и удаленных с использованием проверки подлинности Windows.  
  
        > **Примечание:** параметр <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> не является обязательным, если подписка создается членом **sysadmin** предопределенной роли сервера, однако рекомендуется. В этом случае агент будет выполнять олицетворение учетную запись агента SQL Server. Дополнительные сведения см. в статье [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   (Необязательно) Значение **true** (по умолчанию) для <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A> Создать задание агента, который используется для синхронизации подписки. Если будет присвоено значение **false**, подписку можно будет синхронизировать только программно.  
  
    -   (Необязательно) Задайте <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> и <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> или <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> поля <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> при использовании проверки подлинности SQL Server для подключения к подписчику.  
  
    -   (Необязательно) Задайте <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> и <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> или <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> поля <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherSecurity%2A> при использовании проверки подлинности SQL Server для подключения к издателю.  
  
8.  Вызов <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> метод.  
  
    > **ВАЖНО!**  При создании принудительной подписки на издателе с удаленным распространителем значения, заданные для всех свойств, включая <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A>, отправляются распространителю в виде обычного текста. Необходимо зашифровать соединение между издателем и его удаленным распространителем перед вызовом метода <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> метод. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 В следующем примере создается принудительная подписка на публикацию транзакций. Данные учетной записи Windows для задания агента распространителя предоставляются во время выполнения.  
  
 [!code-csharp[HowTo#rmo_CreateTranPushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createtranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranPushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createtranpushsub)]  
  
 В следующем примере создается принудительная подписка на публикацию слиянием. Данные учетной записи Windows для задания агента слияния предоставляются во время выполнения.  
  
 [!code-csharp[HowTo#rmo_CreateMergePushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepushsub)]  
  
## См. также:  
 [Просмотр и изменение свойств принудительной подписки](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Создание публикации](../../relational-databases/replication/publish/create-a-publication.md)   
 [Основные понятия объектов RMO](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Синхронизация принудительной подписки](../../relational-databases/replication/synchronize-a-push-subscription.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)   
 [Использование программы sqlcmd с переменными скрипта](../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)  
  
  