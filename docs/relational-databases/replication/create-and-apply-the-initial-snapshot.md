---
title: "Создание и применение исходного моментального снимка | Microsoft Docs"
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
  - "моментальные снимки [репликация SQL Server], создание"
  - "репликация моментальных снимков [SQL Server], исходные моментальные снимки"
ms.assetid: 742727a1-5189-44ec-b3ae-6fd7aa1f5347
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Создание и применение исходного моментального снимка
  В данном разделе описывается процесс создания и применения исходного моментального снимка в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или объектов RMO. Публикации слиянием, использующие параметризованные фильтры, требуют моментальных снимков, состоящих из двух частей. Дополнительные сведения см. в статье [Create a Snapshot for a Merge Publication with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
 **В этом разделе**  
  
-   **Для создания и применения исходного моментального снимка используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 По умолчанию, если выполняется агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , агент моментальных снимков создает моментальный снимок сразу после того, как создана публикация с помощью мастера создания публикаций. Затем по умолчанию агент распространителя (для репликации моментальных снимков и репликации транзакций) или агент слияния (для подписок на публикацию слиянием) применяет моментальный снимок ко всем подпискам. Моментальный снимок также можно создать с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и монитора репликации. Сведения о запуске монитора репликации см. в разделе [запустить монитор репликации](../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
#### Создание моментального снимка в среде Management Studio  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Щелкните правой кнопкой мыши публикацию, для которой нужно создать моментальный снимок и нажмите кнопку **Просмотр состояния агента моментальных снимков**.  
  
4.  В **Просмотр состояния агента моментальных снимков — \< публикация>** диалоговом нажмите кнопку **запустить**.  
  
 Когда агент моментальных снимков закончит создание моментального снимка, на экране появится сообщение: «[100%] Сформирован моментальный снимок 17 статей».  
  
#### Создание моментального снимка в мониторе репликации  
  
1.  В мониторе репликации раскройте группу издателей на левой панели, а затем раскройте нужного издателя.  
  
2.  Щелкните правой кнопкой мыши публикацию, для которой нужно создать моментальный снимок и нажмите кнопку **Создать моментальный снимок**.  
  
3.  Чтобы просмотреть состояние агента моментальных снимков, перейдите на вкладку **Агенты** . Более подробные сведения, щелкните правой кнопкой мыши агент моментальных снимков в сетке и нажмите кнопку **Просмотр сведений о**.  
  
#### Применение моментального снимка  
  
1.  После создания моментальный снимок применяется при синхронизации подписки с помощью агента распространителя или агента слияния:  
  
    -   Если агент настроен для постоянной работы (выбор по умолчанию для репликации транзакций), моментальный снимок применяется автоматически после того, как он был создан.  
  
    -   Если агент настроен для работы по расписанию, моментальный снимок применяется при следующем запланированном запуске агента.  
  
    -   Если агент настроен для работы по запросу, моментальный снимок применяется при следующем запуске агента.  
  
     Дополнительные сведения о синхронизации подписок см. в разделе [синхронизации принудительной подписки](../../relational-databases/replication/synchronize-a-push-subscription.md) и [синхронизации подписки по запросу](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Исходные моментальные снимки можно создавать программно, создавая и запуская задания агента моментальных снимков либо запуская исполняемый файл агента моментальных снимков из пакетного файла. После создания исходный моментальный снимок передается на подписчик и применяется при первой синхронизации подписки. Если агент моментальных снимков запускается из командной строки или пакетного файла, потребуется повторно запустить агент, когда существующий моментальный снимок станет недействительным.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
#### Создание и запуск задания агента моментальных снимков для формирования исходного моментального снимка  
  
1.  Создайте моментальный снимок, публикацию слиянием или публикацию транзакций. Дополнительные сведения см. в статье [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Выполнение [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Укажите параметр **@publication** и следующие параметры.  
  
    -   **@Job_login, который указывает** учетные данные проверки подлинности Windows, при которых выполняется агент моментальных снимков на распространителе.  
  
    -   **@Job_password**, который представляет пароль для предоставленных учетных данных Windows.  
  
    -   (Необязательно) Значение **0** для **@publisher_security_mode** Если агент будет использовать проверку подлинности SQL Server при подключении к издателю. В этом случае необходимо указать сведения об имени входа проверки подлинности SQL Server **@publisher_login** и **@publisher_password**.  
  
    -   (Необязательно) Расписание синхронизации для задания агента моментальных снимков. Дополнительные сведения см. в статье [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
    > [!IMPORTANT]  
    >  При настройке издателя с удаленным распространителем значения, указываемые для всех параметров, включая *job_login* и *job_password*, отправляются распространителю в виде обычного текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в ядре базы данных & #40; SQL Server Configuration Manager & #41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
3.  Добавьте статьи к публикации. Дополнительные сведения см. в статье [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
4.  На издателе в базе данных публикации выполните хранимую процедуру [sp_startpublication_snapshot & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-startpublication-snapshot-transact-sql.md), указывая значение **@publication** из шага 1.  
  
#### Запуск агента моментальных снимков для формирования исходного моментального снимка  
  
1.  Создайте моментальный снимок, публикацию слиянием или публикацию транзакций. Дополнительные сведения см. в разделе [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Добавьте статьи к публикации. Дополнительные сведения см. в статье [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
3.  Запуск из командной строки или пакетного файла [агент моментальных снимков репликации](../../relational-databases/replication/agents/replication-snapshot-agent.md) запустив **snapshot.exe**, указав следующие аргументы командной строки:  
  
    -   **-Publication**  
  
    -   **-Publisher**  
  
    -   **-Distributor**  
  
    -   **-PublisherDB**  
  
    -   **-ReplicationType**  
  
     При использовании проверки подлинности SQL Server необходимо также указать следующие аргументы.  
  
    -   **-DistributorLogin**  
  
    -   **-DistributorPassword**  
  
    -   **-DistributorSecurityMode** = **0**  
  
    -   **-PublisherLogin**  
  
    -   **-PublisherPassword**  
  
    -   **-PublisherSecurityMode** = **0**  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В этом примере показано, как создать публикацию транзакций и добавить задание агента моментальных снимков для публикации новых (с помощью **sqlcmd** переменные сценария). В примере также запускается задание.  
  
 [!code-sql[HowTo#sp_trangenerate_snapshot](../../relational-databases/replication/codesnippet/tsql/create-and-apply-the-ini_1.sql)]  
  
 В этом примере создается публикация слиянием и добавляет задание агента моментальных снимков (с помощью **sqlcmd** переменные) для публикации. В этом примере также запускается задание.  
  
 [!code-sql[HowTo#sp_mergegenerate_snapshot](../../relational-databases/replication/codesnippet/tsql/create-and-apply-the-ini_2.sql)]  
  
 Следующие параметры командной строки запускают агент моментальных снимков для формирования моментальных снимков для публикации слиянием.  
  
> [!NOTE]  
>  Пример разбит на строки для удобства чтения. В пакетном файле команды необходимо вводить в одной строке.  
  
```  
  
REM -- Declare variables  
SET Publisher=%InstanceName%  
SET PublicationDB=AdventureWorks2012   
SET Publication=AdvWorksSalesOrdersMerge   
  
REM --Start the Snapshot Agent to generate the snapshot for AdvWorksSalesOrdersMerge.  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %Publication%   
-Publisher %Publisher% -Distributor %Publisher% -PublisherDB %PublicationDB%   
-ReplicationType 2 -OutputVerboseLevel 1 -DistributorSecurityMode 1  
  
```  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 После создания публикации агент моментальных снимков создает моментальный снимок. Создание моментального снимка и прямой доступ из управляемого кода к функциям агента репликации могут производиться программным путем с помощью объектов RMO. Какие именно объекты при этом применяются, зависит от типа репликации. Агент моментальных снимков может быть запущен как синхронно с помощью объекта <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> , так и в асинхронном режиме из задания агента. После создания исходного моментального снимка он передается на сервер подписчика и применяется при первом сеансе синхронизации подписки. Когда данные в существующем моментальном снимке устарели, соответствующий ему агент должен быть запущен повторно. Дополнительные сведения см. в разделе [Ведение публикаций](../../relational-databases/replication/publish/maintain-publications.md).  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если необходимо хранить учетные данные, используйте [службы шифрования](http://go.microsoft.com/fwlink/?LinkId=34733) , предоставляемые платформой [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
#### Создание исходного моментального снимка для публикации транзакций или моментальных снимков из задания агента моментальных снимков (в асинхронном режиме)  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.TransPublication> класса. Задайте <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Свойства для публикации, а также набор <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства подключения, созданной на шаге 1.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы загрузить оставшиеся свойства объекта. Если этот метод возвращает **false**, то либо на шаге 2 были неверно определены свойства публикации, либо публикация не существует.  
  
4.  Если значение <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> — **false**, вызовите <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> для создания задания агента моментальных снимков для данной публикации.  
  
5.  Вызов <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> метод, чтобы запустить задание агента, формирующее моментальный снимок для этой публикации.  
  
6.  (Необязательно) Если значение <xref:Microsoft.SqlServer.Replication.TransPublication.SnapshotAvailable%2A> — **true**, моментальный снимок доступен для подписчиков.  
  
#### Создание исходного моментального снимка для публикации транзакций или моментальных снимков запуском агента моментальных снимков (в синхронном режиме)  
  
1.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> и укажите следующие необходимые свойства.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> — Имя издателя  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> — имя базы данных публикации  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> — Имя публикации  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> — Имя распространителя  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> -значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> использовать проверку подлинности Windows при подключении к издателю или значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> и значения для <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherLogin%2A> и <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherPassword%2A> Использование [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности при подключении к издателю. Рекомендуется использовать проверку подлинности Windows.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> -значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> использовать проверку подлинности Windows при соединении с распространителем, или значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> и значения для <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorLogin%2A> и <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorPassword%2A> Использование [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности при подключении к распространителю. Рекомендуется использовать проверку подлинности Windows.  
  
2.  Задайте значение <xref:Microsoft.SqlServer.Replication.ReplicationType.Transactional> или <xref:Microsoft.SqlServer.Replication.ReplicationType.Snapshot> для <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> .  
  
#### Создание исходного моментального снимка для публикации слиянием из задания агента моментальных снимков (в асинхронном режиме)  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergePublication> класса. Задайте <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Свойства для публикации, а также набор <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства подключения, созданной на шаге 1.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы загрузить оставшиеся свойства объекта. Если этот метод возвращает **false**, то либо на шаге 2 были неверно определены свойства публикации, либо публикация не существует.  
  
4.  Если значение <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> — **false**, вызовите <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> для создания задания агента моментальных снимков для данной публикации.  
  
5.  Вызов <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> метод, чтобы запустить задание агента, формирующее моментальный снимок для этой публикации.  
  
6.  (Необязательно) Если значение <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A> — **true**, моментальный снимок доступен для подписчиков.  
  
#### Создание исходного моментального снимка для публикации слиянием запуском агента моментальных снимков (в синхронном режиме)  
  
1.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> и укажите следующие необходимые свойства.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> — Имя издателя  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> — имя базы данных публикации  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> — Имя публикации  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> — Имя распространителя  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> -значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> использовать проверку подлинности Windows при подключении к издателю или значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> и значения для <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherLogin%2A> и <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherPassword%2A> Использование [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности при подключении к издателю. Рекомендуется использовать проверку подлинности Windows.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> -значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> использовать проверку подлинности Windows при соединении с распространителем, или значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> и значения для <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorLogin%2A> и <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorPassword%2A> Использование [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности при подключении к распространителю. Рекомендуется использовать проверку подлинности Windows.  
  
2.  Задайте значение <xref:Microsoft.SqlServer.Replication.ReplicationType.Merge> для <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> .  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 В следующем примере производится синхронный запуск агента моментальных снимков, который создает исходный моментальный снимок публикации транзакций.  
  
 [!code-csharp[HowTo#rmo_GenerateSnapshot](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_generatesnapshot)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateSnapshot](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_generatesnapshot)]  
  
 В следующем примере производится асинхронный запуск задания агента моментальных снимков, который создает исходный моментальный снимок публикации транзакций.  
  
 [!code-csharp[HowTo#rmo_GenerateSnapshot_WithJob](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_generatesnapshot_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateSnapshot_WithJob](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_generatesnapshot_withjob)]  
  
## См. также:  
 [Создание публикации](../../relational-databases/replication/publish/create-a-publication.md)   
 [Создание подписки по запросу](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Создание принудительной подписки](../../relational-databases/replication/create-a-push-subscription.md)   
 [Указание расписаний синхронизации](../../relational-databases/replication/specify-synchronization-schedules.md)   
 [Создание и применение моментального снимка](../../relational-databases/replication/create-and-apply-the-snapshot.md)   
 [Инициализация подписки с помощью моментального снимка](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Основные понятия объектов RMO](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Основные понятия системных хранимых процедур репликации](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Использование программы sqlcmd с переменными скрипта](../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)  
  
  