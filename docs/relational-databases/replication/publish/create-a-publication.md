---
title: "Создание публикации | Microsoft Docs"
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
  - "публикации [репликация SQL Server], создание"
  - "статьи [репликация SQL Server], определение"
  - "добавление статей"
  - "статьи [репликация SQL Server], добавление"
ms.assetid: 52ee6de9-1d58-4cb9-8711-372bddbe7154
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Создание публикации
  В данном разделе описывается процесс создания публикации в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] или объектов RMO.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Для создания публикации и определения статей используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Названия публикаций и статей не могут содержать следующие символы: %, \* , [,], |,:, «,? , ' , \ , / , \< , >. Если объекты в базе данных включают следующие символы и требуется реплицировать их, необходимо указать имя статьи, отличающееся от имени объекта в **Свойства статьи — \< статья>** диалоговое окно доступно из **статьи** в мастере.  
  
###  <a name="Security"></a> Безопасность  
 По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если необходимо хранить учетные данные, используйте [службы шифрования](http://go.microsoft.com/fwlink/?LinkId=34733) , предоставляемые платформой [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows .NET Framework.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Создание публикаций и определение статей осуществляется с помощью мастера создания публикаций. После создания публикации, просмотр и изменение свойств публикации в **Свойства публикации — \< публикация>** диалоговое окно. Сведения о создании публикации из базы данных Oracle см. в разделе [Создание публикации из базы данных Oracle](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
#### Создание публикации и определение статей  
  
1.  Подключитесь к издателю в среде [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]и раскройте узел сервера.  
  
2.  Разверните **репликации** папки затем щелкните правой кнопкой **Локальные публикации** папки.  
  
3.  Щелкните **Создать публикацию**.  
  
4.  Следуйте указаниям на страницах мастера создания публикаций, чтобы:  
  
    -   задать распространитель, если распространение не было настроено на сервере. Дополнительные сведения о настройке распространения см. в разделе [настройки публикации и распространения](../../../relational-databases/replication/configure-publishing-and-distribution.md).  
  
         При указании на **распространитель** страницы, что сервер издателя буде функционировать как свой собственный распространитель (локальный распространитель), а сервер не настроен как распространитель, мастера создания публикаций произведет настройку сервера. Нужно будет задать для распространителя папку моментальных снимков по умолчанию на странице **Папка моментальных снимков** . Папка моментальных снимков — это просто каталог, назначенный для совместного использования; агенты, считывающие и записывающие данные в эту папку, должны иметь достаточные разрешения для доступа к ней. Дополнительные сведения о соответствующей защите папок см. в разделе [Безопасность папки моментальных снимков](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
         Если задано, что в качестве распространителя будет функционировать другой сервер, необходимо ввести пароль на странице **Административный пароль** для соединений, устанавливаемых между издателем и распространителем. Пароль должен совпадать с паролем, указанным при включении издателя на удаленном распространителе.  
  
         Дополнительные сведения см. в разделе [Настройка распространения](../../../relational-databases/replication/configure-distribution.md).  
  
    -   Выберите базу данных публикации.  
  
    -   Выберите тип публикации. Дополнительные сведения см. в разделе [типы репликации](../../../relational-databases/replication/types-of-replication.md).  
  
    -   Задайте данные и объекты базы данных для публикации. При необходимости отфильтруйте столбцы из статей таблиц и установите свойства статей.  
  
    -   Если требуется, отфильтруйте строки из статей таблиц. Дополнительные сведения см. в разделе [Фильтрация опубликованных данных](../../../relational-databases/replication/publish/filter-published-data.md).  
  
    -   Настройте расписание для агента моментальных снимков.  
  
    -   Задайте учетные данные, под которыми следующие агенты репликации будут запускаться и устанавливать соединения:  
  
         \- Агент моментальных снимков для всех публикаций.  
  
         \- Агент чтения журнала для всех публикаций транзакций.  
  
         \- Агент чтения очереди для публикаций транзакций, допускающих обновляемые подписки.  
  
         Дополнительные сведения см. в разделах [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md) и [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md).  
  
    -   При необходимости создайте скрипт для публикации. Дополнительные сведения см. в разделе [Scripting Replication](../../../relational-databases/replication/scripting-replication.md).  
  
    -   Задайте имя для публикации.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Создание публикации может быть произведено программным путем с помощью хранимых процедур репликации. Какие именно хранимые процедуры должны для этого применяться, зависит от типа создаваемой публикации.  
  
#### Создание публикации транзакций или моментальных снимков  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_replicationdboption & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) Чтобы активировать публикацию текущей базы данных с помощью моментальных снимков или репликации транзакций.  
  
2.  Для публикации транзакций необходимо выяснить наличие задания агента чтения журнала для базы данных публикации (этот шаг необязателен для публикаций моментальных снимков).  
  
    -   Если задание агента чтения журнала для указанной базы данных публикации уже существует, перейдите к шагу 3.  
  
    -   Если вы не знаете, существует ли задание агента чтения журнала для опубликованной базы данных, выполнение [sp_helplogreader_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) на издателе в базе данных публикации.  
  
    -   Если результирующий набор пуст, необходимо создать задание агента чтения журнала. На издателе, хранимую [sp_addlogreader_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md). Укажите [!INCLUDE[msCoName](../../../includes/msconame-md.md)] учетные данные Windows, под которыми работает агент **@job_name** и **@password**. Если агент будет использовать проверку подлинности SQL Server при подключении к издателю, необходимо также указать значение **0** для **@publisher_security_mode** и [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сведения об имени входа **@publisher_login** и **@publisher_password**. Перейдите к шагу 3.  
  
3.  На издателе, хранимую [sp_addpublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md). Укажите имя публикации для **@publication**, и для **@repl_freq** параметр, задайте значение **моментального снимка** для публикации моментальных снимков или значение **непрерывного** для публикации транзакций. Укажите все остальные параметры публикации. Таким образом будет определена публикация.  
  
    > [!NOTE]  
    >  Имена публикаций не могут содержать следующие символы:  
    >   
    >  % * [ ] | : " ? \ / \< >  
  
4.  На издателе, хранимую [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Укажите имя публикации, использовавшееся на шаге 3 для **@publication** учетные данные Windows, с которыми работает агент моментальных снимков и **@snapshot_job_name** и **@password**. Если агент будет использовать проверку подлинности SQL Server при подключении к издателю, необходимо также указать значение **0** для **@publisher_security_mode** и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сведения об имени входа **@publisher_login** и **@publisher_password**. Будет создано задание агента моментальных снимков для публикации.  
  
    > [!IMPORTANT]  
    >  При настройке издателя с удаленным распространителем значения, указываемые для всех параметров, включая *job_login* и *job_password*, отправляются распространителю в виде обычного текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в ядре базы данных & #40; SQL Server Configuration Manager & #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
5.  Добавьте статьи к публикации. Дополнительные сведения см. в разделе [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
6.  Запустите задание агента моментальных снимков, чтобы создать исходный моментальный снимок для этой публикации. Дополнительные сведения см. в разделе [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
#### Создание публикации слиянием  
  
1.  На издателе, хранимую [sp_replicationdboption & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) Чтобы активировать публикацию текущей базы данных с помощью репликации слиянием.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Укажите имя публикации в параметре **@publication** , а также все остальные параметры публикации. Таким образом будет определена публикация.  
  
    > [!NOTE]  
    >  Имена публикаций не могут содержать следующие символы:  
    >   
    >  % * [ ] | : " ? \ / \< >  
  
3.  На издателе, хранимую [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Укажите имя публикации, использовавшееся на шаге 2 для **@publication** учетные данные Windows, с которыми работает агент моментальных снимков и **@snapshot_job_name** и **@password**. Если агент будет использовать проверку подлинности SQL Server при подключении к издателю, необходимо также указать значение **0** для **@publisher_security_mode** и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сведения об имени входа **@publisher_login** и **@publisher_password**. Будет создано задание агента моментальных снимков для публикации.  
  
    > [!IMPORTANT]  
    >  При настройке издателя с удаленным распространителем значения, указываемые для всех параметров, включая *job_login* и *job_password*, отправляются распространителю в виде обычного текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в ядре базы данных & #40; SQL Server Configuration Manager & #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
4.  Добавьте статьи к публикации. Дополнительные сведения см. в разделе [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
5.  Запустите задание агента моментальных снимков, чтобы создать исходный моментальный снимок для этой публикации. Дополнительные сведения см. в статье [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
###  <a name="TsqlExample"></a> Пример (Transact-SQL)  
 В следующем примере производится создание публикации транзакций. Учетные данные Windows, необходимые для создания задания агента моментальных снимков и агента чтения журнала, передаются через переменные скрипта.  
  
 [!code-sql[HowTo#sp_AddTranPub](../../../relational-databases/replication/codesnippet/tsql/create-a-publication_1.sql)]  
  
 В следующем примере производится создание публикации слиянием. Учетные данные Windows, необходимые для создания задания агента моментальных снимков, передаются через переменные скрипта.  
  
 [!code-sql[HowTo#sp_AddMergePub](../../../relational-databases/replication/codesnippet/tsql/create-a-publication_2.sql)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Публикации можно создавать программно с помощью объектов RMO. Классы RMO, с помощью которых создается публикация, зависят от типа создаваемой публикации.  
  
#### Создание публикации транзакций или моментальных снимков  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> класса для базы данных публикации, установите <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства экземпляра <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1 и вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод. Если <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> возвращает **false**, убедитесь, что база данных существует.  
  
3.  Если <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing%2A> свойство **false**, задайте для него значение **true**.  
  
4.  Для публикации транзакций, проверьте значение <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentExists%2A> свойство. Если свойство имеет значение **true**, то задание агента чтения журнала уже есть в базе данных. Если свойство имеет значение **false**, выполните следующие действия.  
  
    -   Задайте <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> и <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> или <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> поля <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentProcessSecurity%2A> учетные данные для [!INCLUDE[msCoName](../../../includes/msconame-md.md)] учетной записи Windows, под которой запускается агент чтения журнала.  
  
        > [!NOTE]  
        >  Установка <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentProcessSecurity%2A> не является обязательным, если публикация создается членом **sysadmin** фиксированной серверной роли. В этом случае агент будет выполнять олицетворение учетную запись агента SQL Server. Дополнительные сведения см. в статье [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   (Необязательно) Задайте <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> и <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> или <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> поля <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentPublisherSecurity%2A> при использовании проверки подлинности SQL Server для подключения к издателю.  
  
    -   Вызов <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.CreateLogReaderAgent%2A> метод для создания задания агента чтения журнала для базы данных.  
  
5.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.TransPublication> класса и задайте следующие свойства для этого объекта:  
  
    -    <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1 для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   Имя опубликованной базы данных для <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>.  
  
    -   Имя публикации, для <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>.  
  
    -   Объект <xref:Microsoft.SqlServer.Replication.PublicationType> либо <xref:Microsoft.SqlServer.Replication.PublicationType.Transactional> или <xref:Microsoft.SqlServer.Replication.PublicationType.Snapshot>.  
  
    -    <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> и <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> поля <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> учетные данные для учетной записи Windows, под которой выполняется агент моментальных снимков. Эта учетная запись также используется, когда агент моментальных снимков соединяется с локальным распространителем, и для любых удаленных соединений, где применяется проверка подлинности Windows;  
  
        > [!NOTE]  
        >  Установка <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> не является обязательным, если публикация создается членом **sysadmin** фиксированной серверной роли. В этом случае агент будет выполнять олицетворение учетную запись агента SQL Server. Дополнительные сведения см. в статье [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   (Необязательно) <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> и <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> или <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> поля <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentPublisherSecurity%2A> при использовании проверки подлинности SQL Server для подключения к издателю.  
  
    -   (Необязательно) Используйте исключающего логического оператора OR (**|** в Visual C# и **или** в Visual Basic) и исключающего логического или (**^** в Visual C# и **Xor** в Visual Basic) для установки <xref:Microsoft.SqlServer.Replication.PublicationAttributes> значения для <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> свойство.  
  
    -   (Необязательно) Имя издателя для <xref:Microsoft.SqlServer.Replication.TransPublication.PublisherName%2A> Если издатель не является SQL Server издателем.  
  
6.  Вызов <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> метод для создания публикации.  
  
    > [!IMPORTANT]  
    >  При настройке издателя с удаленным распространителем значения, заданные для всех свойств, включая <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A>, отправляются распространителю в виде обычного текста. Необходимо зашифровать соединение между издателем и его удаленным распространителем перед вызовом метода <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> метод. Дополнительные сведения см. в разделе [Включение шифрования соединений в ядре базы данных & #40; SQL Server Configuration Manager & #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
7.  Вызов <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> метод для создания задания агента моментальных снимков для публикации.  
  
#### Создание публикации слиянием  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> класса для базы данных публикации, установите <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства экземпляра <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1 и вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод. Если <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> возвращает **false**, убедитесь, что база данных существует.  
  
3.  Если <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> свойство **false**, задайте для него значение **true**, и вызвать <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>.  
  
4.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergePublication> класса и задайте следующие свойства для этого объекта:  
  
    -    <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1 для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   Имя опубликованной базы данных для <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>.  
  
    -   Имя публикации, для <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>.  
  
    -    <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> и <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> поля <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> учетные данные для учетной записи Windows, под которой выполняется агент моментальных снимков. Эта учетная запись также используется, когда агент моментальных снимков соединяется с локальным распространителем, и для любых удаленных соединений, где применяется проверка подлинности Windows;  
  
        > [!NOTE]  
        >  Установка <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> не является обязательным, если публикация создается членом **sysadmin** фиксированной серверной роли. Дополнительные сведения см. в статье [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   (Необязательно) Используйте исключающего логического оператора OR (**|** в Visual C# и **или** в Visual Basic) и исключающего логического или (**^** в Visual C# и **Xor** в Visual Basic) для установки <xref:Microsoft.SqlServer.Replication.PublicationAttributes> значения для <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> свойство.  
  
5.  Вызов <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> метод для создания публикации.  
  
    > [!IMPORTANT]  
    >  При настройке издателя с удаленным распространителем значения, заданные для всех свойств, включая <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A>, отправляются распространителю в виде обычного текста. Необходимо зашифровать соединение между издателем и его удаленным распространителем перед вызовом метода <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> метод. Дополнительные сведения см. в разделе [Включение шифрования соединений в ядре базы данных & #40; SQL Server Configuration Manager & #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
6.  Вызов <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> метод для создания задания агента моментальных снимков для публикации.  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 В этом примере в базе данных AdventureWorks разрешается публикация транзакций, определяется задание агента чтения журнала и создается публикация AdvWorksProductTran. Для этой публикации необходимо определить статью. Данные учетной записи Windows, необходимые для создания задания агента чтения журнала и задания агента моментальных снимков, передаются во время выполнения. Более подробные сведения по определению статей моментальных снимков и транзакций с помощью объектов RMO см. в разделе [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
 [!code-csharp[HowTo#rmo_CreateTranPub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createtranpub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranPub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createtranpub)]  
  
 В этом примере в базе данных AdventureWorks разрешается публикация слиянием и создается публикация AdvWorksSalesOrdersMerge. Для этой публикации все равно необходимо определить статьи. Данные учетной записи Windows, необходимые для создания задания агента моментальных снимков, предоставляются во время выполнения. Более подробные сведения по определению статей публикацией слиянием с помощью объектов RMO см. в разделе [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
 [!code-csharp[HowTo#rmo_CreateMergePub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepub)]  
  
## См. также:  
 [Использование программы sqlcmd с переменными скрипта](../../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)   
 [Публикация данных и объектов базы данных](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Основные понятия объектов RMO](../../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Определение статьи](../../../relational-databases/replication/publish/define-an-article.md)   
 [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Настройка распространителя](../../../relational-databases/replication/configure-distribution.md)   
 [Организация безопасности распространителя](../../../relational-databases/replication/security/secure-the-distributor.md)   
 [Организация безопасности издателя](../../../relational-databases/replication/security/secure-the-publisher.md)  
  
  