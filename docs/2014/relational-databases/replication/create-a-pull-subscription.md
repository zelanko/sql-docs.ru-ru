---
title: Создание подписки по запросу | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: f8868957d7c479de3a51a599deed42c34d6676eb
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52753496"
---
# <a name="create-a-pull-subscription"></a>Создание подписки по запросу
  В данном разделе описывается процесс создания подписки по запросу в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или объектов RMO.  
  
 Настроить подписку по запросу для репликации P2P возможно с помощью скрипта, но не с помощью мастера.  
  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Создайте подписку по запросу на издателе или подписчике с помощью мастера создания подписки. Следуйте инструкциям на страницах мастера, чтобы выполнить следующие действия:  
  
-   Указать издателя и публикацию.  
  
-   Выбрать, где будут выполняться агенты репликации. Для подписки по запросу выберите **Выполнять каждый агент на своем подписчике (подписки по запросу)** на странице **Расположение агента распространителя** или на странице **Расположение агента слияния** в зависимости от типа публикации.  
  
-   Указать подписчиков и базы данных подписок.  
  
-   Указать имена входов и пароли, используемые агентами репликации для подключений:  
  
    -   Для подписок на публикации моментальных снимков и публикации транзакций укажите учетные данные на странице **Безопасность агента распространителя** .  
  
    -   Для подписок на публикации слиянием укажите учетные данные на странице **Безопасность агента слияния** .  
  
     Дополнительные сведения о разрешениях, необходимых каждому агенту, см. в разделе [Модель безопасности агента репликации](security/replication-agent-security-model.md).  
  
-   Указать расписание синхронизации и время, когда подписчик должен быть инициализирован.  
  
-   Укажите дополнительные параметры для публикаций слиянием: тип подписки, значения параметризированного фильтра и сведения для синхронизации по протоколу HTTPS, если для публикации используется веб-синхронизация.  
  
-   Укажите дополнительные параметры для публикаций транзакций, позволяющих использовать обновляемые подписки: должны ли подписчики фиксировать изменения на издателе немедленно или записывать их в очередь; учетные данные, используемые для подключения подписчика к издателю.  
  
-   При необходимости создайте скрипт для подписки.  
  
#### <a name="to-create-a-pull-subscription-from-the-publisher"></a>Создание подписки по запросу с издателя  
  
