---
title: Создание и применение исходного моментального снимка | Документация Майкрософт
ms.custom: ''
ms.date: 11/20/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], creating
- snapshot replication [SQL Server], initial snapshots
ms.assetid: 742727a1-5189-44ec-b3ae-6fd7aa1f5347
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 48a3bfbca1b133be9c8be9b05fef3f4e2dd9ae14
ms.sourcegitcommit: 636c02bd04f091ece934e78640b2363d88cac28d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860736"
---
# <a name="create-and-apply-the-initial-snapshot"></a>Создание и применение исходного моментального снимка
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
В данном разделе описывается процесс создания и применения исходного моментального снимка в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или объектов RMO. Публикации слиянием, использующие параметризованные фильтры, требуют моментальных снимков, состоящих из двух частей. Дополнительные сведения см. в статье [Создание моментального снимка для публикации слиянием с параметризованными фильтрами](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  Моментальные снимки создаются агентом моментальных снимков после создания публикации. Моментальные снимки могут создаваться:  
  
-   Немедленно. По умолчанию моментальный снимок для публикации слиянием формируется немедленно после создания публикации в мастере создания публикаций.    
-   По расписанию. Расписание задается на странице **Агент моментальных снимков** мастера создания публикаций либо при использовании хранимых процедур или объектов RMO.    
-   Вручную. Агент моментальных снимков запускается из командной строки или из среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Дополнительные сведения о выполнении агентов см. в статьях [Основные понятия исполняемых файлов агента репликации](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) и [Запуск и остановка агента репликации (среда SQL Server Management Studio)](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
Для репликации слиянием моментальный снимок формируется при каждом запуске агента моментальных снимков. Для репликации транзакций формирование моментального снимка зависит от настроек свойства публикации **immediate_sync**. Если значение свойства установлено в TRUE (значение по умолчанию при использовании мастера создания публикаций), моментальный снимок создается при каждом запуске агента моментальных снимков и может быть применен к подписчику в любое время. Если значение свойства установлено в FALSE (значение по умолчанию при использовании хранимой процедуры **sp_addpublication**), моментальный снимок создается только в том случае, если после запуска агента моментальных снимков была добавлена новая подписка. Для проведения синхронизации подписчики должны ждать завершения работы агента моментальных снимков.  
  
Когда создаются моментальные снимки, они сохраняются по умолчанию в стандартной папке моментальных снимков, расположенной на распространителе. Файлы моментальных снимков можно также сохранить на сменных носителях, например на сменных дисках, компакт-дисках или в местоположениях, отличных от папки моментальных снимков по умолчанию. Кроме этого, эти файлы можно сжимать для облегчения их хранения и передачи, а также выполнять скрипты до или после применения моментального снимка на подписчике. Дополнительные сведения об этих параметрах см. в разделе [Snapshot Options](../../relational-databases/replication/snapshot-options.md).  
  
Если требуется моментальный снимок для публикации слиянием, в которой используются параметризованные фильтры, процесс создания моментального снимка происходит в два этапа. Сначала создается моментальный снимок схемы, который содержит скрипты репликации и схему публикуемых объектов, но не содержит данные. Потом каждая подписка инициализируется при помощи моментального снимка, который содержит скрипты и схему, скопированную из моментального снимка схемы, и данные, которые принадлежат секции подписки. Дополнительные сведения см. в статье [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
После того как моментальный снимок создан на издателе и сохранен в папке по умолчанию или в каком-либо другом местоположении, этот моментальный снимок можно передать подписчику и применить. Агент распространителя (для репликации моментальных снимков или репликации транзакций) или агент слияния (для репликации слиянием) передает моментальный снимок и применяет файлы схемы и данных в базе данных подписки на подписчике во время выполнения первоначальной синхронизации. Если используется мастер создания подписки, первоначальная синхронизация происходит по умолчанию немедленно после создания подписки. Этот режим управляется параметром **Инициализировать, когда** на странице **Инициализация подписок** мастера. Когда моментальные снимки создаются после инициализации подписки, они не применяются на подписчике, если подписка не помечена для повторной инициализации. Дополнительные сведения см. в статье [Повторная инициализация подписок](../../relational-databases/replication/reinitialize-subscriptions.md).  
  
После того, как агент распространителя или агент слияния применяет исходный моментальный снимок, агент распространяет последующие обновления и другие изменения данных. Когда моментальные снимки распространяются и применяются на подписчиках, воздействие оказывается только на подписчики, ожидающие исходные или новые моментальные снимки. Другие подписчики на данную публикацию (уже получающие вставки, обновления, удаления или другие изменения опубликованных данных) не подвергаются воздействию.  

Чтобы просмотреть или изменить папку по умолчанию для моментального снимка, см.  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Изменение параметров моментального снимка](../../relational-databases/replication/snapshot-options.md)  
  
-   Программирование репликации и RMO: [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md)  

## <a name="default-snapshot-location"></a>Расположение моментального снимка по умолчанию

 Задайте местоположение моментальных снимков по умолчанию на странице **Папка моментальных снимков** мастера настройки распространителя. Дополнительные сведения см. в статье [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md). При создании публикации на сервере, не настроенном в качестве распространителя, задайте местоположение моментальных снимков по умолчанию на странице **Папка моментальных снимков** мастера создания публикаций. Дополнительные сведения об использовании мастера см. в статье [Создание публикации](../../relational-databases/replication/publish/create-a-publication.md).  
  
 В диалоговом окне **Свойства распространителя —** распространитель> **на странице \<Издатели** измените расположение моментальных снимков по умолчанию. Дополнительные сведения см. в статье [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md). В диалоговом окне **Свойства публикации — \<публикация>** укажите папку моментальных снимков для каждой публикации. Дополнительные сведения см. в статье [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### <a name="modify-the-default-snapshot-location"></a>Изменение местоположения моментальных снимков по умолчанию  
  
1.  В диалоговом окне **Свойства распространителя — \<распространитель>** на странице **Издатели** нажмите кнопку свойств ( **...** ) рядом с издателем, для которого нужно изменить расположение моментальных снимков по умолчанию.  
  
2.  В диалоговом окне **Свойства издателя — \<издатель>** введите значение для свойства **Папка моментальных снимков по умолчанию**.  
  
    > [!NOTE]  
    >  Агент моментальных снимков должен иметь разрешения на запись в указанный каталог, а агент распространителя или агент слияния должен иметь разрешения на чтение из этого каталога. Если используются подписки по запросу, необходимо указать UNC-путь общего каталога, например \\\computername\snapshot. Дополнительные сведения см. в статье [Организация безопасности папки моментальных снимков](../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="create-snapshot"></a>Создание моментального снимка
По умолчанию, если выполняется агент SQL Server, агент моментальных снимков создает моментальный снимок сразу после того, как создана публикация с помощью мастера создания публикаций. Затем по умолчанию агент распространителя (для репликации моментальных снимков и репликации транзакций) или агент слияния (для подписок на публикацию слиянием) применяет моментальный снимок ко всем подпискам. Моментальный снимок также можно создать с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и монитора репликации. Сведения о запуске монитора репликации см. в [этой статье](../../relational-databases/replication/monitor/start-the-replication-monitor.md).  

### <a name="using-sql-server-management-studio"></a>Использование среды SQL Server Management Studio

1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера.    
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .    
3.  Щелкните правой кнопкой мыши публикацию, для которой нужно создать моментальный снимок, а затем выберите **Просмотреть состояние агента моментальных снимков**.    
4.  В диалоговом окне **Просмотр состояния агента моментальных снимков — \<публикация>** щелкните **Запуск**.    
 Когда агент моментальных снимков закончит создание моментального снимка, на экране появится сообщение: «[100%] Сформирован моментальный снимок 17 статей».  
  
### <a name="in-replication-monitor"></a>В мониторе репликации  
  
1.  В мониторе репликации раскройте группу издателей на левой панели, а затем раскройте нужного издателя.    
2.  Щелкните правой кнопкой мыши публикацию, для которой нужно создать моментальный снимок, и выберите **Создать моментальный снимок**.    
3.  Чтобы просмотреть состояние агента моментальных снимков, перейдите на вкладку **Агенты** . Для получения дополнительных сведений щелкните правой кнопкой мыши агент моментальных снимков в сетке и выберите **Просмотреть сведения**.  

## <a name="using-transact-sql"></a>Использование Transact-SQL
Исходные моментальные снимки можно создавать программно, создавая и запуская задания агента моментальных снимков либо запуская исполняемый файл агента моментальных снимков из пакетного файла. После создания исходный моментальный снимок передается на подписчик и применяется при первой синхронизации подписки. Если агент моментальных снимков запускается из командной строки или пакетного файла, потребуется повторно запустить агент, когда существующий моментальный снимок станет недействительным.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  

1.  Создайте моментальный снимок, публикацию слиянием или публикацию транзакций. Дополнительные сведения см. в разделе [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Выполните хранимую процедуру [sp_addpublication_snapshot (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Укажите параметр **@publication** и следующие параметры.  
  
    -   **@job_login — указывает** учетные данные для проверки подлинности Windows, под которыми запускается агент моментальных снимков на распространителе.  
  
    -   **@job_password** — пароль для указанных учетных данных Windows.  
  
    -   (Необязательно) Значение **0** в параметре **@publisher_security_mode** , если агент при соединении с издателем будет использовать проверку подлинности SQL Server. В этом случае в параметрах **@publisher_login** и **@publisher_password** .  
  
    -   (Необязательно) Расписание синхронизации для задания агента моментальных снимков. Дополнительные сведения см. в разделе [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
    > [!IMPORTANT]  
    >  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
3.  Добавьте статьи к публикации. Дополнительные сведения см. в статье [определить статью](../../relational-databases/replication/publish/define-an-article.md).  
  
4.  На издателе в базе данных публикации выполните хранимую процедуру [sp_startpublication_snapshot (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-startpublication-snapshot-transact-sql.md), указав в параметре **@publication** значение из шага 1.  
  
## <a name="apply-a-snapshot"></a>Применение моментального снимка  

### <a name="using-sql-server-management-studio"></a>Использование среды SQL Server Management Studio
  
1.  После создания моментальный снимок применяется при синхронизации подписки с помощью агента распространителя или агента слияния:   
    -   Если агент настроен для постоянной работы (выбор по умолчанию для репликации транзакций), моментальный снимок применяется автоматически после того, как он был создан.   
    -   Если агент настроен для работы по расписанию, моментальный снимок применяется при следующем запланированном запуске агента.    
    -   Если агент настроен для работы по запросу, моментальный снимок применяется при следующем запуске агента.  
  
     Дополнительные сведения о синхронизации подписок см. в разделах [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md) и [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
###   <a name="use-transact-sql"></a>Использование Transact-SQL  
 
1.  Создайте моментальный снимок, публикацию слиянием или публикацию транзакций. Дополнительные сведения см. в разделе [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Добавьте статьи к публикации. Дополнительные сведения см. в статье [определить статью](../../relational-databases/replication/publish/define-an-article.md).  
  
3.  Из командной строки или из пакетного файла запустите [агент слияния репликации](../../relational-databases/replication/agents/replication-snapshot-agent.md) , вызвав программу **snapshot.exe**со следующими параметрами командной строки.  
  
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
 В этом примере показано, как создавать публикации транзакций и добавлять задания агента моментальных снимков к новым публикациям (с помощью переменных скрипта **sqlcmd** ). В примере также запускается задание.  
  
 [!code-sql[HowTo#sp_trangenerate_snapshot](../../relational-databases/replication/codesnippet/tsql/create-and-apply-the-ini_1.sql)]  
  
 В этом примере создается публикация слиянием, к которой добавляется задание агента моментальных снимков (с помощью переменных **sqlcmd** ). В этом примере также запускается задание.  
  
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
 После создания публикации агент моментальных снимков создает моментальный снимок. Создание моментального снимка и прямой доступ из управляемого кода к функциям агента репликации могут производиться программным путем с помощью объектов RMO. Какие именно объекты при этом применяются, зависит от типа репликации. Агент моментальных снимков может быть запущен как синхронно с помощью объекта <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> , так и в асинхронном режиме из задания агента. После создания исходного моментального снимка он передается на сервер подписчика и применяется при первом сеансе синхронизации подписки. Когда данные в существующем моментальном снимке устарели, соответствующий ему агент должен быть запущен повторно. Дополнительные сведения см. в статье [Обслуживание публикаций](../../relational-databases/replication/publish/maintain-publications.md).  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если необходимо хранить учетные данные, используйте [службы шифрования](https://go.microsoft.com/fwlink/?LinkId=34733) , предоставляемые платформой [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
#### <a name="to-generate-the-initial-snapshot-for-a-snapshot-or-transactional-publication-by-starting-the-snapshot-agent-job-asynchronous"></a>Создание исходного моментального снимка для публикации транзакций или моментальных снимков из задания агента моментальных снимков (в асинхронном режиме)  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransPublication> . Задайте для публикации свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> , а также установите созданное на шаге 1 соединение <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> в качестве значения для свойства.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> , чтобы загрузить оставшиеся свойства объекта. Если этот метод возвращает **false**, то либо на шаге 2 были неверно определены свойства публикации, либо публикация не существует.  
  
4.  Если значение <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> равно **false**, то для создания задания агента моментальных снимков для этой публикации вызовите метод <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> .  
  
5.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> , чтобы запустить задание агента, которое создает моментальный снимок для этой публикации.  
  
6.  Если параметр <xref:Microsoft.SqlServer.Replication.TransPublication.SnapshotAvailable%2A> равно **true**, моментальный снимок доступен для подписчиков (необязательно).  
  
#### <a name="to-generate-the-initial-snapshot-for-a-snapshot-or-transactional-publication-by-running-the-snapshot-agent-synchronous"></a>Создание исходного моментального снимка для публикации транзакций или моментальных снимков запуском агента моментальных снимков (в синхронном режиме)  
  
1.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> и укажите следующие необходимые свойства.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> — имя издателя.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> — имя базы данных публикации.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> — имя публикации.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> — имя распространителя.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> — значение параметра <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> , чтобы использовать проверку подлинности Windows для соединения с издателем, или значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> и значения параметров <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherLogin%2A> и <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherPassword%2A> , чтобы использовать проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для соединения с издателем. Рекомендуется использовать проверку подлинности Windows.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> — значение параметра <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> , чтобы использовать проверку подлинности Windows для соединения с распространителем, или значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> и значения параметров <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorLogin%2A> и <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorPassword%2A> , чтобы использовать проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для соединения с распространителем. Рекомендуется использовать проверку подлинности Windows.  
  
2.  Укажите значение <xref:Microsoft.SqlServer.Replication.ReplicationType.Transactional> или <xref:Microsoft.SqlServer.Replication.ReplicationType.Snapshot> в параметре <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> .  
  
#### <a name="to-generate-the-initial-snapshot-for-a-merge-publication-by-starting-the-snapshot-agent-job-asynchronous"></a>Создание исходного моментального снимка для публикации слиянием из задания агента моментальных снимков (в асинхронном режиме)  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePublication> . Задайте для публикации свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> , а также установите созданное на шаге 1 соединение <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> в качестве значения для свойства.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> , чтобы загрузить оставшиеся свойства объекта. Если этот метод возвращает **false**, то либо на шаге 2 были неверно определены свойства публикации, либо публикация не существует.  
  
4.  Если значение <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> равно **false**, то для создания задания агента моментальных снимков для этой публикации вызовите метод <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> .  
  
5.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> , чтобы запустить задание агента, которое создает моментальный снимок для этой публикации.  
  
6.  Если параметр <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A> равно **true**, моментальный снимок доступен для подписчиков (необязательно).  
  
#### <a name="to-generate-the-initial-snapshot-for-a-merge-publication-by-running-the-snapshot-agent-synchronous"></a>Создание исходного моментального снимка для публикации слиянием запуском агента моментальных снимков (в синхронном режиме)  
  
1.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> и укажите следующие необходимые свойства.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> — имя издателя.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> — имя базы данных публикации.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> — имя публикации.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> — имя распространителя.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> — значение параметра <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> , чтобы использовать проверку подлинности Windows для соединения с издателем, или значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> и значения параметров <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherLogin%2A> и <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherPassword%2A> , чтобы использовать проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для соединения с издателем. Рекомендуется использовать проверку подлинности Windows.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> — значение параметра <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> , чтобы использовать проверку подлинности Windows для соединения с распространителем, или значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> и значения параметров <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorLogin%2A> и <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorPassword%2A> , чтобы использовать проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для соединения с распространителем. Рекомендуется использовать проверку подлинности Windows.  
  
2.  Укажите значение <xref:Microsoft.SqlServer.Replication.ReplicationType.Merge> в параметре <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> .  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 В следующем примере производится синхронный запуск агента моментальных снимков, который создает исходный моментальный снимок публикации транзакций.  
  
 [!code-cs[HowTo#rmo_GenerateSnapshot](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_generatesnapshot)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateSnapshot](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_generatesnapshot)]  
  
 В следующем примере производится асинхронный запуск задания агента моментальных снимков, который создает исходный моментальный снимок публикации транзакций.  
  
 [!code-cs[HowTo#rmo_GenerateSnapshot_WithJob](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_generatesnapshot_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateSnapshot_WithJob](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_generatesnapshot_withjob)]  
  
## <a name="see-also"></a>См. также:  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md)   
 [Инициализация подписки с помощью моментального снимка](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Replication Management Objects Concepts](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Replication Security Best Practices](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Replication System Stored Procedures Concepts](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Использование программы sqlcmd с переменными скрипта](../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)  
  
  
