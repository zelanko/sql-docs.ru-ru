---
title: Создание публикации | Документация Майкрософт
description: Сведения о том, как создать публикацию в SQL Server с помощью SQL Server Management Studio, Transact-SQL или объектов Replication Management Objects.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publications [SQL Server replication], creating
- articles [SQL Server replication], defining
- adding articles
- articles [SQL Server replication], adding
ms.assetid: 52ee6de9-1d58-4cb9-8711-372bddbe7154
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 7c3c7ec81176b4124a78322cc5601ac8f049ca34
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86922830"
---
# <a name="create-a-publication"></a>Create a Publication
[!INCLUDE[sql-asdbmi](../../../includes/applies-to-version/sql-asdbmi.md)]
  В данном разделе описывается процесс создания публикации в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]или объектов RMO.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Для создания публикации и определения статей используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Названия публикаций и статей не могут содержать следующие символы: %, \*, [ , ], |, :, ", ? , ' , \ , / , < , >. Если объекты в базе данных, содержащие любые из этих символов, нужно реплицировать, то в диалоговом окне **\<Article>Свойства статьи —** , которое доступно на странице **Статьи** мастера, нужно задать имя статьи, отличающееся от имени объекта.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
 По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если необходимо хранить учетные данные, используйте [службы шифрования](https://go.microsoft.com/fwlink/?LinkId=34733) , предоставляемые платформой [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows .NET Framework.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Создание публикаций и определение статей осуществляется с помощью мастера создания публикаций. После создания публикации ее свойства можно просмотреть и изменить в диалоговом окне **Свойства публикации — \<Publication>** . Дополнительные сведения о создании публикаций из базы данных Oracle вы найдете в [этой статье](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
#### <a name="to-create-a-publication-and-define-articles"></a>Создание публикации и определение статей  
  
1.  Подключитесь к издателю в среде [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем щелкните правой кнопкой мыши папку **Локальные публикации** .  
  
3.  Щелкните **Создать публикацию**.  
  
4.  Следуйте указаниям на страницах мастера создания публикаций, чтобы:  
  
    -   задать распространитель, если распространение не было настроено на сервере. Дополнительные сведения о настройке распространения см. в статье [Настройка публикации и распространения](../../../relational-databases/replication/configure-publishing-and-distribution.md).  
  
         Если на странице **Распространитель** вы задаете, что сервер издателя буде функционировать как свой собственный распространитель (локальный распространитель), а сервер не настроен в качестве распространителя, то мастер создания публикаций произведет настройку сервера. Нужно будет задать для распространителя папку моментальных снимков по умолчанию на странице **Папка моментальных снимков** . Папка моментальных снимков — это просто каталог, назначенный для совместного использования; агенты, считывающие и записывающие данные в эту папку, должны иметь достаточные разрешения для доступа к ней. Дополнительные сведения о надлежащей защите папок см. в статье [Организация безопасности папки моментальных снимков](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
         Если задано, что в качестве распространителя будет функционировать другой сервер, необходимо ввести пароль на странице **Административный пароль** для соединений, устанавливаемых между издателем и распространителем. Пароль должен совпадать с паролем, указанным при включении издателя на удаленном распространителе.  
  
         Дополнительные сведения см. в разделе [Configure Distribution](../../../relational-databases/replication/configure-distribution.md).  
  
    -   Выберите базу данных публикации.  
  
    -   Выберите тип публикации. Дополнительные сведения см. в статье [Типы репликации](../../../relational-databases/replication/types-of-replication.md).  
  
    -   Задайте данные и объекты базы данных для публикации. При необходимости отфильтруйте столбцы из статей таблиц и установите свойства статей.  
  
    -   Если требуется, отфильтруйте строки из статей таблиц. Дополнительные сведения см. в статье [Фильтрация опубликованных данных](../../../relational-databases/replication/publish/filter-published-data.md).  
  
    -   Настройте расписание для агента моментальных снимков.  
  
    -   Задайте учетные данные, под которыми следующие агенты репликации будут запускаться и устанавливать соединения:  
  
         — агент моментальных снимков для всех публикаций;  
  
         — агент чтения журнала для всех публикаций транзакций;  
  
         — агент чтения очереди для публикаций транзакций, допускающих обновление подписок.  
  
         Дополнительные сведения см. в разделах [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md) и [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md).  
  
    -   При необходимости создайте скрипт для публикации. Дополнительные сведения см. в разделе [Scripting Replication](../../../relational-databases/replication/scripting-replication.md).  
  
    -   Задайте имя для публикации.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 Создание публикации может быть произведено программным путем с помощью хранимых процедур репликации. Какие именно хранимые процедуры должны для этого применяться, зависит от типа создаваемой публикации.  
  
#### <a name="to-create-a-snapshot-or-transactional-publication"></a>Создание публикации транзакций или моментальных снимков  
  
1.  Чтобы активировать публикацию текущей базы данных в репликации моментальных снимков или транзакций, в базе данных публикации на издателе выполните хранимую процедуру [sp_replicationdboption (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md).  
  
2.  Для публикации транзакций необходимо выяснить наличие задания агента чтения журнала для базы данных публикации (этот шаг необязателен для публикаций моментальных снимков).  
  
    -   Если задание агента чтения журнала для указанной базы данных публикации уже существует, перейдите к шагу 3.  
  
    -   Если неизвестно, существует ли задание агента чтения журнала для публикуемой базы данных, выполните процедуру [sp_helplogreader_agent (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) на издателе в базе данных издателя.  
  
    -   Если результирующий набор пуст, необходимо создать задание агента чтения журнала. На издателе выполните процедуру [sp_addlogreader_agent (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md). Укажите в параметрах **\@job_name** и **\@password** учетные данные [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, с которыми работает агент. Если агент будет использовать проверку подлинности SQL Server для подключения к издателю, также необходимо указать значение **0** в параметре **\@publisher_security_mode** и данные входа [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в параметрах **\@publisher_login** и **\@publisher_password**. Перейдите к шагу 3.  
  
3.  На издателе выполните процедуру [sp_addpublication (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md). Задайте имя публикации в параметре **\@publication**, а в параметре **\@repl_freq** задайте значение **snapshot** для публикации моментальных снимков или **continuous** для публикации транзакций. Укажите все остальные параметры публикации. Таким образом будет определена публикация.  
  
    > [!NOTE]  
    >  Имена публикаций не могут содержать следующие символы:  
    >   
    >  % * [ ] | : " ? \ / < >  
  
4.  На издателе выполните процедуру [sp_addpublication_snapshot (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Укажите имя публикации, использовавшееся в шаге 3, в параметре **\@publication**, а учетные данные Windows, с которыми работает агент моментальных снимков, — в параметрах **\@snapshot_job_name** и **\@password**. Если агент будет использовать проверку подлинности SQL Server для подключения к издателю, также необходимо указать значение **0** в параметре **\@publisher_security_mode** и данные входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в параметрах **\@publisher_login** и **\@publisher_password**. Будет создано задание агента моментальных снимков для публикации.  
  
    > [!IMPORTANT]  
    >  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
5.  Добавьте статьи к публикации. Дополнительные сведения см. в статье [определить статью](../../../relational-databases/replication/publish/define-an-article.md).  
  
6.  Запустите задание агента моментальных снимков, чтобы создать исходный моментальный снимок для этой публикации. Дополнительные сведения см. в разделе [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
#### <a name="to-create-a-merge-publication"></a>Создание публикации слиянием  
  
1.  Чтобы активировать публикацию текущей базы в репликации слиянием, на издателе выполните хранимую процедуру [sp_replicationdboption (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md).  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergepublication (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Укажите имя публикации в параметре **\@publication**, а также все остальные параметры публикации. Таким образом будет определена публикация.  
  
    > [!NOTE]  
    >  Имена публикаций не могут содержать следующие символы:  
    >   
    >  % * [ ] | : " ? \ / < >  
  
3.  На издателе выполните процедуру [sp_addpublication_snapshot (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Укажите имя публикации, использовавшееся в шаге 2, в параметре **\@publication**, а учетные данные Windows, с которыми работает агент моментальных снимков, — в параметрах **\@snapshot_job_name** и **\@password**. Если агент будет использовать проверку подлинности SQL Server для подключения к издателю, также необходимо указать значение **0** в параметре **\@publisher_security_mode** и данные входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в параметрах **\@publisher_login** и **\@publisher_password**. Будет создано задание агента моментальных снимков для публикации.  
  
    > [!IMPORTANT]  
    >  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
4.  Добавьте статьи к публикации. Дополнительные сведения см. в статье [определить статью](../../../relational-databases/replication/publish/define-an-article.md).  
  
5.  Запустите задание агента моментальных снимков, чтобы создать исходный моментальный снимок для этой публикации. Дополнительные сведения см. в разделе [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере производится создание публикации транзакций. Учетные данные Windows, необходимые для создания задания агента моментальных снимков и агента чтения журнала, передаются через переменные скрипта.  
  
 [!code-sql[HowTo#sp_AddTranPub](../../../relational-databases/replication/codesnippet/tsql/create-a-publication_1.sql)]  
  
 В следующем примере производится создание публикации слиянием. Учетные данные Windows, необходимые для создания задания агента моментальных снимков, передаются через переменные скрипта.  
  
 [!code-sql[HowTo#sp_AddMergePub](../../../relational-databases/replication/codesnippet/tsql/create-a-publication_2.sql)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> При помощи объектов RMO  
 Публикации можно создавать программно с помощью объектов RMO. Классы RMO, с помощью которых создается публикация, зависят от типа создаваемой публикации.  
  
#### <a name="to-create-a-snapshot-or-transactional-publication"></a>Создание публикации транзакций или моментальных снимков  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> для базы данных публикации, установите в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> экземпляр соединения <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданный на шаге 1, и вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> возвращает значение **false**, убедитесь, что база данных существует.  
  
3.  Если свойство <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing%2A> имеет значение **false**, то его следует заменить на **true**.  
  
4.  Для публикации транзакций проверьте значение свойства <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentExists%2A> . Если свойство имеет значение **true**, то задание агента чтения журнала уже есть в базе данных. Если свойство имеет значение **false**, выполните следующие действия.  
  
    -   Задайте поля <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> и <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> в <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentProcessSecurity%2A> для передачи данных учетной записи [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, под которой запущен агент чтения журнала.  
  
        > [!NOTE]  
        >  Указывать свойство <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentProcessSecurity%2A> не обязательно, если публикация создается членом предопределенной роли сервера **sysadmin** . В этом случае агент будет выполнять олицетворение учетную запись агента SQL Server. Дополнительные сведения см. в статье [Модель безопасности агента репликации](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   (необязательно) при соединении с издателем с проверкой подлинности SQL Server укажите значения свойств <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> и <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> или <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> объекта <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentPublisherSecurity%2A> .  
  
    -   С помощью метода <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.CreateLogReaderAgent%2A> создайте задание агента чтения журнала для базы данных.  
  
5.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransPublication> и укажите для него следующие свойства:  
  
    -   Соединение <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданное на шаге 1, в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   имя опубликованной базы данных в свойстве <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>;  
  
    -   имя публикации в качестве значения свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>;  
  
    -   значение <xref:Microsoft.SqlServer.Replication.PublicationType> или <xref:Microsoft.SqlServer.Replication.PublicationType.Transactional> в параметре <xref:Microsoft.SqlServer.Replication.PublicationType.Snapshot>;  
  
    -   поля <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> и <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> свойства <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> , чтобы указать учетные данные для учетной записи Windows, с которой работает агент моментальных снимков. Эта учетная запись также используется, когда агент моментальных снимков соединяется с локальным распространителем, и для любых удаленных соединений, где применяется проверка подлинности Windows;  
  
        > [!NOTE]  
        >  Указывать свойство <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> не обязательно, если публикация создается членом предопределенной роли сервера **sysadmin** . В этом случае агент будет выполнять олицетворение учетную запись агента SQL Server. Дополнительные сведения см. в статье [Модель безопасности агента репликации](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   Поля <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> и <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> или <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> в <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentPublisherSecurity%2A> при соединении с издателем с использованием проверки подлинности SQL Server (необязательно).  
  
    -   С помощью операторов включающего логического ИЛИ ( **|** в Visual C# и **Or** в Visual Basic) и исключающего логического ИЛИ ( **^** в Visual C# и **Xor** в Visual Basic) задайте значение <xref:Microsoft.SqlServer.Replication.PublicationAttributes> для свойства <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> .  
  
    -   Имя издателя в качестве значения <xref:Microsoft.SqlServer.Replication.TransPublication.PublisherName%2A> , если издатель не является издателем SQL Server (необязательно).  
  
6.  Чтобы создать публикацию, вызовите метод <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> .  
  
    > [!IMPORTANT]  
    >  При настройке издателя с удаленным распространителем значения, передаваемые для всех свойств, включая <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A>, отправляются распространителю в виде обычного текста. Перед вызовом метода <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> следует зашифровать подключение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
7.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> , чтобы создать задание агента моментальных снимков для публикации.  
  
#### <a name="to-create-a-merge-publication"></a>Создание публикации слиянием  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> для базы данных публикации, установите в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> экземпляр соединения <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданный на шаге 1, и вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> возвращает значение **false**, убедитесь, что база данных существует.  
  
3.  Если метод <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> Property is **false**, то его следует заменить на **true**и вызвать метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>.  
  
4.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePublication> и укажите для него следующие свойства:  
  
    -   Соединение <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданное на шаге 1, в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   имя опубликованной базы данных в свойстве <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>;  
  
    -   имя публикации в качестве значения свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>;  
  
    -   поля <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> и <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> свойства <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> , чтобы указать учетные данные для учетной записи Windows, с которой работает агент моментальных снимков. Эта учетная запись также используется, когда агент моментальных снимков соединяется с локальным распространителем, и для любых удаленных соединений, где применяется проверка подлинности Windows;  
  
        > [!NOTE]  
        >  Указывать свойство <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> не обязательно, если публикация создается членом предопределенной роли сервера **sysadmin** . Дополнительные сведения см. в статье [Модель безопасности агента репликации](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   С помощью операторов включающего логического ИЛИ ( **|** в Visual C# и **Or** в Visual Basic) и исключающего логического ИЛИ ( **^** в Visual C# и **Xor** в Visual Basic) задайте значение <xref:Microsoft.SqlServer.Replication.PublicationAttributes> для свойства <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> .  
  
5.  Чтобы создать публикацию, вызовите метод <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> .  
  
    > [!IMPORTANT]  
    >  При настройке издателя с удаленным распространителем значения, передаваемые для всех свойств, включая <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A>, отправляются распространителю в виде обычного текста. Перед вызовом метода <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> следует зашифровать подключение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
6.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> , чтобы создать задание агента моментальных снимков для публикации.  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> Примеры (объекты RMO)  
 В этом примере в базе данных AdventureWorks разрешается публикация транзакций, определяется задание агента чтения журнала и создается публикация AdvWorksProductTran. Для этой публикации необходимо определить статью. Данные учетной записи Windows, необходимые для создания задания агента чтения журнала и задания агента моментальных снимков, передаются во время выполнения. Более подробные сведения по определению статей моментальных снимков и транзакций с помощью объектов RMO см. в разделе [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
 [!code-cs[HowTo#rmo_CreateTranPub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createtranpub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranPub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createtranpub)]  
  
 В этом примере в базе данных AdventureWorks разрешается публикация слиянием и создается публикация AdvWorksSalesOrdersMerge. Для этой публикации все равно необходимо определить статьи. Данные учетной записи Windows, необходимые для создания задания агента моментальных снимков, предоставляются во время выполнения. Более подробные сведения по определению статей публикацией слиянием с помощью объектов RMO см. в разделе [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
 [!code-cs[HowTo#rmo_CreateMergePub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepub)]  
  
## <a name="see-also"></a>См. также:  
 [Использование программы sqlcmd с переменными скрипта](../../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)   
 [Публикация данных и объектов базы данных](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Replication Management Objects Concepts](../../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)   
 [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Настройка распространения](../../../relational-databases/replication/configure-distribution.md)   
 [Организация безопасности распространителя](../../../relational-databases/replication/security/secure-the-distributor.md)   
 [Защита издателя](../../../relational-databases/replication/security/secure-the-publisher.md)  
  
  