1.  Подключитесь к издателю в среде [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Щелкните правой кнопкой мыши публикацию, для которой хотите создать одну или более подписок, затем щелкните **Создать подписку**.  
  
4.  Выполните инструкции на страницах мастера создания подписки.  
  
#### <a name="to-create-a-pull-subscription-from-the-subscriber"></a>Создание подписки по запросу с подписчика  
  
1.  Подключитесь к подписчику в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** .  
  
3.  Щелкните правой кнопкой мыши папку **Локальные подписки** , затем щелкните **Создать подписку**.  
  
4.  На странице **Публикация** мастера создания подписки выберите **\<Найти издатель SQL Server>** или **\<Найти издатель Oracle>** из раскрывающегося списка **Издатель**.  
  
5.  Соединитесь с издателем в диалоговом окне **Соединение с сервером** .  
  
6.  Выберите публикацию на странице **Публикация** .  
  
7.  Выполните инструкции на страницах мастера создания подписки.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Подписки по запросу можно создавать программно с помощью хранимых процедур репликации. Какие именно хранимые процедуры будут при этом применяться, зависит от типа публикации, к которой относится подписка.  
  
#### <a name="to-create-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>Создание подписки по запросу на публикацию моментальных снимков или транзакций  
  
1.  Проверьте на издателе, поддерживает ли публикация подписки по запросу. Для этого выполните процедуру [sp_helppublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).  
  
    -   Если в результирующем наборе значение параметра **allow_pull** равно **1**, подписки по запросу поддерживаются.  
  
    -   Если значение **allow_pull** — **0**, выполнение [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), указав **allow_pull**для **@property** и `true` для **@value**.  
  
2.  На подписчике выполните процедуру [sp_addpullsubscription (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql). Укажите параметр **@publisher** и **@publication**. Сведения об обновлении подписок см. в разделе [Создание обновляемых подписок для публикаций транзакций](publish/create-an-updatable-subscription-to-a-transactional-publication.md).  
  
3.  На подписчике выполните процедуру [sp_addpullsubscription_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql). Укажите следующее.  
  
    -   Значения параметров **@publisher**, **@publisher_db**и **@publication** .  
  
    -   Значения параметров [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, от имени которого на подписчике будет запущен агент распространителя, в качестве значений параметров **@job_login** и **@job_password**.  
  
        > [!NOTE]  
        >  Для соединений, производимых с использованием встроенной проверки подлинности Windows, в параметрах **@job_login** и **@job_password**. Агент распространителя всегда создает локальное соединение с подписчиком с использованием встроенной проверки подлинности Windows. По умолчанию агент установит соединение с распространителем с помощью встроенной проверки подлинности Windows.  
  
    -   (Необязательно) Значение **0** для **@distributor_security_mode** и [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сведения об имени входа **@distributor_login** и **@distributor_password**, если необходимо использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности при подключении к распространителю.  
  
    -   Расписание задания агента распространителя для этой подписки. Дополнительные сведения см. в статье [Specify Synchronization Schedules](specify-synchronization-schedules.md).  
  
4.  Чтобы зарегистрировать подписку по запросу, выполните на издателе хранимую процедуру [sp_addsubscription (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql). Задайте значения для параметров **@publication**, **@subscriber**и **@destination_db**. В качестве значения параметра **@subscription_type** в качестве значения параметра **@subscription_type**.  
  
#### <a name="to-create-a-pull-subscription-to-a-merge-publication"></a>Создание подписки по запросу на публикацию слиянием  
  
1.  Проверьте на издателе, поддерживает ли публикация подписки по запросу. Для этого выполните процедуру [sp_helpmergepublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql).  
  
    -   Если в результирующем наборе значение параметра **allow_pull** равно **1**, подписки по запросу поддерживаются.  
  
    -   Если значение **allow_pull** — **0**, выполнение [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), указав **allow_pull** для **@property** и `true` для **@value**.  
  
2.  На подписчике выполните процедуру [sp_addmergepullsubscription (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql). Укажите значения параметров **@publisher**, **@publisher_db**, **@publication**, а также следующих:  
  
    -   **@subscriber_type** — укажите значение **local** для клиентской подписки или **global** — для серверной;  
  
    -   **@subscription_priority** — укажите приоритет подписки (от**0,00** до **99,99**). Это значение необходимо указывать только для серверной подписки.  
  
         Дополнительные сведения см. в статье [Расширенное обнаружение и разрешение конфликтов репликации слиянием](merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
3.  На подписчике выполните процедуру [sp_addmergepullsubscription_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql). Укажите значения следующих параметров.  
  
    -   **@publisher**, **@publisher_db**и **@publication**.  
  
    -   учетные данные пользователя Windows, от имени которого на подписчике будет запущен агент слияния, в качестве значений параметров **@job_login** и **@job_password**.  
  
        > [!NOTE]  
        >  Для соединений, производимых с использованием встроенной проверки подлинности Windows, в параметрах **@job_login** и **@job_password**. Агент слияния всегда создает локальное соединение с подписчиком с использованием встроенной проверки подлинности Windows. По умолчанию агент установит соединение с распространителем и издателем с помощью встроенной проверки подлинности Windows.  
  
    -   (Необязательно.) Значение **0** в качестве значения параметра **@distributor_security_mode** и данные входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для параметров **@distributor_login** и **@distributor_password**, если для соединения с распространителем нужно использовать проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    -   (Необязательно.) Значение **0** в качестве значения параметра **@publisher_security_mode** и данные входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для параметров **@publisher_login** и **@publisher_password**, если для соединения с распространителем нужно использовать проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    -   Расписание агента слияния для данной подписки. Дополнительные сведения см. в разделе [Создание обновляемых подписок для публикаций транзакций](publish/create-an-updatable-subscription-to-a-transactional-publication.md).  
  
4.  На издателе выполните процедуру [sp_addmergesubscription (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql). Укажите значения параметров **@publication**, **@subscriber**, **@subscriber_db**и значение **@subscription_type** в качестве значения параметра **@subscription_type**. После этого подписка по запросу будет зарегистрирована.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере создается подписка по запросу на публикацию транзакций. Первый пакет выполняется на подписчике, а второй — на издателе. Имя входа и пароль предоставляются во время выполнения переменными сценария sqlcmd.  
  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent](../../snippets/tsql/SQL15/replication/howto/tsql/createtranpullsub.sql#sp_addtranpullsubscriptionagent)]  
  
 [!code-sql[HowTo#sp_addtranpullsubscription](../../snippets/tsql/SQL15/replication/howto/tsql/createtranpullsub.sql#sp_addtranpullsubscription)]  
  
 В следующем примере создается подписка по запросу на публикацию слиянием. Первый пакет выполняется на подписчике, а второй — на издателе. Значения имени входа и пароля задаются во время выполнения с помощью переменных скриптов **sqlcmd** .  
  
 [!code-sql[HowTo#sp_addmergepullsubscriptionagent](../../snippets/tsql/SQL15/replication/howto/tsql/createmergepullsub.sql#sp_addmergepullsubscriptionagent)]  
  
 [!code-sql[HowTo#sp_addmergepullsubscription](../../snippets/tsql/SQL15/replication/howto/tsql/createmergepullsub.sql#sp_addmergepullsubscription)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Конкретные классы RMO, используемые для этого, зависят от типа репликации, к которой относится подписка.  
  
#### <a name="to-create-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>Создание подписки по запросу на публикацию моментальных снимков или транзакций  
  
1.  Создайте соединения с подписчиком и издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  На основе соединения с издателем, созданного на шаге 1, создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransPublication> . Задайте свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> и <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A>. Если метод возвращает значение `false`, то либо неверно определены свойства, указанные на шаге 2, либо публикация не существует на сервере.  
  
4.  Выполните операцию «поразрядное логическое И» (`&` в Visual C# и `And` в Visual Basic) над свойством <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> и флагом <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull>. Если результат равен <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, присвойте свойству <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> результат операции «поразрядное логическое ИЛИ» (`|` в Visual C# и `Or` в Visual Basic) над свойством <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> и флагом <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull>. Затем вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> , чтобы включить подписку по запросу.  
  
5.  Если база данных подписки не существует, создайте ее с помощью класса <xref:Microsoft.SqlServer.Management.Smo.Database> . Дополнительные сведения см. в статье [Creating, Altering, and Removing Databases](../server-management-objects-smo/tasks/creating-altering-and-removing-databases.md) (Создание, изменение и удаление баз данных).  
  
6.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransPullSubscription> .  
  
7.  Укажите следующие свойства подписки:  
  
    -   соединение ( <xref:Microsoft.SqlServer.Management.Common.ServerConnection> ) с подписчиком, созданное на шаге 1, в свойстве <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>;  
  
    -   имя базы данных подписки в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>;  
  
    -   Имя издателя в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.  
  
    -   имя базы данных публикации в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>;  
  
    -   имя публикации в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>;  
  
    -   данные учетной записи пользователя [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, от имени которого на подписчике будет запущен агент распространителя, в свойствах <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A>, <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> или <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> объекта <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A>. Эта учетная запись будет использоваться для создания локальных соединений с подписчиком, а также для удаленных соединений с использованием проверки подлинности Windows.  
  
        > [!NOTE]  
        >  Указывать свойство <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> необязательно, если подписка создается членом предопределенной роли сервера `sysadmin`, однако рекомендуется это сделать. В этом случае агент будет выполнять олицетворение учетную запись агента SQL Server. Дополнительные сведения см. в статье [Модель безопасности агента репликации](security/replication-agent-security-model.md).  
  
    -   (необязательно) значение `true` в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A>, чтобы создать задание агента, используемое для синхронизации подписки. Если указано значение `false` (значение по умолчанию), подписку можно синхронизировать только программно, и поэтому придется указывать дополнительные свойства <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> при доступе к этому объекту из <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizationAgent%2A>. Дополнительные сведения см. в статье [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).  
  
        > [!NOTE]  
        >  Агент SQL Server доступен не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Перечень функций, поддерживаемых в разных выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md). При указании значения `true` для подписчиков выпуска Express задание агента не создается. Однако метаданные, существенные для работы подписки, сохраняются на подписчике.  
  
    -   (необязательно) при соединении с распространителем с проверкой подлинности SQL Server укажите значения свойств <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> и <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> или <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> объекта <xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> ;  
  
8.  Вызовите метод <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> .  
  
9. Используя экземпляр класса <xref:Microsoft.SqlServer.Replication.TransPublication> , созданный на шаге 2, вызовите метод <xref:Microsoft.SqlServer.Replication.TransPublication.MakePullSubscriptionWellKnown%2A> , чтобы зарегистрировать подписку по запросу для данного издателя. Если данная регистрация уже существует, возникнет исключение.  
  
#### <a name="to-create-a-pull-subscription-to-a-merge-publication"></a>Создание подписки по запросу на публикацию слиянием  
  
1.  Создайте соединения с подписчиком и издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  На основе соединения с издателем, созданного на шаге 1, создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePublication> . Задайте свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>и <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A>. Если метод возвращает значение `false`, то либо неверно определены свойства, указанные на шаге 2, либо публикация не существует на сервере.  
  
4.  Выполните операцию «поразрядное логическое И» (`&` в Visual C# и `And` в Visual Basic) над свойством <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> и флагом <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull>. Если результат равен <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, присвойте свойству <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> результат операции «поразрядное логическое ИЛИ» (`|` в Visual C# и `Or` в Visual Basic) над свойством <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> и флагом <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull>. Затем вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> , чтобы включить подписку по запросу.  
  
5.  Если база данных подписки не существует, создайте ее с помощью класса <xref:Microsoft.SqlServer.Management.Smo.Database> . Дополнительные сведения см. в статье [Creating, Altering, and Removing Databases](../server-management-objects-smo/tasks/creating-altering-and-removing-databases.md) (Создание, изменение и удаление баз данных).  
  
6.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePullSubscription> .  
  
7.  Укажите следующие свойства подписки:  
  
    -   соединение ( <xref:Microsoft.SqlServer.Management.Common.ServerConnection> ) с подписчиком, созданное на шаге 1, в свойстве <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>;  
  
    -   имя базы данных подписки в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>;  
  
    -   Имя издателя в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.  
  
    -   имя базы данных публикации в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>;  
  
    -   имя публикации в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>;  
  
    -   данные учетной записи пользователя [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, от имени которого на подписчике будет запущен агент слияния, в свойствах <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A>, <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> или <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> объекта <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A>. Эта учетная запись будет использоваться для создания локальных соединений с подписчиком, а также для удаленных соединений с использованием проверки подлинности Windows.  
  
        > [!NOTE]  
        >  Указывать свойство <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> необязательно, если подписка создается членом предопределенной роли сервера `sysadmin`, однако рекомендуется это сделать. В этом случае агент будет выполнять олицетворение учетную запись агента SQL Server. Дополнительные сведения см. в статье [Модель безопасности агента репликации](security/replication-agent-security-model.md).  
  
    -   (необязательно) значение `true` в свойстве <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A>, чтобы создать задание агента, используемое для синхронизации подписки. Если указано значение `false` (значение по умолчанию), подписку можно синхронизировать только программно, и поэтому придется указывать дополнительные свойства <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> при доступе к этому объекту из <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizationAgent%2A>. Дополнительные сведения см. в статье [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).  
  
    -   (необязательно) при соединении с распространителем с проверкой подлинности SQL Server укажите значения свойств <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> и <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> или <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> объекта <xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> ;  
  
    -   (необязательно) при соединении с издателем с проверкой подлинности SQL Server укажите значения свойств <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> и <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> или <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> объекта <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherSecurity%2A> .  
  
8.  Вызовите метод <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> .  
  
9. Используя экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePublication> , созданный на шаге 2, вызовите метод <xref:Microsoft.SqlServer.Replication.MergePublication.MakePullSubscriptionWellKnown%2A> , чтобы зарегистрировать подписку по запросу для данного издателя. Если данная регистрация уже существует, возникнет исключение.  
  
###  <a name="PShellExample"></a> Пример (объекты RMO)  
 В следующем примере создается подписка по запросу на публикацию транзакций. Данные учетной записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows для задания агента распространителя предоставляются во время выполнения.  
  
 [!code-csharp[HowTo#rmo_CreateTranPullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createtranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranPullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createtranpullsub)]  
  
 В следующем примере создается подписка по запросу на публикацию слиянием. Данные учетной записи  Windows для задания агента слияния предоставляются во время выполнения.  
  
 [!code-csharp[HowTo#rmo_CreateMergePullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergepullsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergepullsub)]  
  
 В следующем примере создается подписка по запросу на публикацию слиянием без создания соответствующего задания агента и метаданных подписки в таблице [MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql). Данные учетной записи  Windows для задания агента слияния предоставляются во время выполнения.  
  
 [!code-csharp[HowTo#rmo_CreateMergePullSub_NoJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergepullsub_nojob)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePullSub_NoJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergepullsub_nojob)]  
  
 В следующем примере создается подписка по запросу на публикацию слиянием, которую можно синхронизировать через Интернет при помощи веб-синхронизации. Данные учетной записи  Windows для задания агента слияния предоставляются во время выполнения. Дополнительные сведения см. в разделе [Configure Web Synchronization](configure-web-synchronization.md).  
  
 [!code-csharp[HowTo#rmo_CreateMergePullSub_WebSync](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergepullsub_websync)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePullSub_WebSync](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergepullsub_websync)]  
  
## <a name="see-also"></a>См. также:  
 [Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md)   
 [Просмотр и изменение свойств подписки по запросу](view-and-modify-pull-subscription-properties.md)   
 [Configure Web Synchronization](configure-web-synchronization.md)   
 [Subscribe to Publications](subscribe-to-publications.md)   
 [Рекомендации по защите репликации](security/replication-security-best-practices.md)  
  
  
