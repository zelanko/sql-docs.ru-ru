---
title: Создание моментального снимка для публикации слиянием с параметризованными фильтрами | Документация Майкрософт
ms.custom: ''
ms.date: 05/03/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- parameterized filters [SQL Server replication], snapshots
- snapshots [SQL Server replication], parameterized filters and
- filters [SQL Server replication], parameterized
ms.assetid: 00dfb229-f1de-4d33-90b0-d7c99ab52dcb
caps.latest.revision: 45
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cb2fb7f8a2a7519e89d05259e2723ccb700be6cf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32957169"
---
# <a name="create-a-snapshot-for-a-merge-publication-with-parameterized-filters"></a>Создание моментального снимка для публикации слиянием с параметризованными фильтрами
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В данном разделе описывается процесс создания моментального снимка для публикации слиянием с параметризованными фильтрами в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или объектов RMO.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Рекомендации](#Recommendations)  
  
-   **Для создания моментального снимка для публикации слиянием с параметризованными фильтрами используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   При создании моментальных снимков для публикации слиянием с помощью параметризованных фильтров необходимо сначала создать стандартный моментальный снимок (схему), который будет содержать все опубликованные данные и метаданные подписчика для подписки. Дополнительные сведения см. в статье [Создание и применение исходного моментального снимка](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md). После создания моментального снимка схемы можно создать моментальный снимок, содержащий секцию опубликованных данных для конкретного подписчика.  
  
-   Если при фильтрации одной или нескольких статей публикации получаются неперекрывающиеся секции, которые являются уникальными для каждой подписки, метаданные очищаются при каждом запуске агента слияния. Это означает, что срок действия секционированного снимка истекает быстрее. При выборе этого параметра необходимо рассмотреть возможность разрешения подписчикам инициировать создание и доставку моментальных снимков. Дополнительные сведения о параметрах фильтрации см. в разделе об установке параметров секции статьи [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md) (Моментальные снимки для публикаций слиянием с параметризованными фильтрами).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Создание моментальных снимков для секций на странице **Секции данных** диалогового окна **Свойства публикации — \<публикация>**. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Просмотр и изменение свойств публикации](../../relational-databases/replication/publish/view-and-modify-publication-properties.md). Подписчикам можно разрешить инициировать создание и доставку или только создание моментальных снимков.  
  
 Перед созданием моментальных снимков для одной или нескольких секций необходимо следующее.  
  
