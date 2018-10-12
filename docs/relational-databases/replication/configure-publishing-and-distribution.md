---
title: Настройка публикации и распространения | Документация Майкрософт
ms.custom: ''
ms.date: 09/23/2018
ms.prod: sql
ms.prod_service: database-engine
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
ms.openlocfilehash: c5d302195025be0d9ab1e19ac0227e427e7b4bbc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47832092"
---
# <a name="configure-publishing-and-distribution"></a>Настройка публикации и распространения
[!INCLUDE[appliesto-ss-asdbmi-asdbmi-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
 В данном разделе описывается процесс настройки публикации и распространения в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или объектов RMO.

##  <a name="BeforeYouBegin"></a> Перед началом 

###  <a name="Security"></a> безопасность 
Дополнительные сведения см. в разделе [Безопасное развертывание (репликация)](../../relational-databases/replication/security/secure-deployment-replication.md).

##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio 
Настройте распространение с помощью мастера создания публикаций или мастера настройки распространителя. После настройки распространителя просмотрите и измените его свойства в диалоговом окне **Свойства распространителя — \<распространитель>**. Используйте мастер настройки распространителя, если необходимо настроить распространитель так, чтобы члены предопределенных ролей базы данных `db_owner` могли создавать публикации, или если необходимо настроить удаленный распространитель, который не является издателем.

#### <a name="to-configure-distribution"></a>Настройка распространения 

1. В среде [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]подключитесь к серверу, который будет выступать в роли распространителя (в большинстве случаев издатель и распространитель являются одним сервером), и разверните узел сервера.

2. Щелкните правой кнопкой мыши папку **Репликация** , затем щелкните **Настройка распространения**.

3. Выполняйте инструкции мастера настройки распространителя: 

  - Выберите распространитель. Чтобы использовать локальный распространитель, выберите имя **ServerName, которое будет выступать в качестве своего собственного распространителя. При этом SQL Server создаст базу данных распространения и журнал**. Для использования удаленного распространителя выберите **Использовать следующий сервер в качестве распространителя**, а затем выберите сервер. Сервер должен быть сконфигурирован в качестве распространителя, а издатель должен быть включен для использования распространителя. Дополнительные сведения см. в разделе [Включение удаленного издателя на распространителе (среда SQL Server Management Studio)](../../relational-databases/replication/enable-a-remote-publisher-at-a-distributor-sql-server-management-studio.md).

     Если выбран удаленный распространитель, необходимо ввести пароль на странице **Административный пароль** , который требуется для соединения издателя с распространителем. Пароль должен совпадать с паролем, указанным при включении издателя на удаленном распространителе.

  - Укажите корневую папку моментальных снимков (для локального распространителя). Папка моментальных снимков — это просто каталог, назначенный для совместного использования; агенты, считывающие и записывающие данные в эту папку, должны иметь достаточные разрешения для доступа к ней. Каждый издатель, использующий распространитель, создает папку в корневой папке, каждая публикация создает папки в папке «Издатель», в которой хранятся файлы моментальных снимков. Дополнительные сведения о надлежащей защите папок см. в разделе [Организация безопасности папки моментальных снимков](../../relational-databases/replication/security/secure-the-snapshot-folder.md).

  - Укажите базу данных распространителя (для локального распространителя). В базе данных распространителя хранятся метаданные и данные журнала для всех типов репликации и транзакций, относящихся к репликации транзакций.

  - При необходимости укажите, что другие издатели могут использовать распространитель. Если другим издателям разрешено использовать распространитель, необходимо ввести пароль на странице **Пароль распространителя** , который используется для подключения этих издателей к распространителю.

  - При необходимости создайте скрипт настроек конфигурации. Дополнительные сведения см. в статье [Scripting Replication](../../relational-databases/replication/scripting-replication.md).

##  <a name="TsqlProcedure"></a> Использование Transact-SQL 
Публикацию и распространение репликации можно настроить программно с помощью хранимых процедур репликации.
### <a name="to-configure-publishing-using-a-local-distributor"></a>Настройка публикации с помощью локального распространителя
1. Чтобы определить, настроен ли сервер в качестве распространителя, выполните процедуру, описанную в разделе [sp_get_distributor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-get-distributor-transact-sql.md).

  - Если значение `installed` в результирующем наборе равно `0`, выполните процедуру [sp_adddistributor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md) в распространителе в базе данных master.

  - Если значение `distribution db installed` в результирующем наборе равно `0`, выполните процедуру [sp_adddistributiondb (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md) в распространителе в базе данных master. Укажите имя базы данных распространителя в параметре `@database`. При необходимости можно указать максимальный срок хранения транзакции в параметре `@max_distretention` и срок хранения журнала в параметре `@history_retention`. Если создается новая база данных, укажите желаемые параметры свойств.

2. В распространителе, который также является издателем, выполните процедуру [sp_adddistpublisher (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md), указав общий ресурс UNC, который будет использоваться как папка по умолчанию для моментальных снимков, в параметре `@working_directory`.

   Для распространителя в Управляемом экземпляре Базы данных SQL укажите учетную запись хранения Azure в параметре `@working_directory` и ключ доступа к хранилищу в параметре `@storage_connection_string`. 

3. На издателе выполните процедуру [sp_replicationdboption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md). Укажите опубликованную базу данных в параметре `@dbname`, тип репликации в параметре `@optname` и значение `true` в параметре `@value`.

#### <a name="to-configure-publishing-using-a-remote-distributor"></a>Настройка публикации с помощью удаленного распространителя 

1. Чтобы определить, настроен ли сервер в качестве распространителя, выполните процедуру, описанную в разделе [sp_get_distributor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-get-distributor-transact-sql.md).

   - Если значение `installed` в результирующем наборе равно `0`, выполните процедуру [sp_adddistributor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md) в распространителе в базе данных master. Укажите надежный пароль в параметре `@password`. Этот пароль для учетной записи `distributor_admin` будет использоваться издателем при подключении к распространителю.

   - Если значение `distribution db installed` в результирующем наборе равно `0`, выполните процедуру [sp_adddistributiondb (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md) в распространителе в базе данных master. Укажите имя базы данных распространителя в параметре `@database`. При необходимости можно указать максимальный срок хранения транзакции в параметре `@max_distretention` и срок хранения журнала в параметре `@history_retention`. Если создается новая база данных, укажите желаемые параметры свойств.

2. В распространителе выполните процедуру [sp_adddistpublisher (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md), указав общий ресурс UNC, который будет использоваться как папка по умолчанию для моментальных снимков, в параметре `@working_directory`. Если распространитель будет использовать проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при подключении к издателю, то нужно также указать значение `0` в параметре `@security_mode` и данные имени входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в параметрах `@login` и `@password`.

   Для распространителя в Управляемом экземпляре Базы данных SQL укажите учетную запись хранения Azure в параметре `@working_directory` и ключ доступа к хранилищу в параметре `@storage_connection_string`. 

3. На издателе в базе данных master выполните процедуру [sp_adddistributor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md). Укажите надежный пароль из шага 1 в параметре `@password`. Этот пароль будет использоваться издателем при соединении с распространителем.

4. На издателе выполните процедуру [sp_replicationdboption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md). Укажите опубликованную базу данных в параметре `@dbname`, тип репликации в параметре `@optname` и значение true в параметре `@value`.

###  <a name="TsqlExample"></a> Примеры (Transact-SQL) 
В следующих разделах описывается программная настройка публикации и распространения. В этом примере имя сервера, настраиваемого в качестве издателя и локального распространителя, указывается с помощью переменных скрипта. Публикацию и распространение репликации можно настроить программно с помощью хранимых процедур репликации.

[!code-sql[HowTo#AddDistPub](../../relational-databases/replication/codesnippet/tsql/configure-publishing-and_1.sql)] 

##  <a name="RMOProcedure"></a> При помощи объектов RMO 

#### <a name="to-configure-publishing-and-distribution-on-a-single-server"></a>Настройка публикации и распространения на одиночном сервере 

1. Создайте соединение с сервером с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .

2. Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.ReplicationServer> . Передайте объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданный на шаге 1.

3. Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.DistributionDatabase> .

4. Задайте для свойства <xref:Microsoft.SqlServer.Replication.DistributionDatabase.Name%2A> имя базы данных, а для свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> — значение <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1.

5. Установите распространитель, вызвав метод <xref:Microsoft.SqlServer.Replication.ReplicationServer.InstallDistributor%2A> . Передайте объект <xref:Microsoft.SqlServer.Replication.DistributionDatabase> , созданный на шаге 3.

6. Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.DistributionPublisher> .

7. Установите следующие свойства <xref:Microsoft.SqlServer.Replication.DistributionPublisher>. 

  - <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> — имя издателя.

  - <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> — соединение <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданное на шаге 1.

  - <xref:Microsoft.SqlServer.Replication.DistributionPublisher.DistributionDatabase%2A> — название базы данных, созданной на шаге 5.

  - <xref:Microsoft.SqlServer.Replication.DistributionPublisher.WorkingDirectory%2A> — общая папка, используемая для доступа к файлам моментальных снимков.

  - <xref:Microsoft.SqlServer.Replication.DistributionPublisher.PublisherSecurity%2A> — режим безопасности при соединении с издателем. Рекомендуется<xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> .

8. Вызовите метод <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Create%2A> .

#### <a name="to-configure-publishing-and-distribution-using-a-remote-distributor"></a>Настройка публикации и распространения с использованием удаленного распространителя 

1. Создайте соединение с удаленным распространителем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .

2. Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.ReplicationServer> . Передайте объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданный на шаге 1.

3. Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.DistributionDatabase> .

4. Задайте для свойства <xref:Microsoft.SqlServer.Replication.DistributionDatabase.Name%2A> имя базы данных, а для свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> — значение <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1.

5. Установите распространитель, вызвав метод <xref:Microsoft.SqlServer.Replication.ReplicationServer.InstallDistributor%2A> . Укажите безопасный пароль (используемый издателем для соединения с удаленным распространителем) и объект <xref:Microsoft.SqlServer.Replication.DistributionDatabase> из шага 3. Дополнительные сведения см. в разделе [Организация безопасности распространителя](../../relational-databases/replication/security/secure-the-distributor.md).

   > `IMPORTANT!!` При возможности предлагать пользователю ввод учетных данных безопасности во время выполнения. Если необходимо хранить учетные данные, используйте [службы шифрования](http://go.microsoft.com/fwlink/?LinkId=34733) , предоставляемые платформой [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.

6. Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.DistributionPublisher> .

7. Установите следующие свойства <xref:Microsoft.SqlServer.Replication.DistributionPublisher>. 

  - <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> — имя локального издателя.

  - <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> — соединение <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданное на шаге 1.

  - <xref:Microsoft.SqlServer.Replication.DistributionPublisher.DistributionDatabase%2A> — название базы данных, созданной на шаге 5.

  - <xref:Microsoft.SqlServer.Replication.DistributionPublisher.WorkingDirectory%2A> — общая папка, используемая для доступа к файлам моментальных снимков.

  - <xref:Microsoft.SqlServer.Replication.DistributionPublisher.PublisherSecurity%2A> — режим безопасности при соединении с издателем. Рекомендуется<xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> .

8. Вызовите метод <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Create%2A> .

9. Создайте соединение с локальным издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .

10. Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.ReplicationServer> . Передайте объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданный на шаге 9.

11. Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationServer.InstallDistributor%2A> . Передайте имя удаленного распространителя и пароль для удаленного распространителя, указанный в шаге 5.

>[!IMPORTANT]
По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если необходимо хранить учетные данные, используйте [службы шифрования](http://go.microsoft.com/fwlink/?LinkId=34733) , предоставляемые платформой Windows .NET Framework.

###  <a name="PShellExample"></a> Пример (объекты RMO) 
Публикацию и распространение репликации можно настраивать программно, с помощью объектов RMO.

[!code-cs[HowTo#rmo_AddDistPub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_adddistpub)] 

[!code-vb[HowTo#rmo_vb_AddDistPub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_adddistpub)] 

## <a name="see-also"></a>См. также: 
[Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
[Replication System Stored Procedures Concepts](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
[Настройка распространения](../../relational-databases/replication/configure-distribution.md)  
[Основные понятия объектов RMO](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)  
[Настройка репликации для групп доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/configure-replication-for-always-on-availability-groups-sql-server.md) 


