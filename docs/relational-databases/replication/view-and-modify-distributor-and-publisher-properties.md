---
title: "Просмотр и изменение свойств издателя и распространителя | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- viewing replication properties
- Distributors [SQL Server replication], modifying
- modifying replication properties, Distributors
- Distributors [SQL Server replication], properties
ms.assetid: 5dae1d59-c377-4c6e-adc9-b68c5b328f79
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b0c9adb0d7fa110c08f280706d17706f4af07b07
ms.lasthandoff: 04/11/2017

---
# <a name="view-and-modify-distributor-and-publisher-properties"></a>Просмотр и изменение свойств издателя и распространителя
  В данном разделе описывается просмотр и изменение свойств распространителя и издателя в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или объектов RMO.  
  
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
  
#### <a name="to-view-and-modify-distributor-properties"></a>Просмотр и изменение свойств распространителя  
  
1.  Подключитесь к распространителю в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]и разверните узел сервера.  
  
2.  Щелкните правой кнопкой папку **Репликация** , затем щелкните **Свойства распространителя**.  
  
3.  Просматривайте и изменяйте свойства в диалоговом окне **Свойства распространителя — <\<Распространитель>**.  
  
    -   Для просмотра и изменения свойств базы данных распространителя нажмите кнопку с многоточием (**...**) базы данных на вкладке **Общие** диалогового окна.  
  
    -   Для просмотра и изменения свойств издателя, связанного с распространителем, нажмите кнопку с многоточием (**...**) издателя на вкладке **Издатели** диалогового окна.  
  
    -   Для доступа к профилям агентов репликации нажмите кнопку **Значения по умолчанию для профилей** на странице **Общие** диалогового окна. Дополнительные сведения см. в разделе [Replication Agent Profiles](../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
    -   Для изменения пароля учетной записи, используемой при выполнении административных хранимых процедур на издателе и обновлении данных на распространителе, введите новый пароль в поля **Пароль** и **Подтверждение пароля** на странице **Издатели** диалогового окна. Дополнительные сведения см. в разделе [Организация безопасности распространителя](../../relational-databases/replication/security/secure-the-distributor.md).  
  
4.  Измените свойства, если необходимо, и нажмите кнопку **ОК**.  
  
#### <a name="to-view-and-modify-publisher-properties"></a>Просмотр и изменение свойств издателя  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Правой кнопкой мыши щелкните папку **Репликация** , а затем выберите пункт **Свойства издателя**.  
  
3.  Просматривайте и изменяйте свойства в диалоговом окне **Свойства издателя — <Издатель>**.  
  
    -   Пользователь, являющийся членом предопределенной роли сервера **sysadmin** , может разрешить применение репликации для баз данных, выполнив настройки на странице **Базы данных публикации** . Разрешение репликации для базы данных не вызывает ее публикации. Вместо этого оно позволяет любому пользователю, принадлежащему к предопределенной роли базы данных **db_owner** для этой базы данных, создавать в ней одну или несколько публикаций.  
  
4.  Измените свойства, если необходимо, и нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Свойства издателя и распространителя можно просмотреть программно с помощью хранимых процедур репликации.  
  
#### <a name="to-view-distributor-and-distribution-database-properties"></a>Просмотр свойств распространителя и базы данных распространителя  
  
1.  Выполните хранимую процедуру [sp_helpdistributor](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md) , которая возвращает сведения о распространителе, базе данных распространителя и рабочем каталоге.  
  
2.  Выполните хранимую процедуру [sp_helpdistributiondb](../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md) , которая возвращает свойства заданной базы данных распространителя.  
  
#### <a name="to-change-distributor-and-distribution-database-properties"></a>Изменение свойств распространителя и базы данных распространителя  
  
1.  Чтобы изменить свойства распространителя, выполните на распространителе хранимую процедуру [sp_changedistributor_property](../../relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql.md) .  
  
2.  Чтобы изменить свойства базы данных распространителя, выполните на распространителе хранимую процедуру [sp_changedistributiondb](../../relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql.md) .  
  
3.  Чтобы изменить пароль распространителя, выполните на распространителе хранимую процедуру [sp_changedistributor_password](../../relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql.md) .  
  
    > [!IMPORTANT]  
    >  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если нужно хранить учетные данные в файле скрипта, для этого файла необходимо обеспечить защиту, чтобы исключить несанкционированный доступ.  
  
4.  Чтобы изменить свойства издателя с помощью распространителя, выполните на распространителе хранимую процедуру [sp_changedistpublisher](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md) .  
  
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
  
#### <a name="to-view-and-modify-distributor-properties"></a>Просмотр и изменение свойств распространителя  
  
1.  Установите соединение с распространителем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection>.  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.ReplicationServer>. Передайте объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection>, созданный на шаге 1.  
  
3.  (Необязательно.) Проверьте свойство <xref:Microsoft.SqlServer.Replication.ReplicationServer.IsDistributor%2A>, чтобы убедиться, что подключенный в настоящее время сервер является распространителем.  
  
4.  Чтобы получить свойства с сервера, необходимо вызвать метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A>.  
  
5.  (Необязательно.) Чтобы изменить свойства, укажите новое значение для одного или нескольких свойств распространителя, которые могут принимать значение <xref:Microsoft.SqlServer.Replication.ReplicationServer>.  
  
6.  (Необязательно.) Если свойство <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> объекта <xref:Microsoft.SqlServer.Replication.ReplicationServer> имеет значение **true**, для фиксирования изменений на сервере необходимо вызвать метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>.  
  
#### <a name="to-view-and-modify-distribution-database-properties"></a>Просмотр и изменение свойств базы данных-распространителя  
  
1.  Установите соединение с распространителем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection>.  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.DistributionDatabase>. Укажите имя и передайте объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection>, созданный на шаге 1.  
  
3.  Чтобы получить свойства с сервера, необходимо вызвать метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A>. Если этот метод вернет значение **false**, значит, на сервере не существует базы данных с указанным именем.  
  
4.  (Необязательно.) Чтобы изменить свойства, установите новое значение для одного из свойств <xref:Microsoft.SqlServer.Replication.DistributionDatabase>, которое можно установить.  
  
5.  (Необязательно.) Если свойство <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> объекта <xref:Microsoft.SqlServer.Replication.DistributionDatabase> имеет значение **true**, для фиксирования изменений на сервере необходимо вызвать метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>.  
  
#### <a name="to-view-and-modify-publisher-properties"></a>Просмотр и изменение свойств издателя  
  
1.  Установите соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection>.  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.DistributionPublisher>. Укажите свойство <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> и передайте объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1.  
  
3.  (Необязательно.) Чтобы изменить свойства, установите новое значение для одного из свойств <xref:Microsoft.SqlServer.Replication.DistributionPublisher>, которое можно установить.  
  
4.  (Необязательно.) Если свойство <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> объекта <xref:Microsoft.SqlServer.Replication.DistributionPublisher> имеет значение **true**, для фиксирования изменений на сервере необходимо вызвать метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>.  
  
#### <a name="to-change-the-password-for-the-administrative-connection-from-the-publisher-to-the-distributor"></a>Изменение пароля для административного соединения между издателем и распространителем  
  
1.  Установите соединение с распространителем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection>.  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.ReplicationServer>.  
  
3.  Укажите в качестве свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> соединение, созданное на шаге 1.  
  
4.  Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A>.  
  
5.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A>. Передайте новое значение пароля в параметре *password* .  
  
    > [!IMPORTANT]  
    >  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если необходимо хранить учетные данные, используйте [службы шифрования](http://go.microsoft.com/fwlink/?LinkId=34733) , предоставляемые платформой [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
6.  (Необязательно) Выполните следующие шаги, чтобы изменить пароль на каждом удаленном издателе, использующем данный распространитель.  
  
    1.  Установите соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection>.  
  
    2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.ReplicationServer>.  
  
    3.  Укажите в качестве свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> соединение, созданное на шаге 6а.  
  
    4.  Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A>.  
  
    5.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A>. Передайте новое значение пароля из шага 5 в параметре *password* .  
  
###  <a name="PShellExample"></a> Пример (объекты RMO)  
 В этом примере показано, как изменить свойства распространителя и базы данных-распространителя.  
  
> [!IMPORTANT]  
>  Чтобы учетные данные не хранились в коде, новый пароль для распространителя указывается во время выполнения.  
  
 [!code-cs[HowTo#rmo_ChangeDistPub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changedistpub)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeDistPub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changedistpub)]  
  
## <a name="see-also"></a>См. также:  
 [Основные понятия объектов RMO](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Disable Publishing and Distribution](../../relational-databases/replication/disable-publishing-and-distribution.md)  (Отключение публикации и распространения)  
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)   
 [Replication Management Objects Concepts](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Distributor and Publisher Information Script](../../relational-databases/replication/administration/distributor-and-publisher-information-script.md)  (Скрипт вывода сведений о распространителе и издателе)  
 [Replication System Stored Procedures Concepts](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Просмотр сведений и выполнение задач для издателя (монитор репликации)](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)  
  
  

