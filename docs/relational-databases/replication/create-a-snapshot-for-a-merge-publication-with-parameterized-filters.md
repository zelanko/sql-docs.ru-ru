---
title: "Создание моментального снимка для публикации слиянием с параметризованными фильтрами | Microsoft Docs"
ms.custom: ""
ms.date: "05/03/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "параметризованные фильтры [репликация SQL Server], моментальные снимки"
  - "моментальные снимки [репликация SQL Server], параметризованные фильтры и"
  - "фильтры [репликация SQL Server], параметризованные"
ms.assetid: 00dfb229-f1de-4d33-90b0-d7c99ab52dcb
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 45
---
# Создание моментального снимка для публикации слиянием с параметризованными фильтрами
  В данном разделе описывается процесс создания моментального снимка для публикации слиянием с параметризованными фильтрами в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или объектов RMO.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Рекомендации](#Recommendations)  
  
-   **Для создания моментального снимка для публикации слиянием с параметризованными фильтрами используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   При создании моментальных снимков для публикации слиянием с помощью параметризованных фильтров необходимо сначала создать стандартный моментальный снимок (схему), который будет содержать все опубликованные данные и метаданные подписчика для подписки. Дополнительные сведения см. в статье [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md). После создания моментального снимка схемы можно создать моментальный снимок, содержащий секцию опубликованных данных для конкретного подписчика.  
  
-   Если при фильтрации одной или нескольких статей публикации получаются неперекрывающиеся секции, которые являются уникальными для каждой подписки, метаданные очищаются при каждом запуске агента слияния. Это означает, что срок действия секционированного снимка истекает быстрее. При выборе этого параметра необходимо рассмотреть возможность разрешения подписчикам инициировать создание и доставку моментальных снимков. Дополнительные сведения о параметрах фильтрации см. в разделе «Установка секций параметры»» из [моментальные снимки для публикаций слиянием с помощью параметризованных фильтров](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Создание моментальных снимков для секции на **секции данных** Страница **Свойства публикации — \< публикация>** диалоговое окно. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md). Подписчикам можно разрешить инициировать создание и доставку или только создание моментальных снимков.  
  
 Перед созданием моментальных снимков для одной или нескольких секций необходимо следующее.  
  
1.  Создать публикацию слиянием при помощи мастера создания публикаций и указать один или несколько параметризованных фильтров строк на странице **Добавление фильтра** окна мастера. Дополнительные сведения см. в разделе [Define and Modify a Parameterized Row Filter for a Merge Article](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
2.  Создайте моментальный снимок схемы для публикации. По умолчанию создание моментального снимка схемы происходит по завершении выполнения мастера создания публикаций; создание моментального снимка схемы также возможно из среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### Создание моментального снимка схемы  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем — папку **Публикации** .  
  
3.  Щелкните правой кнопкой мыши публикацию, для которой нужно создать моментальный снимок и нажмите кнопку **Просмотр состояния агента моментальных снимков**.  
  
4.  В **Просмотр состояния агента моментальных снимков — \< публикация>** диалоговом нажмите кнопку **запустить**.  
  
     Когда агент моментальных снимков закончит создание моментального снимка, на экране появится сообщение: «[100%] Сформирован моментальный снимок 17 статей».  
  
#### Разрешение подписчикам запускать создание и доставку моментальных снимков  
  
1.  На **секции данных** Страница **Свойства публикации — \< публикация>** диалоговом **автоматически определять секцию и, при необходимости, при попытке синхронизации от нового подписчика, создавать моментальный снимок**.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### Создание и обновление моментальных снимков  
  
1.  На **секции данных** Страница **Свойства публикации — \< публикация>** диалоговом нажмите кнопку **Добавить**.  
  
2.  Введите значение для **HOST_NAME()** или **SUSER_SNAME()** значение, связанное с секцией, для которой нужно создать моментальный снимок.  
  
3.  При необходимости задайте расписание обновления моментальных снимков.  
  
    1.  Выберите **Расписание агента моментальных снимков для этой секции в следующее время выполнения**  
  
    2.  Примите используемое по умолчанию расписание обновления моментальных снимков или щелкните **Изменить** , чтобы указать другое расписание.  
  
4.  Щелкните **ОК**, чтобы вернуться в **Свойства публикации — \< публикация>** диалоговое окно.  
  
5.  Выберите секцию в сетке свойств, затем щелкните **Создать выбранные моментальные снимки**.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 С помощью хранимых процедур и агента моментальных снимков можно выполнить следующие действия:  
  
-   Разрешите подписчикам запрашивать создание моментального снимка и его применение при первоначальной синхронизации.  
  
-   Предварительное создание моментальных снимков для каждой секции.  
  
-   создать вручную моментальный снимок для каждого подписчика.  
  
    > [!IMPORTANT]  
    >  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
#### Создание публикации, которая позволяет подписчикам инициировать формирование и доставку моментальных снимков  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergepublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Укажите значения следующих параметров.  
  
    -   имя публикации в качестве значения параметра **@publication**;  
  
    -   Значение **true** для **@allow_subscriber_initiated_snapshot**, который позволяет подписчикам инициировать процесс моментального снимка.  
  
    -   (Необязательно) Число процессов динамических моментальных снимков, которые могут выполняться параллельно для **@max_concurrent_dynamic_snapshots**. Если выполняется максимальное число процессов и подписчик пытается создать моментальный снимок, то процесс помещается в очередь. По умолчанию число параллельных процессов не ограничено.  
  
2.  На издателе, хранимую [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Укажите имя публикации, использовавшееся на шаге 1 для **@publication** и [!INCLUDE[msCoName](../../includes/msconame-md.md)] учетные данные Windows, под которой [агент моментальных снимков репликации](../../relational-databases/replication/agents/replication-snapshot-agent.md) выполняется **@job_login** и **@password**. Если агент будет использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности при подключении к издателю, необходимо также указать значение **0** для **@publisher_security_mode** и [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сведения об имени входа **@publisher_login** и **@publisher_password**. Будет создано задание агента моментальных снимков для публикации. Дополнительные сведения о формировании исходного моментального снимка и определении пользовательского расписания для агента моментальных снимков см. в разделе [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
    > [!IMPORTANT]  
    >  При настройке издателя с удаленным распространителем значения, указываемые для всех параметров, включая *job_login* и *job_password*, отправляются распространителю в виде обычного текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в ядре базы данных & #40; SQL Server Configuration Manager & #41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
3.  Выполнение [sp_addmergearticle & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Добавление статьи к публикации. Эту хранимую процедуру необходимо выполнить один раз для каждой статьи в публикации. При использовании параметризованных фильтров, необходимо указать параметризованный фильтр строк для одной или нескольких статей с помощью **@subset_filterclause** параметр. Дополнительные сведения см. в статье [Define and Modify a Parameterized Row Filter for a Merge Article](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
4.  Если другие статьи будут фильтроваться на основании параметризованного фильтра строк, выполните [sp_addmergefilter & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) для определения соединения или связи логических записей между статьями. Эту хранимую процедуру необходимо выполнить один раз для каждой определяемой связи. Дополнительные сведения см. в статье [Define and Modify a Join Filter Between Merge Articles](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
5.  Если агент слияния запрашивает инициализацию подписчика моментальным снимком, то автоматически создается моментальный снимок для секции запрашивающей подписки.  
  
#### Создание публикации и предварительное создание или автоматическое обновление моментальных снимков  
  
1.  Выполнение [sp_addmergepublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) Чтобы создать публикацию. Дополнительные сведения см. в статье [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  На издателе, хранимую [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Укажите имя публикации, использовавшееся на шаге 1 для **@publication** учетные данные Windows, с которыми работает агент моментальных снимков и **@job_login** и **@password**. Если агент будет использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности при подключении к издателю, необходимо также указать значение **0** для **@publisher_security_mode** и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сведения об имени входа **@publisher_login** и **@publisher_password**. Будет создано задание агента моментальных снимков для публикации. Дополнительные сведения о формировании исходного моментального снимка и определении пользовательского расписания для агента моментальных снимков см. в разделе [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
    > [!IMPORTANT]  
    >  При настройке издателя с удаленным распространителем значения, указываемые для всех параметров, включая *job_login* и *job_password*, отправляются распространителю в виде обычного текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в ядре базы данных & #40; SQL Server Configuration Manager & #41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
3.  Выполнение [sp_addmergearticle & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Добавление статьи к публикации. Эту хранимую процедуру необходимо выполнить один раз для каждой статьи в публикации. При использовании параметризованных фильтров, необходимо указать параметризованный фильтр строк для одной статьи, использующей **@subset_filterclause** параметр. Дополнительные сведения см. в статье [Define and Modify a Parameterized Row Filter for a Merge Article](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
4.  Если другие статьи будут фильтроваться на основании параметризованного фильтра строк, выполните [sp_addmergefilter & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) для определения соединения или связи логических записей между статьями. Эту хранимую процедуру необходимо выполнить один раз для каждой определяемой связи. Дополнительные сведения см. в статье [Define and Modify a Join Filter Between Merge Articles](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
5.  На издателе в базе данных публикации выполните хранимую процедуру [sp_helpmergepublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), указывая значение **@publication** из шага 1. Обратите внимание на значение **snapshot_jobid** в результирующем наборе.  
  
6.  Преобразовать значение **snapshot_jobid** полученное в шаге 5, чтобы **uniqueidentifier**.  
  
7.  На издателе в **msdb** базы данных, выполните [sp_start_job & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md), указав преобразованное значение, полученное на шаге 6 для **@job_id**.  
  
8.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergepartition & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md). Укажите имя публикации из шага 1 для **@publication** и значение, используемое для определения секции для **@suser_sname** Если [SUSER_SNAME & #40; Transact-SQL & #41;](../../t-sql/functions/suser-sname-transact-sql.md) используется в предложении фильтра, так и для **@host_name** Если [HOST_NAME & #40; Transact-SQL & #41;](../../t-sql/functions/host-name-transact-sql.md) используется в предложении фильтра.  
  
9. На издателе в базе данных публикации выполните хранимую процедуру [sp_adddynamicsnapshot_job & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql.md). Укажите имя публикации из шага 1 для **@publication**, значение **@suser_sname** или **@host_name** из шага 8, а также расписание для задания. Будет создано задание, создающее параметризованный моментальный снимок для указанной секции. Дополнительные сведения см. в статье [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
    > [!NOTE]  
    >  Это задание выполняется в той же учетной записи Windows, что и задание исходного моментального снимка в шаге 2. Чтобы удалить задание параметризованного моментального снимка и его связанных данных секции, выполнение [хранимой процедуры sp_dropdynamicsnapshot_job & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-dropdynamicsnapshot-job-transact-sql.md).  
  
10. На издателе в базе данных публикации выполните хранимую процедуру [sp_helpmergepartition & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql.md), указывая значение **@publication** из шага 1 и значение **@suser_sname** или **@host_name** из шага 8. Обратите внимание на значение **dynamic_snapshot_jobid** в результирующем наборе.  
  
11. На распространителе в **msdb** базы данных, выполните [sp_start_job & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md), указав значение, полученное на шаге 9 для **@job_id**. Будет запущено задание параметризованного моментального снимка для данной секции.  
  
12. Чтобы создать секционированный снимок для каждой подписки, повторите шаги 8–11.  
  
#### Создание публикации и моментальных снимков для каждой секции вручную  
  
1.  Выполнение [sp_addmergepublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) Чтобы создать публикацию. Дополнительные сведения см. в статье [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  На издателе, хранимую [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Укажите имя публикации, использовавшееся на шаге 1 для **@publication** учетные данные Windows, с которыми работает агент моментальных снимков и **@job_login** и **@password**. Если агент будет использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности при подключении к издателю, необходимо также указать значение **0** для **@publisher_security_mode** и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сведения об имени входа **@publisher_login** и **@publisher_password**. Будет создано задание агента моментальных снимков для публикации. Дополнительные сведения о формировании исходного моментального снимка и определении пользовательского расписания для агента моментальных снимков см. в разделе [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
    > [!IMPORTANT]  
    >  При настройке издателя с удаленным распространителем значения, указываемые для всех параметров, включая *job_login* и *job_password*, отправляются распространителю в виде обычного текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в ядре базы данных & #40; SQL Server Configuration Manager & #41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
3.  Выполнение [sp_addmergearticle & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Добавление статьи к публикации. Эту хранимую процедуру необходимо выполнить один раз для каждой статьи в публикации. При использовании параметризованных фильтров, необходимо указать параметризованный фильтр строк для по крайней мере одной статьи, использующей **@subset_filterclause** параметр. Дополнительные сведения см. в статье [Define and Modify a Parameterized Row Filter for a Merge Article](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
4.  Если другие статьи будут фильтроваться на основании параметризованного фильтра строк, выполните [sp_addmergefilter & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) для определения соединения или связи логических записей между статьями. Эту хранимую процедуру необходимо выполнить один раз для каждой определяемой связи. Дополнительные сведения см. в статье [Define and Modify a Join Filter Between Merge Articles](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
5.  Чтобы создать стандартную схему моментального снимка и другие файлы, запустите задание моментального снимка или агент моментальных снимков репликации из командной строки. Дополнительные сведения см. в статье [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
6.  Снова запустите агент моментальных снимков репликации из командной строки, чтобы создать файлы массового копирования (BCP), указав расположение секционированного моментального снимка для **- DynamicSnapshotLocation** и один, или оба следующие свойства, определяющие секцию:  
  
    -   **-DynamicFilterHostName** -значение Если [HOST_NAME & #40; Transact-SQL & #41;](../../t-sql/functions/host-name-transact-sql.md) используется.  
  
    -   **-DynamicFilterLogin** -значение Если [SUSER_SNAME & #40; Transact-SQL & #41;](../../t-sql/functions/suser-sname-transact-sql.md) используется.  
  
7.  Чтобы создать секционированный снимок для каждой подписки, повторите шаг 6.  
  
8.  Чтобы применить исходный секционированный снимок на подписчиках, запустите агент слияния для каждой подписки; при этом укажите следующие свойства:  
  
    -   **Имя узла -** -значение, используемое для определения секции, если фактическое значение HOST_NAME переопределяется.  
  
    -   **-DynamicSnapshotLocation** -расположение динамического моментального снимка для этой секции.  
  
> [!NOTE]  
>  Дополнительные сведения о программировании агентов репликации см. в разделе [Основные понятия исполняемых файлов агента репликации](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В этом примере создается публикация слиянием с параметризованными фильтрами, где подписчики запускают процесс создания моментальных снимков. Значения для **@job_login** и **@job_password** передаются с использованием переменных сценария.  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../relational-databases/replication/codesnippet/tsql/create-a-snapshot-for-a-_1.sql)]  
  
 В этом примере создается публикация с помощью параметризованного фильтра, где каждый подписчик имеет его секции, определенные путем выполнения [sp_addmergepartition](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md) и задание отфильтрованного моментального снимка, созданного с помощью выполнения [sp_adddynamicsnapshot_job](../../relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql.md) передачи секционирования данных. Значения для **@job_login** и **@job_password** передаются с использованием переменных сценария.  
  
 [!code-sql[HowTo#sp_MergeDynamicPubPlusPartition](../../relational-databases/replication/codesnippet/tsql/create-a-snapshot-for-a-_2.sql)]  
  
 В этом примере публикация создается с помощью параметризованного фильтра, где путем передачи сведений о секционировании для подписчика должна создаваться своя секция данных и фильтруемое задание моментального снимка. Подписчик передает сведения о секционировании с помощью параметров командной строки, если агенты репликации запускаются вручную. В этом примере предполагается, что также уже создана подписка на публикацию.  
  
 [!code-sql[HowTo#sp_MergeDynamicPubPartitionManual](../../relational-databases/replication/codesnippet/tsql/create-a-snapshot-for-a-_3.sql)]  
  
```  
  
REM Line breaks are added to improve readability.   
REM In a batch file, commands must be made in a single line.  
REM Run the Snapshot agent from the command line to generate the standard snapshot   
REM schema and other files.   
SET DistPub=%computername%  
SET PubDB=AdventureWorks2012   
SET PubName=AdvWorksSalesPersonMerge  
  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %PubName%    
-Publisher %DistPub% -Distributor  %DistPub%  -PublisherDB %PubDB%  -ReplicationType 2    
-OutputVerboseLevel 1  -DistributorSecurityMode 1  
  
PAUSE  
  
```  
  
```  
  
REM Run the Snapshot agent from the command line, this time to generate   
REM the bulk copy (.bcp) data for each Subscriber partition.    
SET DistPub=%computername%  
SET PubDB=AdventureWorks2012   
SET PubName=AdvWorksSalesPersonMerge  
SET SnapshotDir=\\%DistPub%\repldata\unc\fernando  
  
MD %SnapshotDir%  
  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %PubName%    
-Publisher %DistPub%  -Distributor  %DistPub%  -PublisherDB %PubDB%  -ReplicationType 2    
-OutputVerboseLevel 1  -DistributorSecurityMode 1  -DynamicFilterHostName "adventure-works\Fernando"    
-DynamicSnapshotLocation %SnapshotDir%  
  
PAUSE  
  
```  
  
```  
  
REM Run the Merge Agent for each subscription to apply the partitioned   
REM snapshot for each Subscriber.    
SET Publisher = %computername%  
SET Subscriber = %computername%  
SET PubDB = AdventureWorks2012   
SET SubDB = AdventureWorks2012Replica   
SET PubName = AdvWorksSalesPersonMerge   
SET SnapshotDir=\\%DistPub%\repldata\unc\fernando  
  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE" -Publisher  %Publisher%    
-Subscriber  %Subscriber%  -Distributor %Publisher%  -PublisherDB %PubDB%    
-SubscriberDB %SubDB% -Publication %PubName%  -PublisherSecurityMode 1  -OutputVerboseLevel 3    
-Output -SubscriberSecurityMode 1  -SubscriptionType 3 -DistributorSecurityMode 1    
-Hostname "adventure-works\Fernando"  -DynamicSnapshotLocation %SnapshotDir%  
  
PAUSE  
  
```  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Для программного создания секционированных снимков можно использовать объекты RMO следующими способами.  
  
-   Разрешите подписчикам запрашивать создание моментального снимка и его применение при первоначальной синхронизации.  
  
-   Предварительное создание моментальных снимков для каждой секции.  
  
-   Создайте моментальный снимок вручную для каждого подписчика при помощи агента моментальных снимков.  
  
> [!NOTE]  
>  При фильтрации для статьи дает неперекрывающиеся секции, уникальные для каждой подписки (указав значение F:Microsoft.SqlServer.Replication.PartitionOptions.NonOverlappingSingleSubscription для P:Microsoft.SqlServer.Replication.MergeArticle.PartitionOption при создании статьи публикации слиянием), метаданные очищаются при каждом выполняется агент слияния. Это означает, что срок действия секционированного снимка истекает быстрее. Если выбран этот режим, рекомендуется рассмотреть возможность разрешения подписчикам создания моментальных снимков. Дополнительные сведения см. в подразделе «Использование соответствующих параметров фильтрации» раздела [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если необходимо хранить учетные данные, используйте [службы шифрования](http://go.microsoft.com/fwlink/?LinkId=34733) , предоставляемые платформой [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
#### Создание публикации, которая позволяет подписчикам инициировать формирование и доставку моментальных снимков  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> класса для базы данных публикации, установите <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства экземпляра <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1 и вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод. Если <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> возвращает **false**, убедитесь, что база данных существует.  
  
3.  Если <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> свойство **false**, задайте для него значение **true** и вызвать <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>.  
  
4.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergePublication> класса и задайте следующие свойства для этого объекта:  
  
    -    <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1 для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   Имя опубликованной базы данных для <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>.  
  
    -   Имя публикации, для <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>.  
  
    -   Максимальное число заданий динамического моментального снимка для <xref:Microsoft.SqlServer.Replication.MergePublication.MaxConcurrentDynamicSnapshots%2A>. Поскольку инициированные подписчиком запросы на моментальные снимки могут возникнуть в любое время, это свойство ограничивает количество заданий агента моментальных снимков, которые могут выполняться одновременно, когда несколько подписчиков запрашивают секционированные снимки в одно и то же время. Если выполняется максимальное количество заданий, дополнительные запросы на секционированные моментальные снимки помещаются в очередь, пока одно из выполняющихся заданий не будет завершено.  
  
    -   Использование побитового логического или (**|** в Visual C# и **или** в Visual Basic) для добавления значения <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowSubscriberInitiatedSnapshot> для <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A>.  
  
    -    <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> и <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> поля <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> учетные данные для [!INCLUDE[msCoName](../../includes/msconame-md.md)] учетной записи Windows, под которой запускается задание агента моментальных снимков.  
  
        > [!NOTE]  
        >  Установка <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> рекомендуется, если публикация создается членом **sysadmin** фиксированной серверной роли. Дополнительные сведения см. в статье [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
5.  Вызов <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> метод для создания публикации.  
  
    > [!IMPORTANT]  
    >  При настройке издателя с удаленным распространителем значения, заданные для всех свойств, включая <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A>, отправляются распространителю в виде обычного текста. Необходимо зашифровать соединение между издателем и его удаленным распространителем перед вызовом метода <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> метод. Дополнительные сведения см. в разделе [Включение шифрования соединений в ядре базы данных & #40; SQL Server Configuration Manager & #41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
6.  Используйте <xref:Microsoft.SqlServer.Replication.MergeArticle> свойство для добавления статей в публикацию. Укажите <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> свойство, по крайней мере одной статьи, определяющей параметризованный фильтр. (Необязательно) Создание <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> объекты, определяющие фильтры соединения между статьями. Дополнительные сведения см. в статье [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
7.  Если значение <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> — **false**, вызовите <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> для создания начального задания агента моментальных снимков для данной публикации.  
  
8.  Вызов <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> метод <xref:Microsoft.SqlServer.Replication.MergePublication> объект, созданный на шаге 4. Запустится задание агента по созданию исходного моментального снимка. Дополнительные сведения о формировании исходного моментального снимка и определении пользовательского расписания для агента моментальных снимков см. в разделе [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
9. (Необязательно) Проверьте значение **true** для <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A> Свойства, чтобы определить, когда исходный моментальный снимок готов к использованию.  
  
10. Когда агент слияния для подписчика подключается в первый раз, секционированный моментальный снимок создается автоматически.  
  
#### Создание публикации и предварительное создание или автоматическое обновление моментальных снимков  
  
1.  Использовать экземпляр <xref:Microsoft.SqlServer.Replication.MergePublication> класса, чтобы определить публикацию слиянием. Дополнительные сведения см. в статье [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Используйте <xref:Microsoft.SqlServer.Replication.MergeArticle> свойство для добавления статей в публикацию. Укажите <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> свойство, по крайней мере одной статьи, определяющей параметризованный фильтр и создайте любые <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> объекты, определяющие фильтры соединения между статьями. Дополнительные сведения см. в статье [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
3.  Если значение <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> — **false**, вызовите <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> для создания задания агента моментальных снимков для данной публикации.  
  
4.  Вызов <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> метод <xref:Microsoft.SqlServer.Replication.MergePublication> объекта, созданного на шаге 1. Этот метод запускает задание агента по созданию исходного моментального снимка. Дополнительные сведения о создании исходного моментального снимка и определении пользовательского расписания для агента моментальных снимков см. в разделе [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
5.  Проверьте значение **true** для <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A> Свойства, чтобы определить, когда исходный моментальный снимок готов к использованию.  
  
6.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergePartition> и задать критерии параметризованного фильтра для подписчика, используя один или оба из следующих свойств:  
  
    -   Если результат определяется секции подписчика [SUSER_SNAME & #40; Transact-SQL & #41;](../../t-sql/functions/suser-sname-transact-sql.md), используйте <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterLogin%2A>.  
  
    -   Если результат определяется секции подписчика [HOST_NAME & #40; Transact-SQL & #41;](../../t-sql/functions/host-name-transact-sql.md) или перегружающей ее функции, используйте <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterHostName%2A>.  
  
7.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob> класса и свойства как шаг 6.  
  
8.  Используйте <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule> класса, чтобы определить расписание для создания отфильтрованного моментального снимка для секции подписчика.  
  
9. С помощью экземпляра <xref:Microsoft.SqlServer.Replication.MergePublication> из шага 1, вызовите <xref:Microsoft.SqlServer.Replication.MergePublication.AddMergePartition%2A>. Передайте <xref:Microsoft.SqlServer.Replication.MergePartition> из шага 6.  
  
10. С помощью экземпляра <xref:Microsoft.SqlServer.Replication.MergePublication> из шага 1, вызовите <xref:Microsoft.SqlServer.Replication.MergePublication.AddMergeDynamicSnapshotJob%2A> метод. Передайте <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob> из шага 7 и <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule> из шага 8.  
  
11. Вызов <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergeDynamicSnapshotJobs%2A>, и найдите <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob> объекта для задания вновь добавленный секционированного моментального снимка в возвращаемый массив.  
  
12. Получить <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob.Name%2A> свойство для задания.  
  
13. Создайте соединение с распространителем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
14. Создайте экземпляр объекты управления SQL Server (SMO) <xref:Microsoft.SqlServer.Management.Smo.Server> класса, передав <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 13.  
  
15. Создайте экземпляр <xref:Microsoft.SqlServer.Management.Smo.Agent.Job> класса, передав <xref:Microsoft.SqlServer.Management.Smo.Server.JobServer%2A> Свойства <xref:Microsoft.SqlServer.Management.Smo.Server> объекта из шага 14 и имя задания из шага 12.  
  
16. Вызов <xref:Microsoft.SqlServer.Management.Smo.Agent.Job.Start%2A> метод, чтобы запустить задание секционированного моментального снимка.  
  
17. Повторите шаги 6 — 16 для каждого подписчика.  
  
#### Создание публикации и моментальных снимков для каждой секции вручную  
  
1.  Использовать экземпляр <xref:Microsoft.SqlServer.Replication.MergePublication> класса, чтобы определить публикацию слиянием. Дополнительные сведения см. в статье [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Используйте <xref:Microsoft.SqlServer.Replication.MergeArticle> для добавления статей публикации укажите <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> свойство, по крайней мере одной статьи, определяющей параметризованный фильтр и создайте любые <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> объекты, определяющие фильтры соединения между статьями. Дополнительные сведения см. в статье [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
3.  Создайте исходный моментальный снимок. Дополнительные сведения см. в статье [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
4.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> и укажите следующие необходимые свойства.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> — Имя издателя  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> — имя базы данных публикации  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> — Имя публикации  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> — Имя распространителя  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> -значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> используется встроенная проверка подлинности Windows или значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> для использования проверки подлинности SQL Server.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> -значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> используется встроенная проверка подлинности Windows или значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> для использования проверки подлинности SQL Server.  
  
5.  Задайте значение <xref:Microsoft.SqlServer.Replication.ReplicationType.Merge> для <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>.  
  
6.  Задайте одно или несколько следующих свойств, чтобы определить параметры секционирования.  
  
    -   Если результат определяется секции подписчика [SUSER_SNAME & #40; Transact-SQL & #41;](../../t-sql/functions/suser-sname-transact-sql.md), используйте <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DynamicFilterLogin%2A>.  
  
    -   Если результат определяется секции подписчика [HOST_NAME & #40; Transact-SQL & #41;](../../t-sql/functions/host-name-transact-sql.md) или перегружающей ее функции, используйте <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DynamicFilterHostName%2A>.  
  
7.  Вызовите метод <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> .  
  
8.  Повторите шаги 4–7 для каждого подписчика.  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 В этом примере создается публикация слиянием, позволяющая подписчикам запрашивать создание моментальных снимков.  
  
 [!code-csharp[HowTo#rmo_CreateMergePub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepub)]  
  
 В этом примере вручную создается секция подписчика и фильтрованный моментальный снимок для публикации слиянием с параметризованными фильтрами строк.  
  
 [!code-csharp[HowTo#rmo_CreateMergePartition](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepartition)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePartition](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepartition)]  
  
 В этом примере вручную запускается агент моментальных снимков для создания фильтрованного моментального снимка данных для подписчика на публикацию слиянием с параметризованными фильтрами строк.  
  
 [!code-csharp[HowTo#rmo_GenerateFilteredSnapshot](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_generatefilteredsnapshot)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateFilteredSnapshot](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_generatefilteredsnapshot)]  
  
## См. также:  
 [Параметризованные фильтры строк](../../relational-databases/replication/merge/parameterized-row-filters.md)   
 [Основные понятия системных хранимых процедур репликации](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Моментальные снимки для публикаций слиянием с параметризованными фильтрами](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  