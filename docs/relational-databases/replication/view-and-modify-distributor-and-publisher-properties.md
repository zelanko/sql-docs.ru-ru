---
title: "Просмотр и изменение свойств издателя и распространителя | Microsoft Docs"
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
  - "просмотр свойств репликации"
  - "распространители [репликация SQL Server], изменение"
  - "изменение свойств репликации, распространители"
  - "распространители [репликация SQL Server], свойства"
ms.assetid: 5dae1d59-c377-4c6e-adc9-b68c5b328f79
caps.latest.revision: 43
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 43
---
# Просмотр и изменение свойств издателя и распространителя
  В данном разделе описывается просмотр и изменение свойств распространителя и издателя в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или объектов RMO.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Для просмотра и изменения свойств распространителя и издателя используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Для издателей, которые используют версии, предшествующие [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], пользователь, являющийся членом предопределенной роли сервера **sysadmin** , может зарегистрировать подписчиков на странице **Подписчики** . Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]больше нет необходимости в явной регистрации подписчиков для репликации.  
  
###  <a name="Security"></a> Безопасность  
 По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Просмотр и изменение свойств распространителя  
  
1.  Подключитесь к распространителю в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]и разверните узел сервера.  
  
2.  Щелкните правой кнопкой мыши **репликации** папку и выберите пункт **Свойства распространителя**.  
  
