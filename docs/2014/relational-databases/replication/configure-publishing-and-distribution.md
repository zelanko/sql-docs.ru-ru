---
title: Настройка публикации и распространения | Документация Майкрософт
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], distribution
- distribution configuration [SQL Server replication]
- publishing [SQL Server replication], configuring
ms.assetid: 3cfc8966-833e-42fa-80cb-09175d1feed7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 905b1ceed2df8afc854ad38ee07d2b21596530f1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73882251"
---
# <a name="configure-publishing-and-distribution"></a>Настройка публикации и распространения
  В данном разделе описывается процесс настройки публикации и распространения в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или объектов RMO.  
  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
 Дополнительные сведения см. в разделе [безопасное развертывание репликации](security/view-and-modify-replication-security-settings.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Настройте распространение с помощью мастера создания публикаций или мастера настройки распространителя. После настройки распространителя просмотрите и измените свойства в диалоговом окне **Свойства распространителя \<— распространитель>** . Используйте мастер настройки распространителя, если требуется настроить распространитель так, чтобы члены предопределенных ролей базы данных **db_owner** могли создавать публикации, или если требуется настроить удаленный распространитель, который не является издателем.  
  
#### <a name="to-configure-distribution"></a>Настройка распространения  
  
1.  В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]подключитесь к серверу, который будет распространителем (во многих случаях издатель и распространитель являются одним и тем же сервером), а затем разверните узел сервера.  
  
2.  Щелкните правой кнопкой мыши папку **Репликация** , затем щелкните **Настройка распространения**.  
  
3.  Выполняйте инструкции мастера настройки распространителя:  
  
    -   Выберите распространитель. Чтобы использовать локальный распространитель, выберите **"\<ServerName>" будет работать как собственный распространитель. SQL Server создаст базу данных распространителя и журнал**. Для использования удаленного распространителя выберите **Использовать следующий сервер в качестве распространителя**, а затем выберите сервер. Сервер должен быть сконфигурирован в качестве распространителя, а издатель должен быть включен для использования распространителя. Дополнительные сведения см. в разделе [Включение удаленного издателя на распространителе (среда SQL Server Management Studio)](enable-a-remote-publisher-at-a-distributor-sql-server-management-studio.md).  
  
         Если выбран удаленный распространитель, необходимо ввести пароль на странице **Административный пароль** , который требуется для соединения издателя с распространителем. Пароль должен совпадать с паролем, указанным при включении издателя на удаленном распространителе.  
  
    -   Укажите корневую папку моментальных снимков (для локального распространителя). Папка моментальных снимков — это просто каталог, назначенный для совместного использования; агенты, считывающие и записывающие данные в эту папку, должны иметь достаточные разрешения для доступа к ней. Каждый издатель, использующий распространитель, создает папку в корневой папке, каждая публикация создает папки в папке «Издатель», в которой хранятся файлы моментальных снимков. Дополнительные сведения о надлежащей защите папок см. в разделе [Организация безопасности папки моментальных снимков](security/secure-the-snapshot-folder.md).  
  
    -   Укажите базу данных распространителя (для локального распространителя). В базе данных распространителя хранятся метаданные и данные журнала для всех типов репликации и транзакций, относящихся к репликации транзакций.  
  
    -   При необходимости укажите, что другие издатели могут использовать распространитель. Если другим издателям разрешено использовать распространитель, необходимо ввести пароль на странице **Пароль распространителя** , который используется для подключения этих издателей к распространителю.  
  
    -   При необходимости создайте скрипт настроек конфигурации. Дополнительные сведения см. в разделе [Scripting Replication](scripting-replication.md).  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Публикацию и распространение репликации можно настроить программно с помощью хранимых процедур репликации.  
  
#### <a name="to-configure-publishing-using-a-local-distributor"></a>Настройка публикации с помощью локального распространителя  
  
