---
title: Создание моментального снимка для публикации слиянием с параметризованными фильтрами | Документация Майкрософт
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- parameterized filters [SQL Server replication], snapshots
- snapshots [SQL Server replication], parameterized filters and
- filters [SQL Server replication], parameterized
ms.assetid: 00dfb229-f1de-4d33-90b0-d7c99ab52dcb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a28bf1fc8960c9e34c4acdcbae5ae863d4595a3b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73882364"
---
# <a name="create-a-snapshot-for-a-merge-publication-with-parameterized-filters"></a>Создание моментального снимка для публикации слиянием с параметризованными фильтрами
  В данном разделе описывается процесс создания моментального снимка для публикации слиянием с параметризованными фильтрами в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или объектов RMO.  
  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   При создании моментальных снимков для публикации слиянием с помощью параметризованных фильтров необходимо сначала создать стандартный моментальный снимок (схему), который будет содержать все опубликованные данные и метаданные подписчика для подписки. Дополнительные сведения см. в разделе [Create and Apply the Initial Snapshot](create-and-apply-the-initial-snapshot.md). После создания моментального снимка схемы можно создать моментальный снимок, содержащий секцию опубликованных данных для конкретного подписчика.  
  
-   Если при фильтрации одной или нескольких статей публикации получаются неперекрывающиеся секции, которые являются уникальными для каждой подписки, метаданные очищаются при каждом запуске агента слияния. Это означает, что срок действия секционированного снимка истекает быстрее. При выборе этого параметра необходимо рассмотреть возможность разрешения подписчикам инициировать создание и доставку моментальных снимков. Дополнительные сведения о параметрах фильтрации см. в разделе об установке параметров секции статьи [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md) (Моментальные снимки для публикаций слиянием с параметризованными фильтрами).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Создание моментальных снимков для секций на странице **Секции данных** диалогового окна **Свойства публикации — \<публикация>**. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Просмотр и изменение свойств публикации](publish/view-and-modify-publication-properties.md). Подписчикам можно разрешить инициировать создание и доставку или только создание моментальных снимков.  
  
 Перед созданием моментальных снимков для одной или нескольких секций необходимо следующее.  
  
1.  Создать публикацию слиянием при помощи мастера создания публикаций и указать один или несколько параметризованных фильтров строк на странице **Добавление фильтра** окна мастера. Дополнительные сведения см. в статье [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
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
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergepublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql). Укажите следующие параметры:  
  
    -   Имя публикации для ** \@публикации**.  
  
    -   Значение `true` для ** \@allow_subscriber_initiated_snapshot**, которое позволяет подписчикам инициировать процесс создания моментального снимка.  
  
    -   Используемых Количество процессов динамических моментальных снимков, которые могут выполняться параллельно для ** \@max_concurrent_dynamic_snapshots**. Если выполняется максимальное число процессов и подписчик пытается создать моментальный снимок, то процесс помещается в очередь. По умолчанию число параллельных процессов не ограничено.  
  
