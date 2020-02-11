---
title: Создание принудительной подписки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- push subscriptions [SQL Server replication], creating
- merge replication subscribing [SQL Server replication], push subscriptions
- subscriptions [SQL Server replication], push
- snapshot replication [SQL Server], subscribing
- transactional replication, subscribing
ms.assetid: adfbbc61-58d1-4330-9ad6-b14ab1142e2b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b571bec94c873b830654126e39d75d554599e5fa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62721736"
---
# <a name="create-a-push-subscription"></a>Создание принудительной подписки
  В данном разделе описывается процесс создания принудительной подписки в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или объектов RMO. Дополнительные сведения о создании принудительной подписки для[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков, отличных от, см. в статье [Создание подписки для подписчика, не являющегося SQL Server](create-a-subscription-for-a-non-sql-server-subscriber.md).  
  
  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Для создания принудительной подписки на издателе или подписчике используется мастера создания подписки. Следуйте инструкциям на страницах мастера, чтобы выполнить следующие действия:  
  
-   Указать издателя и публикацию.  
  
-   Выбрать, где будут выполняться агенты репликации. Для принудительной подписки выберите **Выполнять все агенты на распространителе (принудительные подписки)** на странице **Расположение агента распространителя** или на странице **Расположение агента слияния** в зависимости от типа публикации.  
  
-   Указать подписчиков и базы данных подписок.  
  
-   Указать имена входов и пароли, используемые агентами репликации для подключений:  
  
    -   Для подписок на публикации моментальных снимков и публикации транзакций укажите учетные данные на странице **Безопасность агента распространителя** .  
  
    -   Для подписок на публикации слиянием укажите учетные данные на странице **Безопасность агента слияния** .  
  
     Дополнительные сведения о разрешениях, необходимых каждому агенту, см. в статье [Replication Agent Security Model](security/replication-agent-security-model.md) (Модель безопасности агента репликации).  
  
-   Указать расписание синхронизации и время, когда подписчик должен быть инициализирован.  
  
-   Указать дополнительные параметры для публикаций слиянием (тип подписки) и значения для параметризованного фильтра.  
  
-   Укажите дополнительные параметры для публикаций транзакций, позволяющих использовать обновляемые подписки: должны ли подписчики фиксировать изменения на издателе немедленно или записывать их в очередь; учетные данные, используемые для подключения подписчика к издателю.  
  
-   При необходимости создайте скрипт для подписки.  
  
#### <a name="to-create-a-push-subscription-from-the-publisher"></a>Создание принудительной подписки с издателя.  
  
1.  Подключитесь к издателю [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]в, а затем разверните узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Щелкните правой кнопкой мыши публикацию, для которой хотите создать одну или более подписок, затем щелкните **Создать подписку**.  
  
4.  Выполните инструкции на страницах мастера создания подписки.  
  
#### <a name="to-create-a-push-subscription-from-the-subscriber"></a>Создание принудительной подписки с подписчика  
  
1.  Подключитесь к подписчику в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** .  
  
3.  Щелкните правой кнопкой мыши папку **Локальные подписки** , затем щелкните **Создать подписку**.  
  
4.  На странице **Публикация** мастера создания подписки выберите **\<Найти издатель SQL Server>** или **\<Найти издатель Oracle>** из раскрывающегося списка **Издатель**.  
  
5.  Соединитесь с издателем в диалоговом окне **Соединение с сервером** .  
  
6.  Выберите публикацию на странице **Публикация** .  
  
7.  Выполните инструкции на страницах мастера создания подписки.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Принудительные подписки могут быть созданы программно, с помощью хранимых процедур репликации. Какие именно хранимые процедуры будут при этом применяться, зависит от типа публикации, к которой относится подписка.  
  
> [!IMPORTANT]  
>  По возможности следует предлагать пользователям вводить учетные данные безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
#### <a name="to-create-a-push-subscription-to-a-snapshot-or-transactional-publication"></a>Создание принудительной подписки на публикацию моментальных снимков или транзакций  
  
1.  На издателе в базе данных публикации с помощью процедуры [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)проверьте, поддерживает ли публикация принудительные подписки.  
  
    -   Если значение **allow_push** равно **1**, то принудительная подписка поддерживается.  
  
    -   Если значение **allow_push** равно **0**, выполните [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), указав **allow_push** для **@property** и `true` для. **@value**  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql). Укажите **@publication**, **@subscriber** и **@destination_db**. Укажите значение **push** в **@subscription_type**. Дополнительные сведения об обновлении подписок см. в разделе [Создание обновляемой подписки для публикации транзакций](publish/create-an-updatable-subscription-to-a-transactional-publication.md) .  
  