1.  Чтобы определить, настроен ли сервер в качестве распространителя, выполните процедуру, описанную в разделе [sp_get_distributor (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-get-distributor-transact-sql).  
  
    -   Если значение **installed** в результирующем наборе равно **0**, выполните процедуру [sp_adddistributor (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-adddistributor-transact-sql) на распространителе в базе данных master.  
  
    -   Если значение **distribution db installed** в результирующем наборе равно **0**, выполните процедуру [sp_adddistributiondb (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql) на распространителе в базе данных master. Укажите имя базы данных распространителя для ** \@базы данных**. При необходимости можно указать максимальный срок хранения транзакций для ** \@max_distretention** и срок хранения журнала для ** \@history_retention**. Если создается новая база данных, укажите желаемые параметры свойств.  
  
2.  На распространителе, который также является издателем, выполните [sp_adddistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql), указав общий ресурс UNC, который будет использоваться в качестве папки моментальных снимков по умолчанию для ** \@working_directory**.  
  
3.  На издателе выполните процедуру [sp_replicationdboption (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql). Укажите базу данных, публикуемую ** \@** для параметра dbname, тип репликации для ** \@optname**, а также значение `true` для ** \@параметра значение**.  
  
#### <a name="to-configure-publishing-using-a-remote-distributor"></a>Настройка публикации с помощью удаленного распространителя  
  
1.  Чтобы определить, настроен ли сервер в качестве распространителя, выполните процедуру, описанную в разделе [sp_get_distributor (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-get-distributor-transact-sql).  
  
    -   Если значение **installed** в результирующем наборе равно **0**, выполните процедуру [sp_adddistributor (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-adddistributor-transact-sql) на распространителе в базе данных master. Укажите надежный пароль для ** \@пароля**. Этот пароль для учетной записи **distributor_admin** используется издателем при соединении с распространителем.  
  
    -   Если значение **distribution db installed** в результирующем наборе равно **0**, выполните процедуру [sp_adddistributiondb (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql) на распространителе в базе данных master. Укажите имя базы данных распространителя для ** \@базы данных**. При необходимости можно указать максимальный срок хранения транзакций для ** \@max_distretention** и срок хранения журнала для ** \@history_retention**. Если создается новая база данных, укажите желаемые параметры свойств.  
  
2.  На распространителе выполните [sp_adddistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql), указав общий ресурс UNC, который будет использоваться в качестве папки моментальных снимков по умолчанию для ** \@working_directory**. Если распространитель будет использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверку подлинности при соединении с издателем, необходимо также указать значение **0** для ** \@security_mode** и [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сведения об имени входа для ** \@входа** и ** \@пароля**.  
  
3.  На издателе в базе данных master выполните процедуру [sp_adddistributor (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-adddistributor-transact-sql). Укажите надежный пароль, используемый в шаге 1 для ** \@пароля**. Этот пароль будет использоваться издателем при соединении с распространителем.  
  
4.  На издателе выполните процедуру [sp_replicationdboption (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql). Укажите базу данных, публикуемую ** \@** для параметра dbname, тип репликации для ** \@optname**и значение true для ** \@параметра значение**.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующих разделах описывается программная настройка публикации и распространения. В этом примере имя сервера, настраиваемого в качестве издателя и локального распространителя, указывается с помощью переменных скрипта. Публикацию и распространение репликации можно настроить программно с помощью хранимых процедур репликации.  
  
 [!code-sql[HowTo#AddDistPub](../../snippets/tsql/SQL15/replication/howto/tsql/adddistpub.sql#adddistpub)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
  
#### <a name="to-configure-publishing-and-distribution-on-a-single-server"></a>Настройка публикации и распространения на одиночном сервере  
  
1.  Создайте соединение с сервером с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.ReplicationServer>. Передайте объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданный на шаге 1.  
  
3.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.DistributionDatabase>.  
  
4.  Задайте для свойства <xref:Microsoft.SqlServer.Replication.DistributionDatabase.Name%2A> имя базы данных, а для свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> — значение <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1.  
  
5.  Установите распространитель, вызвав метод <xref:Microsoft.SqlServer.Replication.ReplicationServer.InstallDistributor%2A> . Передайте объект <xref:Microsoft.SqlServer.Replication.DistributionDatabase> , созданный на шаге 3.  
  
6.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.DistributionPublisher>.  
  
7.  Установите следующие свойства <xref:Microsoft.SqlServer.Replication.DistributionPublisher>.  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A>— имя издателя.  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> — соединение <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданное на шаге 1.  
  
    -   
  <xref:Microsoft.SqlServer.Replication.DistributionPublisher.DistributionDatabase%2A> — название базы данных, созданной на шаге 5.  
  
    -   
  <xref:Microsoft.SqlServer.Replication.DistributionPublisher.WorkingDirectory%2A> — общая папка, используемая для доступа к файлам моментальных снимков.  
  
    -   
  <xref:Microsoft.SqlServer.Replication.DistributionPublisher.PublisherSecurity%2A> — режим безопасности при соединении с издателем. Рекомендуется<xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> .  
  
8.  Вызовите метод <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Create%2A> .  
  
#### <a name="to-configure-publishing-and-distribution-using-a-remote-distributor"></a>Настройка публикации и распространения с использованием удаленного распространителя  
  
1.  Создайте соединение с удаленным распространителем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.ReplicationServer>. Передайте объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданный на шаге 1.  
  
3.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.DistributionDatabase>.  
  
4.  Задайте для свойства <xref:Microsoft.SqlServer.Replication.DistributionDatabase.Name%2A> имя базы данных, а для свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> — значение <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1.  
  
5.  Установите распространитель, вызвав метод <xref:Microsoft.SqlServer.Replication.ReplicationServer.InstallDistributor%2A> . Укажите безопасный пароль (используемый издателем для соединения с удаленным распространителем) и объект <xref:Microsoft.SqlServer.Replication.DistributionDatabase> из шага 3. Дополнительные сведения см. в разделе [Организация безопасности распространителя](security/secure-the-distributor.md).  
  
    > [!IMPORTANT]  
    >  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если необходимо хранить учетные данные, используйте [службы шифрования](https://go.microsoft.com/fwlink/?LinkId=34733) , предоставляемые платформой [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
6.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.DistributionPublisher>.  
  
7.  Установите следующие свойства <xref:Microsoft.SqlServer.Replication.DistributionPublisher>.  
  
    -   
  <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> — имя локального издателя.  
  
    -   
  <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> — соединение <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданное на шаге 1.  
  
    -   
  <xref:Microsoft.SqlServer.Replication.DistributionPublisher.DistributionDatabase%2A> — название базы данных, созданной на шаге 5.  
  
    -   
  <xref:Microsoft.SqlServer.Replication.DistributionPublisher.WorkingDirectory%2A> — общая папка, используемая для доступа к файлам моментальных снимков.  
  
    -   
  <xref:Microsoft.SqlServer.Replication.DistributionPublisher.PublisherSecurity%2A> — режим безопасности при соединении с издателем. Рекомендуется<xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> .  
  
8.  Вызовите метод <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Create%2A> .  
  
9. Создайте соединение с локальным издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
10. Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.ReplicationServer>. Передайте объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданный на шаге 9.  
  
11. Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationServer.InstallDistributor%2A> . Передайте имя удаленного распространителя и пароль для удаленного распространителя, указанный в шаге 5.  
  
    > [!IMPORTANT]  
    >  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если необходимо сохранить учетные данные, используйте [службы шифрования](https://go.microsoft.com/fwlink/?LinkId=34733) , предоставляемые .NET Framework Windows.  
  
###  <a name="PShellExample"></a>Пример (объекты RMO)  
 Публикацию и распространение репликации можно настраивать программно, с помощью объектов RMO.  
  
 [!code-csharp[HowTo#rmo_AddDistPub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_adddistpub)]  
  
 [!code-vb[HowTo#rmo_vb_AddDistPub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_adddistpub)]  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение свойств распространителя и издателя](view-and-modify-distributor-and-publisher-properties.md)   
 [Основные понятия системных хранимых процедур репликации](concepts/replication-system-stored-procedures-concepts.md)   
 [Настройка распространения](configure-distribution.md)   
 [Основные понятия объекты Replication Management Objects](concepts/replication-management-objects-concepts.md)   
 [Настройка репликации для группы доступности AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) 
  
  