2.  На издателе выполните процедуру [sp_addpublication_snapshot (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql). Укажите имя публикации, используемое на шаге 1 ** \@для публикации** , [!INCLUDE[msCoName](../../includes/msconame-md.md)] и учетные данные Windows, с которыми [репликация агент моментальных снимков](agents/replication-snapshot-agent.md) проверку подлинности при соединении с издателем, необходимо также указать значение [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **0** для ** \@publisher_security_mode** и сведения об имени входа для ** \@publisher_login** и ** \@publisher_password**. Будет создано задание агента моментальных снимков для публикации. Дополнительные сведения о формировании исходного моментального снимка и определении пользовательского расписания для агента моментальных снимков см. в разделе [Create and Apply the Initial Snapshot](create-and-apply-the-initial-snapshot.md).  
  
    > [!IMPORTANT]  
    >  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. [в разделе Enable encrypted connections to the ядро СУБД &#40;диспетчер конфигурации SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
3.  Выполните хранимую процедуру [sp_addmergearticle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql), чтобы добавить статьи в публикацию. Эту хранимую процедуру необходимо выполнить один раз для каждой статьи в публикации. При использовании параметризованных фильтров необходимо указать параметризованный фильтр строк для одной или нескольких статей с помощью параметра ** \@subset_filterclause** . Дополнительные сведения см. в статье [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
4.  Если другие статьи будут фильтроваться на основании параметризованного фильтра строк, выполните хранимую процедуру [sp_addmergefilter (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql), чтобы определить между статьями соединение или связь логических записей. Эту хранимую процедуру необходимо выполнить один раз для каждой определяемой связи. Дополнительные сведения см. в статье [Определение и изменение фильтра соединения между статьями публикации слиянием](publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
5.  Если агент слияния запрашивает инициализацию подписчика моментальным снимком, то автоматически создается моментальный снимок для секции запрашивающей подписки.  
  
#### <a name="to-create-a-publication-and-pre-generate-or-automatically-refresh-snapshots"></a>Создание публикации и предварительное создание или автоматическое обновление моментальных снимков  
  
1.  Чтобы создать публикацию, выполните хранимую процедуру [sp_addmergepublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql). Дополнительные сведения см. в разделе [Create a Publication](publish/create-a-publication.md).  
  
2.  На издателе выполните процедуру [sp_addpublication_snapshot (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql). Укажите имя публикации, используемое на шаге 1 для ** \@публикации** , и учетные данные Windows, с которыми агент моментальных снимков выполняется для ** \@job_login** и ** \@пароля**. Если агент при соединении с издателем будет использовать проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то необходимо также присвоить значение **0** параметру **\@publisher_security_mode** и передать сведения об имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в качестве значений параметров **\@publisher_login** и **\@publisher_password**. Будет создано задание агента моментальных снимков для публикации. Дополнительные сведения о формировании исходного моментального снимка и определении пользовательского расписания для агента моментальных снимков см. в разделе [Create and Apply the Initial Snapshot](create-and-apply-the-initial-snapshot.md).  
  
    > [!IMPORTANT]  
    >  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. [в разделе Enable encrypted connections to the ядро СУБД &#40;диспетчер конфигурации SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
3.  Выполните хранимую процедуру [sp_addmergearticle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql), чтобы добавить статьи в публикацию. Эту хранимую процедуру необходимо выполнить один раз для каждой статьи в публикации. При использовании параметризованных фильтров необходимо указать параметризованный фильтр строк для одной статьи с помощью параметра ** \@subset_filterclause** . Дополнительные сведения см. в статье [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
4.  Если другие статьи будут фильтроваться на основании параметризованного фильтра строк, выполните хранимую процедуру [sp_addmergefilter (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql), чтобы определить между статьями соединение или связь логических записей. Эту хранимую процедуру необходимо выполнить один раз для каждой определяемой связи. Дополнительные сведения см. в статье [Определение и изменение фильтра соединения между статьями публикации слиянием](publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
5.  В издателе в базе данных публикации выполните хранимую процедуру [sp_helpmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), указав в параметре **\@publication** значение из шага 1. Запомните значение параметра **snapshot_jobid** в результирующем наборе.  
  
6.  Преобразуйте значение параметра **snapshot_jobid** , полученное в шаге 5, в тип **uniqueidentifier**.  
  
7.  В издателе в базе данных **msdb** выполните хранимую процедуру [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql), указав преобразованное значение, полученное в шаге 6, в параметре **\@job_id**.  
  
8.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergepartition (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql). Укажите имя публикации из шага 1 для ** \@публикации** , а также значение, используемое для определения секции ** \@SUSER_SNAME** если в предложении фильтра используется [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql) или ** \@HOST_NAME** , если в предложении фильтра используется HOST_NAME &#40;[Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) .  
  
9. На издателе в базе данных публикации выполните хранимую процедуру [sp_adddynamicsnapshot_job (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql). Укажите имя публикации из шага 1 для ** \@публикации**, значение ** \@SUSER_SNAME** или ** \@HOST_NAME** из шага 8, а также расписание для задания. Будет создано задание, создающее параметризованный моментальный снимок для указанной секции. Дополнительные сведения см. в разделе [Указание расписаний синхронизации](specify-synchronization-schedules.md).  
  
    > [!NOTE]  
    >  Это задание выполняется в той же учетной записи Windows, что и задание исходного моментального снимка в шаге 2. Чтобы удалить задание параметризованного моментального снимка и связанную с ним секцию данных, выполните хранимую процедуру [sp_dropdynamicsnapshot_job (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dropdynamicsnapshot-job-transact-sql).  
  
10. В издателе в базе данных публикации выполните хранимую процедуру [sp_helpmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql), указав значение параметра **\@publication** из шага 1 и значение параметра **\@suser_sname** или **\@host_name** из шага 8. Запомните значение параметра **dynamic_snapshot_jobid** в результирующем наборе.  
  
11. В распространителе в базе данных **msdb** выполните хранимую процедуру [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql), присвоив значение, полученное в шаге 9, параметру **\@job_id**. Будет запущено задание параметризованного моментального снимка для данной секции.  
  
12. Чтобы создать секционированный снимок для каждой подписки, повторите шаги 8–11.  
  
#### <a name="to-create-a-publication-and-manually-create-snapshots-for-each-partition"></a>Создание публикации и моментальных снимков для каждой секции вручную  
  
1.  Чтобы создать публикацию, выполните хранимую процедуру [sp_addmergepublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql). Дополнительные сведения см. в разделе [Create a Publication](publish/create-a-publication.md).  
  
2.  На издателе выполните процедуру [sp_addpublication_snapshot (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql). Укажите имя публикации, используемое на шаге 1 для ** \@публикации** , и учетные данные Windows, с которыми агент моментальных снимков выполняется для ** \@job_login** и ** \@пароля**. Если агент при соединении с издателем будет использовать проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то необходимо также присвоить значение **0** параметру **\@publisher_security_mode** и передать сведения об имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в качестве значений параметров **\@publisher_login** и **\@publisher_password**. Будет создано задание агента моментальных снимков для публикации. Дополнительные сведения о формировании исходного моментального снимка и определении пользовательского расписания для агента моментальных снимков см. в разделе [Create and Apply the Initial Snapshot](create-and-apply-the-initial-snapshot.md).  
  
    > [!IMPORTANT]  
    >  Если издатель настраивается с удаленным распространителем, то значения, передаваемые для всех аргументов, включая *job_login* и *job_password*, передаются распространителю в формате обычного (незашифрованного) текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. [в разделе Enable encrypted connections to the ядро СУБД &#40;диспетчер конфигурации SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
3.  Выполните хранимую процедуру [sp_addmergearticle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql), чтобы добавить статьи в публикацию. Эту хранимую процедуру необходимо выполнить один раз для каждой статьи в публикации. При использовании параметризованных фильтров необходимо указать параметризованный фильтр строк по крайней мере для одной статьи с помощью параметра ** \@subset_filterclause** . Дополнительные сведения см. в статье [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
4.  Если другие статьи будут фильтроваться на основании параметризованного фильтра строк, выполните хранимую процедуру [sp_addmergefilter (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql), чтобы определить между статьями соединение или связь логических записей. Эту хранимую процедуру необходимо выполнить один раз для каждой определяемой связи. Дополнительные сведения см. в статье [Определение и изменение фильтра соединения между статьями публикации слиянием](publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
5.  Чтобы создать стандартную схему моментального снимка и другие файлы, запустите задание моментального снимка или агент моментальных снимков репликации из командной строки. Дополнительные сведения см. в разделе [Create and Apply the Initial Snapshot](create-and-apply-the-initial-snapshot.md).  
  
6.  Запустите агент моментальных снимков репликации из командной строки еще раз, чтобы создать файлы массового копирования (BCP-файл); при этом укажите расположение секционированного снимка в качестве значения параметра **-DynamicSnapshotLocation** , а также одно или оба приведенные ниже свойства, определяющие секцию:  
  
    -   **-DynamicFilterHostName** — значение, если используется [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) .  
  
    -   **-DynamicFilterLogin** — значение, если используется [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql) .  
  
7.  Чтобы создать секционированный снимок для каждой подписки, повторите шаг 6.  
  
8.  Чтобы применить исходный секционированный снимок на подписчиках, запустите агент слияния для каждой подписки; при этом укажите следующие свойства:  
  
    -   **-HostName** — значение, используемое для определения секции, если фактическое значение HOST_NAME переопределяется.  
  
    -   **-DynamicSnapshotLocation** — расположение динамического моментального снимка для этой секции.  
  
> [!NOTE]  
>  Дополнительные сведения о программировании агентов репликации см. в статье [Основные понятия исполняемых файлов агента репликации](concepts/replication-agent-executables-concepts.md).  
  
###  <a name="TsqlExample"></a>Примеры (Transact-SQL)  
 В этом примере создается публикация слиянием с параметризованными фильтрами, где подписчики запускают процесс создания моментальных снимков. Значения для ** \@job_login** и ** \@job_password** передаются с помощью переменных скрипта.  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubdynamic1.sql#sp_mergedynamicpub1)]  
  
 В этом примере публикация создается с помощью параметризованного фильтра, где для каждого подписчика с помощью хранимой процедуры [sp_addmergepartition](/sql/relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql) определена своя секция, а также путем выполнения хранимой процедуры [sp_adddynamicsnapshot_job](/sql/relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql) , передающей сведения о секционировании, создано фильтруемое задание моментального снимка. Значения для ** \@job_login** и ** \@job_password** передаются с помощью переменных скрипта.  
  
 [!code-sql[HowTo#sp_MergeDynamicPubPlusPartition](../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubdynamic2.sql#sp_mergedynamicpubpluspartition)]  
  
 В этом примере публикация создается с помощью параметризованного фильтра, где путем передачи сведений о секционировании для подписчика должна создаваться своя секция данных и фильтруемое задание моментального снимка. Подписчик передает сведения о секционировании с помощью параметров командной строки, если агенты репликации запускаются вручную. В этом примере предполагается, что также уже создана подписка на публикацию.  
  
 [!code-sql[HowTo#sp_MergeDynamicPubPartitionManual](../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubdynamic3.sql#sp_mergedynamicpubpartitionmanual)]  
  
 
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
>  Если фильтрация статьи приводит к образованию неперекрывающихся секций, уникальных для каждой подписки (если указано значение <xref:Microsoft.SqlServer.Replication.PartitionOptions.NonOverlappingSingleSubscription> для <xref:Microsoft.SqlServer.Replication.MergeArticle.PartitionOption%2A> при создании статьи публикации слиянием), метаданные очищаются при запуске агента слияния. Это означает, что срок действия секционированного снимка истекает быстрее. Если выбран этот режим, рекомендуется рассмотреть возможность разрешения подписчикам создания моментальных снимков. Дополнительные сведения см. в подразделе «Использование соответствующих параметров фильтрации» раздела [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если необходимо хранить учетные данные, используйте [службы шифрования](https://go.microsoft.com/fwlink/?LinkId=34733) , предоставляемые платформой [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
#### <a name="to-create-a-publication-that-allows-subscribers-to-initiate-snapshot-generation-and-delivery"></a>Создание публикации, которая позволяет подписчикам инициировать формирование и доставку моментальных снимков  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> для базы данных публикации, установите в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> экземпляр соединения <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданный на шаге 1, и вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> возвращает значение `false`, убедитесь, что база данных существует.  
  
3.  Если свойству <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> присвоено значение `false`, укажите значение `true` и вызовите <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>.  
  
4.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePublication> и укажите для него следующие свойства:  
  
    -   Соединение <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданное на шаге 1, в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   имя опубликованной базы данных в свойстве <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>;  
  
    -   имя публикации в качестве значения свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>;  
  
    -   Максимальное количество заданий динамических моментальных снимков, которые должны быть выполнены <xref:Microsoft.SqlServer.Replication.MergePublication.MaxConcurrentDynamicSnapshots%2A>. Поскольку инициированные подписчиком запросы на моментальные снимки могут возникнуть в любое время, это свойство ограничивает количество заданий агента моментальных снимков, которые могут выполняться одновременно, когда несколько подписчиков запрашивают секционированные снимки в одно и то же время. Если выполняется максимальное количество заданий, дополнительные запросы на секционированные моментальные снимки помещаются в очередь, пока одно из выполняющихся заданий не будет завершено.  
  
    -   Используйте оператор побитового логического ИЛИ (`|` в Visual C# и `Or` в Visual Basic), чтобы добавить значение <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowSubscriberInitiatedSnapshot> в <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A>.  
  
    -   Поля <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> и <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> свойства <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> содержат учетные данные учетной записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, от имени которой выполняются задания агента моментальных снимков.  
  
        > [!NOTE]  
        >  Рекомендуется указывать свойство <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A>, если публикация создается членом предопределенной роли сервера `sysadmin`. Дополнительные сведения см. в разделе [модель безопасности агента репликации](security/replication-agent-security-model.md).  
  
5.  Чтобы создать публикацию, вызовите метод <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> .  
  
    > [!IMPORTANT]  
    >  При настройке издателя с удаленным распространителем значения, передаваемые для всех свойств, включая <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A>, отправляются распространителю в виде обычного текста. Перед вызовом метода <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> следует зашифровать подключение между издателем и его удаленным распространителем. Дополнительные сведения см. [в разделе Enable encrypted connections to the ядро СУБД &#40;диспетчер конфигурации SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
6.  Чтобы добавить статьи к публикации, используйте свойство <xref:Microsoft.SqlServer.Replication.MergeArticle> . Укажите свойство <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> хотя бы для одной статьи, определяющей параметризованный фильтр. (Необязательно) Создайте объекты <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> , определяющие фильтры соединения между статьями. Дополнительные сведения см. в статье [определить статью](publish/define-an-article.md).  
  
7.  Если для свойства <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> указано значение `false`, вызовите <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A>, чтобы создать исходное задание агента моментального снимка для этой публикации.  
  
8.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> объекта <xref:Microsoft.SqlServer.Replication.MergePublication> , созданного на шаге 4. Запустится задание агента по созданию исходного моментального снимка. Дополнительные сведения о формировании исходного моментального снимка и определении пользовательского расписания для агента моментальных снимков см. в разделе [Create and Apply the Initial Snapshot](create-and-apply-the-initial-snapshot.md).  
  
9. (Необязательно) Проверьте, указано ли значение `true` для свойства <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A>, чтобы определить, когда исходный моментальный снимок будет готов к использованию.  
  
10. Когда агент слияния для подписчика подключается в первый раз, секционированный моментальный снимок создается автоматически.  
  
#### <a name="to-create-a-publication-and-pregenerate-or-automatically-refresh-snapshots"></a>Создание публикации и предварительное создание или автоматическое обновление моментальных снимков  
  
1.  Чтобы определить публикацию слиянием, используйте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePublication> . Дополнительные сведения см. в разделе [Create a Publication](publish/create-a-publication.md).  
  
2.  Чтобы добавить статьи к публикации, используйте свойство <xref:Microsoft.SqlServer.Replication.MergeArticle> . Укажите свойство <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> хотя бы для одной статьи, определяющей параметризованный фильтр, и создайте любые объекты <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> , определяющие фильтры соединения между статьями. Дополнительные сведения см. в статье [определить статью](publish/define-an-article.md).  
  
3.  Если значение <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> равно `false`, то для создания задания агента моментальных снимков для этой публикации вызовите метод <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A>.  
  
4.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> объекта <xref:Microsoft.SqlServer.Replication.MergePublication> , созданного в шаге 1. Этот метод запускает задание агента по созданию исходного моментального снимка. Дополнительные сведения о создании исходного моментального снимка и определении пользовательского расписания для агента моментальных снимков см. в разделе [Создание и применение исходного моментального снимка](create-and-apply-the-initial-snapshot.md).  
  
5.  Проверьте, указано ли значение `true` для свойства <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A>, чтобы определить, когда исходный моментальный снимок будет готов к использованию.  
  
6.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePartition> и укажите критерии параметризованного фильтра для подписчика, используя одно или оба следующих свойства.  
  
    -   Если секция подписчика определена результатом функции [SUSER_SNAME (Transact-SQL)](/sql/t-sql/functions/suser-sname-transact-sql), используйте <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterLogin%2A>.  
  
    -   Если секция подписчика определена результатом функции [HOST_NAME (Transact-SQL)](/sql/t-sql/functions/host-name-transact-sql) или перегружающей ее функции, используйте <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterHostName%2A>.  
  
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
  
1.  Чтобы определить публикацию слиянием, используйте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePublication> . Дополнительные сведения см. в разделе [Create a Publication](publish/create-a-publication.md).  
  
2.  Чтобы добавить статьи в публикацию, используйте свойство <xref:Microsoft.SqlServer.Replication.MergeArticle> . Укажите свойство <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> хотя бы для одной статьи, определяющей параметризованный фильтр, и создайте любые объекты <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> , определяющие фильтры соединения между статьями. Дополнительные сведения см. в статье [определить статью](publish/define-an-article.md).  
  
3.  Создайте исходный моментальный снимок. Дополнительные сведения см. в разделе [Create and Apply the Initial Snapshot](create-and-apply-the-initial-snapshot.md).  
  
4.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> и укажите следующие необходимые свойства.  
  
    -   
  <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> — имя издателя.  
  
    -   
  <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> — имя базы данных публикации.  
  
    -   
  <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> — имя публикации.  
  
    -   
  <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> — имя распространителя.  
  
    -   
  <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> — значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> для использования встроенной проверки подлинности Windows или значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> для использования проверки подлинности SQL Server.  
  
    -   
  <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> — значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> для использования встроенной проверки подлинности Windows или значение <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> для использования проверки подлинности SQL Server.  
  
5.  Укажите значение <xref:Microsoft.SqlServer.Replication.ReplicationType.Merge> в параметре <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>.  
  
6.  Задайте одно или несколько следующих свойств, чтобы определить параметры секционирования.  
  
    -   Если секция подписчика определена результатом функции [SUSER_SNAME (Transact-SQL)](/sql/t-sql/functions/suser-sname-transact-sql), используйте <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DynamicFilterLogin%2A>.  
  
    -   Если секция подписчика определена результатом функции [HOST_NAME (Transact-SQL)](/sql/t-sql/functions/host-name-transact-sql) или перегружающей ее функции, используйте <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DynamicFilterHostName%2A>.  
  
7.  Вызовите метод <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> .  
  
8.  Повторите шаги 4–7 для каждого подписчика.  
  
###  <a name="PShellExample"></a>Примеры (объекты RMO)  
 В этом примере создается публикация слиянием, позволяющая подписчикам запрашивать создание моментальных снимков.  
  
 [!code-csharp[HowTo#rmo_CreateMergePub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergepub)]  
  
 В этом примере вручную создается секция подписчика и фильтрованный моментальный снимок для публикации слиянием с параметризованными фильтрами строк.  
  
 [!code-csharp[HowTo#rmo_CreateMergePartition](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergepartition)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePartition](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergepartition)]  
  
 В этом примере вручную запускается агент моментальных снимков для создания фильтрованного моментального снимка данных для подписчика на публикацию слиянием с параметризованными фильтрами строк.  
  
 [!code-csharp[HowTo#rmo_GenerateFilteredSnapshot](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_generatefilteredsnapshot)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateFilteredSnapshot](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_generatefilteredsnapshot)]  
  
## <a name="see-also"></a>См. также:  
 [Параметризованные фильтры строк](merge/parameterized-filters-parameterized-row-filters.md)   
 [Основные понятия системных хранимых процедур репликации](concepts/replication-system-stored-procedures-concepts.md)   
 [Моментальные снимки для публикаций слиянием с параметризованными фильтрами](snapshots-for-merge-publications-with-parameterized-filters.md)   
 [Рекомендации по обеспечению безопасности репликации](security/replication-security-best-practices.md)  
  
  