3.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql). Укажите следующие значения.  
  
    -   Параметры **@subscriber**, **@subscriber_db**и **@publication** .  
  
    -   Учетные данные [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, с которыми работает агент распространения на распространителе **@job_login** , **@job_password**для и.  
  
        > [!NOTE]  
        >  Соединения, выполняемые с помощью встроенной проверки подлинности Windows **@job_login** , **@job_password**всегда используют учетные данные Windows, указанные в и. Агент распространителя всегда создает локальные соединения с распространителем через встроенную систему проверки подлинности Windows. По умолчанию агент подключается к подписчику через встроенную систему проверки подлинности Windows;  
  
    -   (необязательно) Значение **0** в **@subscriber_security_mode** и сведения об имени входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в параметрах **@subscriber_login** и значение **@subscriber_password**. Эти параметры указываются в том случае, если при соединении с подписчиком необходимо использовать проверку подлинности SQL Server.  
  
    -   Расписание задания агента распространителя для этой подписки. Дополнительные сведения см. в разделе [Указание расписаний синхронизации](specify-synchronization-schedules.md).  
  
    > [!IMPORTANT]  
    >  При создании принудительной подписки на издателе с удаленным распространителем значения, указываемые для всех параметров, включая *job_login* и *job_password*, передаются распространителю в виде обычного текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. [в разделе Enable encrypted connections to the ядро СУБД &#40;диспетчер конфигурации SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
#### <a name="to-create-a-push-subscription-to-a-merge-publication"></a>Создание принудительной подписки на публикацию слиянием  
  
1.  На издателе в базе данных публикации при помощи процедуры [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)проверьте, поддерживает ли публикация принудительные подписки.  
  
    -   Если значение **allow_push** равно **1**, то публикацией принудительные подписки поддерживаются.  
  
    -   Если значение **allow_push** не равно **1**, выполните [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), указав **allow_push** для **@property** и `true` для. **@value**  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql), указав следующие параметры.  
  
    -   **@publication**. Имя публикации.  
  
    -   **@subscriber_type**. Для клиентской подписки укажите **local** , а для серверной — **global**.  
  
    -   **@subscription_priority**. Для серверной подписки укажите приоритет подписки (в диапазоне от**0.00** до **99.99**).  
  
         Дополнительные сведения см. в разделе [Расширенная репликация слиянием: обнаружение и разрешение конфликтов](merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
3.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergepushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql). Укажите следующие значения.  
  
    -   Параметры **@subscriber**, **@subscriber_db**и **@publication** .  
  
    -   Учетные данные Windows, с которыми работает агент слияния на распространителе **@job_login** , **@job_password**для и.  
  
        > [!NOTE]  
        >  Соединения, выполняемые с помощью встроенной проверки подлинности Windows **@job_login** , **@job_password**всегда используют учетные данные Windows, указанные в и. Агент слияния всегда создает локальные соединения с распространителем через встроенную систему проверки подлинности Windows. По умолчанию агент подключается к подписчику через встроенную систему проверки подлинности Windows;  
  
    -   (необязательно) Значение **0** в **@subscriber_security_mode** и сведения об имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в параметрах **@subscriber_login** и значение **@subscriber_password**. Эти параметры указываются в том случае, если при соединении с подписчиком необходимо использовать проверку подлинности SQL Server.  
  
    -   (необязательно) Значение **0** в **@publisher_security_mode** и сведения об имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в параметрах **@publisher_login** и значение **@publisher_password**. Эти параметры указываются в том случае, если при соединении с издателем необходимо использовать проверку подлинности SQL Server.  
  
    -   Расписание агента слияния для данной подписки. Дополнительные сведения см. в разделе [Указание расписаний синхронизации](specify-synchronization-schedules.md).  
  
    > [!IMPORTANT]  
    >  При создании принудительной подписки на издателе с удаленным распространителем значения, указываемые для всех параметров, включая *job_login* и *job_password*, передаются распространителю в виде обычного текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. [в разделе Enable encrypted connections to the ядро СУБД &#40;диспетчер конфигурации SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
###  <a name="TsqlExample"></a>Примеры (Transact-SQL)  
 В следующем примере создается принудительная подписка на публикацию транзакций. Значения для имени входа и пароля передаются во время выполнения в переменных скрипта **sqlcmd** .  
  
 [!code-sql[HowTo#sp_addtranpushsubscription_agent](../../snippets/tsql/SQL15/replication/howto/tsql/createtranpushsub.sql#sp_addtranpushsubscription_agent)]  
  
 В следующем примере создается принудительная подписка на публикацию слиянием. Значения для имени входа и пароля передаются во время выполнения в переменных скрипта **sqlcmd** .  
  
 [!code-sql[HowTo#sp_addmergepushsubscriptionagent](../../snippets/tsql/SQL15/replication/howto/tsql/createmergepushsub.sql#sp_addmergepushsubscriptionagent)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Принудительные подписки можно создавать программно с помощью объектов RMO. Конкретные классы объектов RMO, используемые для этого, зависят от типа публикации, для которой создается подписка.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если необходимо хранить учетные данные, используйте [службы шифрования](https://go.microsoft.com/fwlink/?LinkId=34733) , предоставляемые платформой [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
#### <a name="to-create-a-push-subscription-to-a-snapshot-or-transactional-publication"></a>Создание принудительной подписки на публикацию моментальных снимков или транзакций  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  На основе соединения с издателем, созданного на шаге 1, создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransPublication> . Задайте свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>и <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает значение `false`, то на шаге 2 свойствам были присвоены неверные значения, или публикация на сервере не существует.  
  
4.  Выполните операцию «поразрядное логическое И» (`&` в Visual C# и `And` в Visual Basic) над свойством <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> и флагом <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. Если результат равен <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, присвойте свойству <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> результат операции «поразрядное логическое ИЛИ» (`|` в Visual C# и `Or` в Visual Basic) над свойством <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> и флагом <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. Затем вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> , чтобы включить принудительные подписки.  
  
5.  Если база данных подписки не существует, создайте ее с помощью класса <xref:Microsoft.SqlServer.Management.Smo.Database> . Дополнительные сведения см. в разделе [Создание, изменение и удаление баз данных](../server-management-objects-smo/tasks/creating-altering-and-removing-databases.md).  
  
6.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransSubscription>.  
  
7.  Укажите следующие свойства подписки:  
  
    -   соединение ( <xref:Microsoft.SqlServer.Management.Common.ServerConnection> ) с издателем, созданное на шаге 1, в свойстве <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>;  
  
    -   имя базы данных подписки в свойстве <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>;  
  
    -   имя подписчика в свойстве <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>;  
  
    -   имя базы данных публикации в свойстве <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>;  
  
    -   имя публикации в свойстве <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>;  
  
    -   данные учетной записи пользователя <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> Windows, от имени которого на распространителе будет запущен агент распространителя, в свойствах <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A>, <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> или <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> объекта [!INCLUDE[msCoName](../../includes/msconame-md.md)]. Эта учетная запись будет использоваться для создания локальных соединений с распространителем и удаленных с использованием проверки подлинности Windows.  
  
        > [!NOTE]  
        >  Указывать свойство <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> необязательно, если подписка создается членом предопределенной роли сервера `sysadmin`, однако рекомендуется это сделать. В этом случае агент будет выполнять олицетворение учетную запись агента SQL Server. Дополнительные сведения см. в разделе [модель безопасности агента репликации](security/replication-agent-security-model.md).  
  
    -   (необязательно) значение `true` в свойстве <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A> (задано по умолчанию). Если будет присвоено значение `false`, подписку можно будет синхронизировать только программно.  
  
    -   (необязательно) при соединении с подписчиком с проверкой подлинности SQL Server укажите значения свойств <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> и <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> или <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> объекта <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> .  
  
8.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> .  
  
    > [!IMPORTANT]  
    >  При создании принудительной подписки на издателе с удаленным распространителем значения, заданные для всех свойств, включая <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A>, отправляются распространителю в виде обычного текста. Перед вызовом метода <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> следует зашифровать подключение между издателем и его удаленным распространителем. Дополнительные сведения см. [в разделе Enable encrypted connections to the ядро СУБД &#40;диспетчер конфигурации SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
#### <a name="to-create-a-push-subscription-to-a-merge-publication"></a>Создание принудительной подписки на публикацию слиянием  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  На основе соединения с издателем, созданного на шаге 1, создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePublication> . Задайте свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>и <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает значение `false`, то на шаге 2 свойствам были присвоены неверные значения, или публикация на сервере не существует.  
  
4.  Выполните операцию «поразрядное логическое И» (`&` в Visual C# и `And` в Visual Basic) над свойством <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> и флагом <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. Если результат равен <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, присвойте свойству <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> результат операции «поразрядное логическое ИЛИ» (`|` в Visual C# и `Or` в Visual Basic) над свойством <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> и флагом <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. Затем вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> , чтобы включить принудительные подписки.  
  
5.  Если база данных подписки не существует, создайте ее с помощью класса <xref:Microsoft.SqlServer.Management.Smo.Database> . Дополнительные сведения см. в разделе [Создание, изменение и удаление баз данных](../server-management-objects-smo/tasks/creating-altering-and-removing-databases.md).  
  
6.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergeSubscription>.  
  
7.  Укажите следующие свойства подписки:  
  
    -   соединение ( <xref:Microsoft.SqlServer.Management.Common.ServerConnection> ) с издателем, созданное на шаге 1, в свойстве <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>;  
  
    -   имя базы данных подписки в свойстве <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>;  
  
    -   имя подписчика в свойстве <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>;  
  
    -   имя базы данных публикации в свойстве <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>;  
  
    -   имя публикации в свойстве <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>;  
  
    -   данные учетной записи пользователя <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> Windows, от имени которого на распространителе будет запущен агент слияния, в свойствах <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A>, <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> или <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> объекта [!INCLUDE[msCoName](../../includes/msconame-md.md)]. Эта учетная запись будет использоваться для создания локальных соединений с распространителем и удаленных с использованием проверки подлинности Windows.  
  
        > [!NOTE]  
        >  Указывать свойство <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> необязательно, если подписка создается членом предопределенной роли сервера `sysadmin`, однако рекомендуется это сделать. В этом случае агент будет выполнять олицетворение учетную запись агента SQL Server. Дополнительные сведения см. в разделе [модель безопасности агента репликации](security/replication-agent-security-model.md).  
  
    -   (необязательно) значение `true` в свойстве <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A> (задано по умолчанию). Если будет присвоено значение `false`, подписку можно будет синхронизировать только программно.  
  
    -   (необязательно) при соединении с подписчиком с проверкой подлинности SQL Server укажите значения свойств <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> и <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> или <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> объекта <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> .  
  
    -   (необязательно) при соединении с издателем с проверкой подлинности SQL Server укажите значения свойств <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> и <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> или <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> объекта <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherSecurity%2A> .  
  
8.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> .  
  
    > [!IMPORTANT]  
    >  При создании принудительной подписки на издателе с удаленным распространителем значения, заданные для всех свойств, включая <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A>, отправляются распространителю в виде обычного текста. Перед вызовом метода <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> следует зашифровать подключение между издателем и его удаленным распространителем. Дополнительные сведения см. [в разделе Enable encrypted connections to the ядро СУБД &#40;диспетчер конфигурации SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
###  <a name="PShellExample"></a>Примеры (объекты RMO)  
 В следующем примере создается принудительная подписка на публикацию транзакций. Данные учетной записи Windows для задания агента распространителя предоставляются во время выполнения.  
  
 [!code-csharp[HowTo#rmo_CreateTranPushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createtranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranPushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createtranpushsub)]  
  
 В следующем примере создается принудительная подписка на публикацию слиянием. Данные учетной записи Windows для задания агента слияния предоставляются во время выполнения.  
  
 [!code-csharp[HowTo#rmo_CreateMergePushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergepushsub)]  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение свойств принудительной подписки](view-and-modify-push-subscription-properties.md)   
 [Рекомендации по обеспечению безопасности репликации](security/replication-security-best-practices.md)   
 [Create a Publication](publish/create-a-publication.md)   
 [Основные понятия объекты Replication Management Objects](concepts/replication-management-objects-concepts.md)   
 [Синхронизация принудительной подписки](synchronize-a-push-subscription.md)   
 [Подписка на публикации](subscribe-to-publications.md)   
 [Использование программы sqlcmd с переменными скрипта](../scripting/sqlcmd-use-with-scripting-variables.md)  
  
  