3.  Просмотр и изменение свойств в **Свойства распространителя — \< распространитель>** диалоговое окно.  
  
    -   Чтобы просмотреть и изменить свойства базы данных распространителя, нажмите кнопку свойств (**...**) базы данных на **Общие** страница «thedialog».  
  
    -   Для просмотра и изменения свойств издателя, связанного с распространителем, нажмите кнопку свойств (**...**) издателя на **издателей** страницы диалогового окна.  
  
    -   Для доступа к профилям агентов репликации нажмите кнопку **Значения по умолчанию для профилей** на странице **Общие** диалогового окна. Дополнительные сведения см. в разделе [Replication Agent Profiles](../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
    -   Для изменения пароля учетной записи, используемой при выполнении административных хранимых процедур на издателе и обновлении данных на распространителе, введите новый пароль в поля **Пароль** и **Подтверждение пароля** на странице **Издатели** диалогового окна. Дополнительные сведения см. в разделе [организация безопасности распространителя](../../relational-databases/replication/security/secure-the-distributor.md).  
  
4.  Измените свойства, если необходимо, и нажмите кнопку **ОК**.  
  
#### Просмотр и изменение свойств издателя  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Щелкните правой кнопкой мыши **репликации** папку и выберите пункт **Свойства издателя**.  
  
3.  Просмотр и изменение свойств в **Свойства издателя — \< издатель >** диалоговое окно.  
  
    -   Пользователь, являющийся членом предопределенной роли сервера **sysadmin** , может разрешить применение репликации для баз данных, выполнив настройки на странице **Базы данных публикации** . Включение базы данных не ее публикации. Вместо этого оно позволяет любому пользователю **db_owner** фиксированной роли базы данных для этой базы данных создать одну или несколько публикаций в базе данных.  
  
4.  Измените свойства, если необходимо, и нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Свойства издателя и распространителя можно просмотреть программно с помощью хранимых процедур репликации.  
  
#### Просмотр свойств распространителя и базы данных распространителя  
  
1.  Выполнение [sp_helpdistributor](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md) для возврата сведений о распространителе, базы данных распространителя и рабочий каталог.  
  
2.  Выполнение [sp_helpdistributiondb](../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md) для получения свойств базы данных распространителя.  
  
#### Изменение свойств распространителя и базы данных распространителя  
  
1.  На распространителе выполните хранимую процедуру [sp_changedistributor_property](../../relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql.md) Изменить свойства распространителя.  
  
2.  На распространителе выполните хранимую процедуру [sp_changedistributiondb](../../relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql.md) Изменить свойства базы данных распространителя.  
  
3.  На распространителе выполните хранимую процедуру [sp_changedistributor_password](../../relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql.md) для изменения пароля распространителя.  
  
    > [!IMPORTANT]  
    >  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если нужно хранить учетные данные в файле скрипта, для этого файла необходимо обеспечить защиту, чтобы исключить несанкционированный доступ.  
  
4.  На распространителе выполните хранимую процедуру [sp_changedistpublisher](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md) Изменение свойств издателя, использующего распространитель.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] возвращает сведения о распространителе и базе данных распространителя.  
  
 [!code-sql[HowTo#sp_helpdistributor](../../relational-databases/replication/codesnippet/tsql/view-and-modify-distribu_1.sql)]  
  
 [!code-sql[HowTo#sp_helpdistributiondb](../../relational-databases/replication/codesnippet/tsql/view-and-modify-distribu_2.sql)]  
  
 В этом примере изменяются сроки хранения для распространителя, пароль соединения с распространителем и интервал, с которым распространитель проверяет состояние различных агентов репликации (интервал тактового импульса).  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если нужно хранить учетные данные в файле скрипта, для этого файла необходимо обеспечить защиту, чтобы исключить несанкционированный доступ.  
  
 [!code-sql[HowTo#sp_changedistributor_property](../../relational-databases/replication/codesnippet/tsql/view-and-modify-distribu_3.sql)]  
  
 [!code-sql[HowTo#sp_changedistributiondb](../../relational-databases/replication/codesnippet/tsql/view-and-modify-distribu_4.sql)]  
  
 [!code-sql[HowTo#sp_changedistributor_password](../../relational-databases/replication/codesnippet/tsql/view-and-modify-distribu_5.sql)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
  
#### Просмотр и изменение свойств распространителя  
  
1.  Создайте соединение с распространителем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.ReplicationServer> класса. Передайте <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1.  
  
3.  (Необязательно) Проверьте <xref:Microsoft.SqlServer.Replication.ReplicationServer.IsDistributor%2A> свойство, чтобы убедиться, что подключенный в настоящее время сервер является распространителем.  
  
4.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> метод для получения свойств с сервера.  
  
5.  (Необязательно) Чтобы изменить свойства, задайте новое значение для одного или нескольких свойств распространителя, которые могут быть установлены на <xref:Microsoft.SqlServer.Replication.ReplicationServer> объекта.  
  
6.  (Необязательно) Если <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> свойство <xref:Microsoft.SqlServer.Replication.ReplicationServer> имеет значение **true**, вызовите <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> метод, чтобы зафиксировать изменения на сервере.  
  
#### Просмотр и изменение свойств базы данных-распространителя  
  
1.  Создайте соединение с распространителем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.DistributionDatabase> класса. Укажите имя свойства и передайте <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод для получения свойств с сервера. Если этот метод вернет значение **false**, значит, на сервере не существует базы данных с указанным именем.  
  
4.  (Необязательно) Чтобы изменить свойства, установите новое значение для одного из <xref:Microsoft.SqlServer.Replication.DistributionDatabase> Свойства, которые могут быть установлены.  
  
5.  (Необязательно) Если <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> свойство <xref:Microsoft.SqlServer.Replication.DistributionDatabase> имеет значение **true**, вызовите <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> метод, чтобы зафиксировать изменения на сервере.  
  
#### Просмотр и изменение свойств издателя  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.DistributionPublisher> класса. Укажите <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> Свойства и передайте <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1.  
  
3.  (Необязательно) Чтобы изменить свойства, установите новое значение для одного из <xref:Microsoft.SqlServer.Replication.DistributionPublisher> Свойства, которые могут быть установлены.  
  
4.  (Необязательно) Если <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> свойство <xref:Microsoft.SqlServer.Replication.DistributionPublisher> имеет значение **true**, вызовите <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> метод, чтобы зафиксировать изменения на сервере.  
  
#### Изменение пароля для административного соединения между издателем и распространителем  
  
1.  Создайте соединение с распространителем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.ReplicationServer> класса.  
  
3.  Задайте <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства подключения, созданной на шаге 1.  
  
4.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> метод, чтобы получить свойства объекта.  
  
5.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> метод. Передайте новое значение пароля в параметре *password* .  
  
    > [!IMPORTANT]  
    >  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если необходимо хранить учетные данные, используйте [службы шифрования](http://go.microsoft.com/fwlink/?LinkId=34733) , предоставляемые платформой [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
6.  (Необязательно) Выполните следующие шаги, чтобы изменить пароль на каждом удаленном издателе, использующем данный распространитель.  
  
    1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
    2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.ReplicationServer> класса.  
  
    3.  Задайте <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства соединение, созданное в шаге 6a.  
  
    4.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> метод, чтобы получить свойства объекта.  
  
    5.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> метод. Передайте новое значение пароля из шага 5 в параметре *password* .  
  
###  <a name="PShellExample"></a> Пример (объекты RMO)  
 В этом примере показано, как изменить свойства распространителя и базы данных-распространителя.  
  
> [!IMPORTANT]  
>  Чтобы учетные данные не хранились в коде, новый пароль для распространителя указывается во время выполнения.  
  
 [!code-csharp[HowTo#rmo_ChangeDistPub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changedistpub)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeDistPub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changedistpub)]  
  
## См. также:  
 [Основные понятия объектов RMO](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Отключение публикации и распространения](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [Настройка распространителя](../../relational-databases/replication/configure-distribution.md)   
 [Основные понятия объектов RMO](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Скрипт вывода сведений о распространителе и издателе](../../relational-databases/replication/administration/distributor-and-publisher-information-script.md)   
 [Основные понятия системных хранимых процедур репликации](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Просмотр сведений и выполнение задач для издателя и #40; Монитор репликации & #41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)  
  
  