1.  Создать публикацию слиянием при помощи мастера создания публикаций и указать один или несколько параметризованных фильтров строк на странице **Добавление фильтра** окна мастера. Дополнительные сведения см. в статье [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
2.  Создайте моментальный снимок схемы для публикации. По умолчанию создание моментального снимка схемы происходит по завершении выполнения мастера создания публикаций; создание моментального снимка схемы также возможно из среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-generate-a-schema-snapshot"></a>Создание моментального снимка схемы  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем — папку **Публикации** .  
  
3.  Щелкните правой кнопкой мыши публикацию, для которой нужно создать моментальный снимок, а затем выберите **Просмотреть состояние агента моментальных снимков**.  
  
4.  В диалоговом окне **Просмотр состояния агента моментальных снимков — \<публикация>** щелкните **Запуск**.  
  
     Когда агент моментальных снимков закончит создание моментального снимка, на экране появится сообщение: «[100%] Сформирован моментальный снимок 17 статей».  
  
#### <a name="to-allow-subscribers-to-initiate-snapshot-generation-and-delivery"></a>Разрешение подписчикам запускать создание и доставку моментальных снимков  
  
1.  На странице **Секции данных** диалогового окна **Свойства публикации — \<публикация>** выберите **Автоматически определять секцию и, при необходимости, создавать моментальный снимок при попытке синхронизации от нового подписчика**.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### <a name="to-generate-and-refresh-snapshots"></a>Создание и обновление моментальных снимков  
  
1.  На странице **Секции данных** диалогового окна **Свойства публикации — \<публикация>** щелкните **Добавить**.  
  
2.  Введите значение **HOST_NAME()** или значение **SUSER_SNAME()** , относящееся к секции, для которой нужно создать моментальный снимок.  
  
3.  При необходимости задайте расписание обновления моментальных снимков.  
  
    1.  Установите флажок **Запланировать запуск агента моментальных снимков для этой секции в следующее время**.  
  
    2.  Примите используемое по умолчанию расписание обновления моментальных снимков или щелкните **Изменить** , чтобы указать другое расписание.  
  
4.  Щелкните **ОК**, чтобы вернуться в диалоговое окно **Свойства публикации — \<публикация>**.  
  
5.  Выберите секцию в сетке свойств, затем щелкните **Создать выбранные моментальные снимки**.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 С помощью хранимых процедур и агента моментальных снимков можно выполнить следующие действия:  
  
-   Разрешите подписчикам запрашивать создание моментального снимка и его применение при первоначальной синхронизации.  
  
-   Предварительное создание моментальных снимков для каждой секции.  
  
-   создать вручную моментальный снимок для каждого подписчика.  
  
    > [!IMPORTANT]  
    >  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
#### <a name="to-create-a-publication-that-allows-subscribers-to-initiate-snapshot-generation-and-delivery"></a>Создание публикации, которая позволяет подписчикам инициировать формирование и доставку моментальных снимков  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Укажите значения следующих параметров.  
  
    -   имя публикации в качестве значения параметра **@publication**.  
  
    -   значение **true** параметра **@allow_subscriber_initiated_snapshot**, позволяющее подписчикам запускать процесс создания моментального снимка;  
  
    -   допустимое число параллельно выполняемых процессов динамических моментальных снимков в качестве значения параметра **@max_concurrent_dynamic_snapshots**. Если выполняется максимальное число процессов и подписчик пытается создать моментальный снимок, то процесс помещается в очередь. По умолчанию число параллельных процессов не ограничено.  
  
2.  На издателе выполните процедуру [sp_addpublication_snapshot (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). В качестве значения параметра **@publication** укажите имя публикации, которое использовалось в шаге 1, а также учетные данные [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, под которыми выполняется [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md) , — в качестве значений параметров **@job_login** и **@password**. Если агент при соединении с издателем будет использовать проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , то необходимо также указать значение **0** параметра **@publisher_security_mode** укажите имя публикации, которое использовалось в шаге 1, а также учетные данные [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в параметрах **@publisher_login** и **@publisher_password**. Будет создано задание агента моментальных снимков для публикации. Дополнительные сведения о формировании исходного моментального снимка и определении пользовательского расписания для агента моментальных снимков см. в разделе [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
    > [!IMPORTANT]  
    >  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
3.  Выполните хранимую процедуру [sp_addmergearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md), чтобы добавить статьи в публикацию. Эту хранимую процедуру необходимо выполнить один раз для каждой статьи в публикации. При использовании параметризованных фильтров необходимо указать параметризованный фильтр строк для одной или нескольких статей, использующих параметр **@subset_filterclause** . Дополнительные сведения см. в статье [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
4.  Если другие статьи будут фильтроваться на основании параметризованного фильтра строк, выполните хранимую процедуру [sp_addmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md), чтобы определить между статьями соединение или связь логических записей. Эту хранимую процедуру необходимо выполнить один раз для каждой определяемой связи. Дополнительные сведения см. в разделе [Определение и изменение фильтра соединения между статьями публикации слиянием](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
5.  Если агент слияния запрашивает инициализацию подписчика моментальным снимком, то автоматически создается моментальный снимок для секции запрашивающей подписки.  
  
#### <a name="to-create-a-publication-and-pre-generate-or-automatically-refresh-snapshots"></a>Создание публикации и предварительное создание или автоматическое обновление моментальных снимков  
  
1.  Чтобы создать публикацию, выполните хранимую процедуру [sp_addmergepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Дополнительные сведения см. в статье [о создании публикации](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  На издателе выполните процедуру [sp_addpublication_snapshot (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). В качестве значения параметра **@publication** , а учетные данные Windows, с которыми работает агент моментальных снимков, — в параметрах **@job_login** и **@password**. Если агент при соединении с издателем будет использовать проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , то необходимо также указать значение **0** параметра **@publisher_security_mode** укажите имя публикации, которое использовалось в шаге 1, а также учетные данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в параметрах **@publisher_login** и **@publisher_password**. Будет создано задание агента моментальных снимков для публикации. Дополнительные сведения о формировании исходного моментального снимка и определении пользовательского расписания для агента моментальных снимков см. в разделе [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
    > [!IMPORTANT]  
    >  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
3.  Выполните хранимую процедуру [sp_addmergearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md), чтобы добавить статьи в публикацию. Эту хранимую процедуру необходимо выполнить один раз для каждой статьи в публикации. При использовании параметризованных фильтров необходимо указать параметризованный фильтр строк для одной статьи, использующей параметр **@subset_filterclause** . Дополнительные сведения см. в статье [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
4.  Если другие статьи будут фильтроваться на основании параметризованного фильтра строк, выполните хранимую процедуру [sp_addmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md), чтобы определить между статьями соединение или связь логических записей. Эту хранимую процедуру необходимо выполнить один раз для каждой определяемой связи. Дополнительные сведения см. в статье [Определение и изменение фильтра соединения между статьями публикации слиянием](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
5.  На издателе в базе данных публикации выполните хранимую процедуру [sp_helpmergepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), указав в параметре **@publication** значение из шага 1. Запомните значение параметра **snapshot_jobid** в результирующем наборе.  
  
6.  Преобразуйте значение параметра **snapshot_jobid** , полученное в шаге 5, в тип **uniqueidentifier**.  
  
7.  На издателе в базе данных **msdb** выполните хранимую процедуру [sp_start_job (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md), при этом присвойте преобразованное значение, полученное на шаге 6, параметру **@job_id**.  
  
8.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergepartition (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md). Укажите имя публикации из шага 1 в качестве значения параметра **@publication**, а также значение, определяющее секцию, в качестве значения параметра **@suser_sname**, если в предложении фильтра используется функция [SUSER_SNAME (Transact-SQL)](../../t-sql/functions/suser-sname-transact-sql.md), либо **@host_name**, если в предложении фильтра используется функция [HOST_NAME (Transact-SQL)](../../t-sql/functions/host-name-transact-sql.md).  
  
9. На издателе в базе данных публикации выполните хранимую процедуру [sp_adddynamicsnapshot_job (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql.md). Укажите имя публикации из шага 1 в качестве значения параметра **@publication**, значение параметра **@suser_sname** или **@host_name** из шага 8, а также расписание для этого задания. Будет создано задание, создающее параметризованный моментальный снимок для указанной секции. Дополнительные сведения см. в статье [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
    > [!NOTE]  
    >  Это задание выполняется в той же учетной записи Windows, что и задание исходного моментального снимка в шаге 2. Чтобы удалить задание параметризованного моментального снимка и связанную с ним секцию данных, выполните хранимую процедуру [sp_dropdynamicsnapshot_job (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropdynamicsnapshot-job-transact-sql.md).  
  
10. На издателе в базе данных публикации выполните хранимую процедуру [sp_helpmergepartition (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql.md), указав в параметре **@publication** значение из шага 1 и значение параметра **@suser_sname** или **@host_name** из шага 8. Запомните значение параметра **dynamic_snapshot_jobid** в результирующем наборе.  
  
11. На распространителе в базе данных **msdb** выполните хранимую процедуру [sp_start_job (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md), при этом присвойте значение, полученное на шаге 9, параметру **@job_id**. Будет запущено задание параметризованного моментального снимка для данной секции.  
  
12. Чтобы создать секционированный снимок для каждой подписки, повторите шаги 8–11.  
  
#### <a name="to-create-a-publication-and-manually-create-snapshots-for-each-partition"></a>Создание публикации и моментальных снимков для каждой секции вручную  
  
1.  Чтобы создать публикацию, выполните хранимую процедуру [sp_addmergepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Дополнительные сведения см. в статье [о создании публикации](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  На издателе выполните процедуру [sp_addpublication_snapshot (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). В качестве значения параметра **@publication** , а учетные данные Windows, с которыми работает агент моментальных снимков, — в параметрах **@job_login** и **@password**. Если агент при соединении с издателем будет использовать проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , то необходимо также указать значение **0** параметра **@publisher_security_mode** укажите имя публикации, которое использовалось в шаге 1, а также учетные данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в параметрах **@publisher_login** и **@publisher_password**. Будет создано задание агента моментальных снимков для публикации. Дополнительные сведения о формировании исходного моментального снимка и определении пользовательского расписания для агента моментальных снимков см. в разделе [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
    > [!IMPORTANT]  
    >  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
3.  Выполните хранимую процедуру [sp_addmergearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md), чтобы добавить статьи в публикацию. Эту хранимую процедуру необходимо выполнить один раз для каждой статьи в публикации. При использовании параметризованных фильтров необходимо указать параметризованный фильтр строк хотя бы для одной статьи, использующей параметр **@subset_filterclause** . Дополнительные сведения см. в статье [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
4.  Если другие статьи будут фильтроваться на основании параметризованного фильтра строк, выполните хранимую процедуру [sp_addmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md), чтобы определить между статьями соединение или связь логических записей. Эту хранимую процедуру необходимо выполнить один раз для каждой определяемой связи. Дополнительные сведения см. в статье [Определение и изменение фильтра соединения между статьями публикации слиянием](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
5.  Чтобы создать стандартную схему моментального снимка и другие файлы, запустите задание моментального снимка или агент моментальных снимков репликации из командной строки. Дополнительные сведения см. в разделе [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
6.  Запустите агент моментальных снимков репликации из командной строки еще раз, чтобы создать файлы массового копирования (BCP-файл); при этом укажите расположение секционированного снимка в качестве значения параметра **-DynamicSnapshotLocation** , а также одно или оба приведенные ниже свойства, определяющие секцию:  
  
    -   **-DynamicFilterHostName** — если используется функция [HOST_NAME (Transact-SQL)](../../t-sql/functions/host-name-transact-sql.md).  
  
    -   **-DynamicFilterLogin** — если используется функция [SUSER_SNAME (Transact-SQL)](../../t-sql/functions/suser-sname-transact-sql.md).  
  
7.  Чтобы создать секционированный снимок для каждой подписки, повторите шаг 6.  
  
8.  Чтобы применить исходный секционированный снимок на подписчиках, запустите агент слияния для каждой подписки; при этом укажите следующие свойства:  
  
    -   **-Hostname** — значение, с помощью которого определяется секция, если реальное значение параметра HOST_NAME переопределяется;  
  
    -   **-DynamicSnapshotLocation** — расположение динамического моментального снимка для этой секции.  
  
> [!NOTE]  
>  Дополнительные сведения о программировании агентов репликации см. в статье [Основные понятия исполняемых файлов агента репликации](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В этом примере создается публикация слиянием с параметризованными фильтрами, где подписчики запускают процесс создания моментальных снимков. Значения для параметров **@job_login** и **@job_password** передаются с использованием переменных сценария.  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../relational-databases/replication/codesnippet/tsql/create-a-snapshot-for-a-_1.sql)]  
  
 В этом примере публикация создается с помощью параметризованного фильтра, где для каждого подписчика с помощью хранимой процедуры [sp_addmergepartition](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md) определена своя секция, а также путем выполнения хранимой процедуры [sp_adddynamicsnapshot_job](../../relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql.md) , передающей сведения о секционировании, создано фильтруемое задание моментального снимка. Значения для параметров **@job_login** и **@job_password** передаются с использованием переменных сценария.  
  
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
>  Если фильтрация статьи приводит к образованию неперекрывающихся секций, уникальных для каждой подписки (если указано значение F:Microsoft.SqlServer.Replication.PartitionOptions.NonOverlappingSingleSubscription для P:Microsoft.SqlServer.Replication.MergeArticle.PartitionOption при создании статьи публикации слиянием), метаданные очищаются при запуске агента слияния. Это означает, что срок действия секционированного снимка истекает быстрее. Если выбран этот режим, рекомендуется рассмотреть возможность разрешения подписчикам создания моментальных снимков. Дополнительные сведения см. в подразделе «Использование соответствующих параметров фильтрации» раздела [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если необходимо хранить учетные данные, используйте [службы шифрования](http://go.microsoft.com/fwlink/?LinkId=34733) , предоставляемые платформой [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
#### <a name="to-create-a-publication-that-allows-subscribers-to-initiate-snapshot-generation-and-delivery"></a>Создание публикации, которая позволяет подписчикам инициировать формирование и доставку моментальных снимков  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> для базы данных публикации, установите в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> экземпляр соединения <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданный на шаге 1, и вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . If <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> возвращает значение **false**, убедитесь, что база данных существует.  
  
3.  If <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> присвоено значение **false**, укажите значение **true** и вызовите <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>.  
  
4.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePublication> и укажите для него следующие свойства:  
  
    -   Соединение <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданное на шаге 1, в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   имя опубликованной базы данных в свойстве <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>;  
  
    -   имя публикации в качестве значения свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>;  
  
    -   Максимальное количество заданий динамических моментальных снимков, которые должны быть выполнены <xref:Microsoft.SqlServer.Replication.MergePublication.MaxConcurrentDynamicSnapshots%2A>. Поскольку инициированные подписчиком запросы на моментальные снимки могут возникнуть в любое время, это свойство ограничивает количество заданий агента моментальных снимков, которые могут выполняться одновременно, когда несколько подписчиков запрашивают секционированные снимки в одно и то же время. Если выполняется максимальное количество заданий, дополнительные запросы на секционированные моментальные снимки помещаются в очередь, пока одно из выполняющихся заданий не будет завершено.  
  
    -   Используйте оператор побитового логического ИЛИ (**|** в Visual C# и **Or** в Visual Basic), чтобы добавить значение <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowSubscriberInitiatedSnapshot> в <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A>.  
  
    -   Поля <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> и <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> свойства <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> содержат учетные данные учетной записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, от имени которой выполняются задания агента моментальных снимков.  
  
        > [!NOTE]  
        >  Рекомендуется указывать свойство <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> , если публикация создается членом предопределенной роли сервера **sysadmin** . Дополнительные сведения см. в статье [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
5.  Чтобы создать публикацию, вызовите метод <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> .  
  
    > [!IMPORTANT]  
    >  При настройке издателя с удаленным распространителем значения, передаваемые для всех свойств, включая <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A>, отправляются распространителю в виде обычного текста. Перед вызовом метода <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> следует зашифровать подключение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
6.  Чтобы добавить статьи к публикации, используйте свойство <xref:Microsoft.SqlServer.Replication.MergeArticle> . Укажите свойство <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> хотя бы для одной статьи, определяющей параметризованный фильтр. (Необязательно) Создайте объекты <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> , определяющие фильтры соединения между статьями. Дополнительные сведения см. в статье [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
7.  Если для свойства <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> указано значение **false**, вызовите <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> , чтобы создать исходное задание агента моментального снимка для этой публикации.  
  
8.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> объекта <xref:Microsoft.SqlServer.Replication.MergePublication> , созданного на шаге 4. Запустится задание агента по созданию исходного моментального снимка. Дополнительные сведения о формировании исходного моментального снимка и определении пользовательского расписания для агента моментальных снимков см. в разделе [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
9. (Необязательно) Проверьте, указано ли значение **true** для свойства <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A> , чтобы определить, когда исходный моментальный снимок будет готов к использованию.  
  
10. Когда агент слияния для подписчика подключается в первый раз, секционированный моментальный снимок создается автоматически.  
  
#### <a name="to-create-a-publication-and-pregenerate-or-automatically-refresh-snapshots"></a>Создание публикации и предварительное создание или автоматическое обновление моментальных снимков  
  
1.  Чтобы определить публикацию слиянием, используйте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePublication> . Дополнительные сведения см. в разделе [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Чтобы добавить статьи к публикации, используйте свойство <xref:Microsoft.SqlServer.Replication.MergeArticle> . Укажите свойство <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> хотя бы для одной статьи, определяющей параметризованный фильтр, и создайте любые объекты <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> , определяющие фильтры соединения между статьями. Дополнительные сведения см. в статье [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
3.  Если для свойства <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> указано значение **false**, вызовите <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> .  
  
4.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> объекта <xref:Microsoft.SqlServer.Replication.MergePublication> , созданного в шаге 1. Этот метод запускает задание агента по созданию исходного моментального снимка. Дополнительные сведения о создании исходного моментального снимка и определении пользовательского расписания для агента моментальных снимков см. в разделе [Создание и применение исходного моментального снимка](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
5.  Проверьте, указано ли значение **true** для свойства <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A> , чтобы определить, когда исходный моментальный снимок будет готов к использованию.  
  
6.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePartition> и укажите критерии параметризованного фильтра для подписчика, используя одно или оба следующих свойства.  
  
    -   Если секция подписчика определена результатом функции [SUSER_SNAME (Transact-SQL)](../../t-sql/functions/suser-sname-transact-sql.md), используйте <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterLogin%2A>.  
  
    -   Если секция подписчика определена результатом функции [HOST_NAME (Transact-SQL)](../../t-sql/functions/host-name-transact-sql.md) или перегружающей ее функции, используйте <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterHostName%2A>.  
  
7.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob> и укажите то же свойство, что и в шаге 6.  
  
8.  Используйте класс <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule> , чтобы определить расписание создания фильтрованных моментальных снимков для секции подписчика.  
  
9. Используя экземпляр <xref:Microsoft.SqlServer.Replication.MergePublication> из шага 1, вызовите метод <xref:Microsoft.SqlServer.Replication.MergePublication.AddMergePartition%2A>. Передайте объект <xref:Microsoft.SqlServer.Replication.MergePartition> , созданный на шаге 6.  
  
10. Используя экземпляр <xref:Microsoft.SqlServer.Replication.MergePublication> из шага 1, вызовите метод <xref:Microsoft.SqlServer.Replication.MergePublication.AddMergeDynamicSnapshotJob%2A> . Передайте объект <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob> из шага 7 и объект <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule> из шага 8.  
  
11. Вызовите метод <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergeDynamicSnapshotJobs%2A>и найдите объект <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob> для вновь добавленного задания секционированного моментального снимка в возвращенном массиве.  
  
12. Получите свойство <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob.Name%2A> для этого задания.  
  
13. Создайте соединение с распространителем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
14. Создайте экземпляр класса <xref:Microsoft.SqlServer.Management.Smo.Server> управляющих объектов SQL Server, передав объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 13.  
  
15. Создайте экземпляр класса <xref:Microsoft.SqlServer.Management.Smo.Agent.Job> , передав свойство <xref:Microsoft.SqlServer.Management.Smo.Server.JobServer%2A> объекта <xref:Microsoft.SqlServer.Management.Smo.Server> из шага 14 и имя задания из шага 12.  
  
16. Вызовите метод <xref:Microsoft.SqlServer.Management.Smo.Agent.Job.Start%2A> , чтобы запустить задание секционированного моментального снимка.  
  
17. Повторите шаги 6 — 16 для каждого подписчика.  
  
#### <a name="to-create-a-publication-and-manually-create-snapshots-for-each-partition"></a>Создание публикации и моментальных снимков для каждой секции вручную  
  
1.  Чтобы определить публикацию слиянием, используйте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePublication> . Дополнительные сведения см. в разделе [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Чтобы добавить статьи в публикацию, используйте свойство <xref:Microsoft.SqlServer.Replication.MergeArticle> . Укажите свойство <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> хотя бы для одной статьи, определяющей параметризованный фильтр, и создайте любые объекты <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> , определяющие фильтры соединения между статьями. Дополнительные сведения см. в статье [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
3.  Создайте исходный моментальный снимок. Дополнительные сведения см. в статье [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
4.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> и укажите следующие необходимые свойства.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> — имя издателя.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> — имя базы данных публикации.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> — имя публикации.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> — имя распространителя.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> — значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> для использования встроенной проверки подлинности Windows или значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> для использования проверки подлинности SQL Server.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> — значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> для использования встроенной проверки подлинности Windows или значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> для использования проверки подлинности SQL Server.  
  
5.  Укажите значение <xref:Microsoft.SqlServer.Replication.ReplicationType.Merge> в параметре <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>.  
  
6.  Задайте одно или несколько следующих свойств, чтобы определить параметры секционирования.  
  
    -   Если секция подписчика определена результатом функции [SUSER_SNAME (Transact-SQL)](../../t-sql/functions/suser-sname-transact-sql.md), используйте <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DynamicFilterLogin%2A>.  
  
    -   Если секция подписчика определена результатом функции [HOST_NAME (Transact-SQL)](../../t-sql/functions/host-name-transact-sql.md) или перегружающей ее функции, используйте <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DynamicFilterHostName%2A>.  
  
7.  Вызовите метод <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> .  
  
8.  Повторите шаги 4–7 для каждого подписчика.  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 В этом примере создается публикация слиянием, позволяющая подписчикам запрашивать создание моментальных снимков.  
  
 [!code-cs[HowTo#rmo_CreateMergePub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepub)]  
  
 В этом примере вручную создается секция подписчика и фильтрованный моментальный снимок для публикации слиянием с параметризованными фильтрами строк.  
  
 [!code-cs[HowTo#rmo_CreateMergePartition](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepartition)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePartition](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepartition)]  
  
 В этом примере вручную запускается агент моментальных снимков для создания фильтрованного моментального снимка данных для подписчика на публикацию слиянием с параметризованными фильтрами строк.  
  
 [!code-cs[HowTo#rmo_GenerateFilteredSnapshot](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_generatefilteredsnapshot)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateFilteredSnapshot](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_generatefilteredsnapshot)]  
  
## <a name="see-also"></a>См. также:  
 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)   
 [Replication System Stored Procedures Concepts](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  (Моментальные снимки для публикаций слиянием с параметризованными фильтрами)  
 [Replication Security Best Practices](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  
