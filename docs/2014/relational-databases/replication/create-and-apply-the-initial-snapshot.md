---
title: Создание и применение исходного моментального снимка | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: a69d4805a21cfbd83bd9a8d79b5150460d4977be
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62721691"
---
# <a name="create-and-apply-the-initial-snapshot"></a>Создание и применение исходного моментального снимка
  В данном разделе описывается процесс создания и применения исходного моментального снимка в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или объектов RMO. Публикации слиянием, использующие параметризованные фильтры, требуют моментальных снимков, состоящих из двух частей. Дополнительные сведения см. в статье [Создание моментального снимка для публикации слиянием с параметризованными фильтрами](create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
 **В этом разделе**  
  
-   **Для создания и применения исходного моментального снимка используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 По умолчанию, если выполняется агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , агент моментальных снимков создает моментальный снимок сразу после того, как создана публикация с помощью мастера создания публикаций. Затем по умолчанию агент распространителя (для репликации моментальных снимков и репликации транзакций) или агент слияния (для подписок на публикацию слиянием) применяет моментальный снимок ко всем подпискам. Моментальный снимок также можно создать с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и монитора репликации. Сведения о запуске монитора репликации см. в [этой статье](monitor/start-the-replication-monitor.md).  
  
#### <a name="to-create-a-snapshot-in-management-studio"></a>Создание моментального снимка в среде Management Studio  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Щелкните правой кнопкой мыши публикацию, для которой нужно создать моментальный снимок, а затем выберите **Просмотреть состояние агента моментальных снимков**.  
  
4.  В диалоговом окне **Просмотр состояния агента моментальных снимков — \<публикация>** щелкните **Запуск**.  
  
 Когда агент моментальных снимков закончит создание моментального снимка, на экране появится сообщение: «[100%] Сформирован моментальный снимок 17 статей».  
  
#### <a name="to-create-a-snapshot-in-replication-monitor"></a>Создание моментального снимка в мониторе репликации  
  
1.  В мониторе репликации раскройте группу издателей на левой панели, а затем раскройте нужного издателя.  
  
2.  Щелкните правой кнопкой мыши публикацию, для которой нужно создать моментальный снимок, и выберите **Создать моментальный снимок**.  
  
3.  Чтобы просмотреть состояние агента моментальных снимков, перейдите на вкладку **Агенты** . Для получения дополнительных сведений щелкните правой кнопкой мыши агент моментальных снимков в сетке и выберите **Просмотреть сведения**.  
  
#### <a name="to-apply-a-snapshot"></a>Применение моментального снимка  
  
1.  После создания моментальный снимок применяется при синхронизации подписки с помощью агента распространителя или агента слияния:  
  
    -   Если агент настроен для постоянной работы (выбор по умолчанию для репликации транзакций), моментальный снимок применяется автоматически после того, как он был создан.  
  
    -   Если агент настроен для работы по расписанию, моментальный снимок применяется при следующем запланированном запуске агента.  
  
    -   Если агент настроен для работы по запросу, моментальный снимок применяется при следующем запуске агента.  
  
     Дополнительные сведения о синхронизации подписок см. в разделах [Synchronize a Push Subscription](synchronize-a-push-subscription.md) и [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Исходные моментальные снимки можно создавать программно, создавая и запуская задания агента моментальных снимков либо запуская исполняемый файл агента моментальных снимков из пакетного файла. После создания исходный моментальный снимок передается на подписчик и применяется при первой синхронизации подписки. Если агент моментальных снимков запускается из командной строки или пакетного файла, потребуется повторно запустить агент, когда существующий моментальный снимок станет недействительным.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
#### <a name="to-create-and-run-a-snapshot-agent-job-to-generate-the-initial-snapshot"></a>Создание и запуск задания агента моментальных снимков для формирования исходного моментального снимка  
  
1.  Создайте моментальный снимок, публикацию слиянием или публикацию транзакций. Дополнительные сведения см. в разделе [Create a Publication](publish/create-a-publication.md).  
  
2.  Выполните хранимую процедуру [sp_addpublication_snapshot (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql). Укажите параметр **@publication** и следующие параметры.  
  
    -   **@job_login — указывает** учетные данные для проверки подлинности Windows, под которыми запускается агент моментальных снимков на распространителе.  
  
    -   **@job_password** — пароль для указанных учетных данных Windows.  
  
    -   (Необязательно) Значение **0** в параметре **@publisher_security_mode** , если агент при соединении с издателем будет использовать проверку подлинности SQL Server. В этом случае в параметрах **@publisher_login** и **@publisher_password**.  
  
    -   (Необязательно) Расписание синхронизации для задания агента моментальных снимков. Дополнительные сведения см. в разделе [Specify Synchronization Schedules](specify-synchronization-schedules.md).  
  
    > [!IMPORTANT]  
    >  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
3.  Добавьте статьи к публикации. Дополнительные сведения см. в статье [определить статью](publish/define-an-article.md).  
  
4.  На издателе в базе данных публикации выполните хранимую процедуру [sp_startpublication_snapshot (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-startpublication-snapshot-transact-sql), указав в параметре **@publication** значение из шага 1.  
  
#### <a name="to-run-the-snapshot-agent-to-generate-the-initial-snapshot"></a>Запуск агента моментальных снимков для формирования исходного моментального снимка  
  
1.  Создайте моментальный снимок, публикацию слиянием или публикацию транзакций. Дополнительные сведения см. в разделе [Create a Publication](publish/create-a-publication.md).  
  
2.  Добавьте статьи к публикации. Дополнительные сведения см. в статье [определить статью](publish/define-an-article.md).  
  
3.  Из командной строки или из пакетного файла запустите [агент слияния репликации](agents/replication-snapshot-agent.md) , вызвав программу **snapshot.exe**со следующими параметрами командной строки.  
  
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
  
 [!code-sql[HowTo#sp_trangenerate_snapshot](../../snippets/tsql/SQL15/replication/howto/tsql/createtranpubinitialsnapshot.sql#sp_trangenerate_snapshot)]  
  
 В этом примере создается публикация слиянием, к которой добавляется задание агента моментальных снимков (с помощью переменных **sqlcmd** ). В этом примере также запускается задание.  
  
 [!code-sql[HowTo#sp_mergegenerate_snapshot](../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubinitialsnapshot.sql#sp_mergegenerate_snapshot)]  
  
 Следующие параметры командной строки запускают агент моментальных снимков для формирования моментальных снимков для публикации слиянием.  
  
> [!NOTE]  
>  Пример разбит на строки для удобства чтения. В пакетном файле команды необходимо вводить в одной строке.  
  
 [!code-sql[HowTo#startmergesnapshot_10](../../snippets/tsql/SQL15/replication/howto/tsql/createmergesnapshot_10.bat)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 После создания публикации агент моментальных снимков создает моментальный снимок. Создание моментального снимка и прямой доступ из управляемого кода к функциям агента репликации могут производиться программным путем с помощью объектов RMO. Какие именно объекты при этом применяются, зависит от типа репликации. Агент моментальных снимков может быть запущен как синхронно с помощью объекта <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> , так и в асинхронном режиме из задания агента. После создания исходного моментального снимка он передается на сервер подписчика и применяется при первом сеансе синхронизации подписки. Когда данные в существующем моментальном снимке устарели, соответствующий ему агент должен быть запущен повторно. Дополнительные сведения см. в статье [Обслуживание публикаций](publish/maintain-publications.md).  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если необходимо хранить учетные данные, используйте [службы шифрования](https://go.microsoft.com/fwlink/?LinkId=34733) , предоставляемые платформой [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
#### <a name="to-generate-the-initial-snapshot-for-a-snapshot-or-transactional-publication-by-starting-the-snapshot-agent-job-asynchronous"></a>Создание исходного моментального снимка для публикации транзакций или моментальных снимков из задания агента моментальных снимков (в асинхронном режиме)  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransPublication> . Задайте для публикации свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> , а также установите созданное на шаге 1 соединение <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> в качестве значения для свойства.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> , чтобы загрузить оставшиеся свойства объекта. Если этот метод возвращает `false`, то либо на шаге 2 были неверно определены свойства публикации, либо публикация не существует.  
  
4.  Если значение <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> равно `false`, то для создания задания агента моментальных снимков для этой публикации вызовите метод <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A>.  
  
5.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> , чтобы запустить задание агента, которое создает моментальный снимок для этой публикации.  
  
6.  Если параметр <xref:Microsoft.SqlServer.Replication.TransPublication.SnapshotAvailable%2A> имеет значение `true`, моментальный снимок доступен для подписчиков (необязательно).  
  
#### <a name="to-generate-the-initial-snapshot-for-a-snapshot-or-transactional-publication-by-running-the-snapshot-agent-synchronous"></a>Создание исходного моментального снимка для публикации транзакций или моментальных снимков запуском агента моментальных снимков (в синхронном режиме)  
  
1.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> и укажите следующие необходимые свойства.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> — имя издателя.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> — имя базы данных публикации.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> — имя публикации.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> — имя распространителя.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> — значение параметра <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> , чтобы использовать проверку подлинности Windows для соединения с издателем, или значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> и значения параметров <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherLogin%2A> и <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherPassword%2A> , чтобы использовать проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для соединения с издателем. Рекомендуется использовать проверку подлинности Windows.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> — значение параметра <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> , чтобы использовать проверку подлинности Windows для соединения с распространителем, или значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> и значения параметров <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorLogin%2A> и <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorPassword%2A> , чтобы использовать проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для соединения с распространителем. Рекомендуется использовать проверку подлинности Windows.  
  
2.  Укажите значение <xref:Microsoft.SqlServer.Replication.ReplicationType.Transactional> или <xref:Microsoft.SqlServer.Replication.ReplicationType.Snapshot> в параметре <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A>.  
  
#### <a name="to-generate-the-initial-snapshot-for-a-merge-publication-by-starting-the-snapshot-agent-job-asynchronous"></a>Создание исходного моментального снимка для публикации слиянием из задания агента моментальных снимков (в асинхронном режиме)  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePublication> . Задайте для публикации свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> , а также установите созданное на шаге 1 соединение <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> в качестве значения для свойства.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> , чтобы загрузить оставшиеся свойства объекта. Если этот метод возвращает `false`, то либо на шаге 2 были неверно определены свойства публикации, либо публикация не существует.  
  
4.  Если значение <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> равно `false`, то для создания задания агента моментальных снимков для этой публикации вызовите метод <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A>.  
  
5.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> , чтобы запустить задание агента, которое создает моментальный снимок для этой публикации.  
  
6.  Если параметр <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A> имеет значение `true`, моментальный снимок доступен для подписчиков (необязательно).  
  
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
  
 [!code-csharp[HowTo#rmo_GenerateSnapshot](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_generatesnapshot)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateSnapshot](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_generatesnapshot)]  
  
 В следующем примере производится асинхронный запуск задания агента моментальных снимков, который создает исходный моментальный снимок публикации транзакций.  
  
 [!code-csharp[HowTo#rmo_GenerateSnapshot_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_generatesnapshot_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateSnapshot_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_generatesnapshot_withjob)]  
  
## <a name="see-also"></a>См. также  
 [Create a Publication](publish/create-a-publication.md)   
 [Создание подписки по запросу](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [Specify Synchronization Schedules](specify-synchronization-schedules.md)   
 [Создание и применение моментального снимка](create-and-apply-the-snapshot.md)   
 [Инициализация подписки с помощью моментального снимка](initialize-a-subscription-with-a-snapshot.md)   
 [Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md)   
 [Replication Security Best Practices](security/replication-security-best-practices.md)   
 [Replication System Stored Procedures Concepts](concepts/replication-system-stored-procedures-concepts.md)   
 [Использование программы sqlcmd с переменными скрипта](../scripting/sqlcmd-use-with-scripting-variables.md)  
  
  
