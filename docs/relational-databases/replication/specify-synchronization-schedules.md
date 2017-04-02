---
title: "Указание расписаний синхронизации | Microsoft Docs"
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
  - "подписки [репликация SQL Server], синхронизация"
  - "синхронизация по расписанию [репликация SQL Server]"
  - "синхронизация [репликация SQL Server], расписания"
  - "репликация [SQL Server], синхронизация"
ms.assetid: 97f2535b-ec19-4973-823d-bcf3d5aa0216
caps.latest.revision: 40
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 40
---
# Указание расписаний синхронизации
  В данном разделе описывается процесс задания расписаний синхронизации в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или объектов RMO. При создании подписки можно определить расписание синхронизации, управляющее запуском агента репликации для подписки. Если не указать параметры расписания, подписка использует расписание по умолчанию.  
  
 Подписки синхронизируются агентом распространителя (для репликации моментальных снимков и репликации транзакций) или агентом слияния (для репликации слиянием). Агенты могут работать непрерывно, запускаться по запросу или по расписанию.  
  
 **В этом разделе**  
  
-   **Для задания расписаний синхронизации используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Укажите расписания синхронизации на странице **Расписание синхронизации** мастера создания подписки. Дополнительные сведения о доступе к этому мастеру см. в разделах [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md) и [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
 Измените расписания синхронизации в диалоговом окне **Свойства расписания задания** , доступном из папки **Задания** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и в окнах подробных сведений агента в мониторе репликации. Сведения о запуске монитора репликации см. в разделе [запустить монитор репликации](../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
 При указании расписаний из папки **Задания** используйте следующую таблицу для определения имени задания агента.  
  
|Агент|Имя задания|  
|-----------|--------------|  
|Агент слияния для подписок по запросу|**\< издатель>-\< база данных публикации>-\< публикация>-\< подписчик>-\< база данных подписки>-\< целое число>**|  
|Агент слияния для принудительных подписок|**\< издатель>-\< база данных публикации>-\< публикация>-\< подписчик>-\< целое число>**|  
|Агент распространителя для принудительных подписок|**\< издатель>-\< база данных публикации>-\< публикации>-\< подписчик>-\< integer>** <sup>1</sup>|  
|Агент распространителя для подписок по запросу|**\< издатель>-\< база данных публикации>-\< публикация>-\< подписчик>-\< база данных подписки>-\< GUID>** <sup>2</sup>|  
|Агент распространителя для принудительных подписок подписчиков серверов, отличных от подписчиков SQL Server|**\< издатель>-\< база данных публикации>-\< публикация>-\< подписчик>-\< целое число>**|  
  
 <sup>1</sup> для принудительных подписок на публикации Oracle это **\< издатель>— \< издатель**> вместо **\< издатель>-\< база данных публикации>**  
  
 <sup>2</sup> для подписок по запросу на публикации Oracle это **\< издатель>-\< база данных распространителя**> вместо **\< издатель>-\< база данных публикации>**  
  
#### Указание расписаний синхронизации  
  
1.  На **SynchronizationSchedule** страница мастера создания подписки выберите одно из следующих значений из **Расписание агента** раскрывающегося списка для каждой создаваемой подписки:  
  
    -   **Выполнять постоянно**  
  
    -   **Запуск только по запросу**  
  
    -   **\<Задать расписание…>**  
  
2.  При выборе **\< задать расписание … >**, укажите расписание в **Свойства расписания задания** диалоговое окно, а затем щелкните **ОК**.  
  
3.  Завершите работу мастера.  
  
#### Изменение расписания синхронизации для принудительных подписок в мониторе репликации  
  
1.  На левой панели монитора репликации раскройте группу издателей, раскройте нужный издатель, а затем выберите публикацию.  
  
2.  Перейдите на вкладку **Все подписки** .  
  
3.  Щелкните правой кнопкой мыши подписку и нажмите кнопку **Просмотр сведений о**.  
  
4.  В **Подписка \< Имя_подписки >** окно, нажмите кнопку **Действие**, и нажмите кнопку **\< ИмяАгента> Свойства задания**.  
  
5.  На **расписания** Страница **Свойства задания — \< имя_задания>** диалоговом нажмите кнопку **изменить.**  
  
6.  В **Свойства расписания задания** диалоговое окно, выберите значение из **Тип расписания** раскрывающегося списка:  
  
    -   Для указания непрерывной работы агента выберите **Запускать автоматически при запуске агента SQL Server**.  
  
    -   Для указания работы агента по расписанию выберите **Периодически**.  
  
    -   Для указания запуска агента по запросу выберите **Один раз**.  
  
7.  При выборе значения **Периодически**укажите расписание для агента.  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### Изменение расписания синхронизации для принудительных подписок в среде Management Studio  
  
1.  Подключитесь к распространителю в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Агент SQL Server** , а затем — папку **Задания** .  
  
3.  Щелкните правой кнопкой задание для агента распространителя или агента слияния, связанных с подпиской и нажмите кнопку **Свойства**.  
  
4.  На **расписания** Страница **Свойства задания — \< имя_задания>** диалоговом нажмите кнопку **изменить.**  
  
5.  В **Свойства расписания задания** диалоговое окно, выберите значение из **Тип расписания** раскрывающегося списка:  
  
    -   Для указания непрерывной работы агента выберите **Запускать автоматически при запуске агента SQL Server**.  
  
    -   Для указания работы агента по расписанию выберите **Периодически**.  
  
    -   Для указания запуска агента по запросу выберите **Один раз**.  
  
6.  При выборе значения **Периодически**укажите расписание для агента.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### Изменение расписания синхронизации для подписок по запросу в среде Management Studio  
  
1.  Подключитесь к подписчику в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Агент SQL Server** , а затем — папку **Задания** .  
  
3.  Щелкните правой кнопкой задание для агента распространителя или агента слияния, связанных с подпиской и нажмите кнопку **Свойства**.  
  
4.  На **расписания** Страница **Свойства задания — \< имя_задания>** диалоговом нажмите кнопку **изменить.**  
  
5.  В **Свойства расписания задания** диалоговое окно, выберите значение из **Тип расписания** раскрывающегося списка:  
  
    -   Для указания непрерывной работы агента выберите **Запускать автоматически при запуске агента SQL Server**.  
  
    -   Для указания работы агента по расписанию выберите **Периодически**.  
  
    -   Для указания запуска агента по запросу выберите **Один раз**.  
  
6.  При выборе значения **Периодически**укажите расписание для агента.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Можно определить расписание синхронизации программно с помощью хранимых процедур репликации. Эти хранимые процедуры зависят от типа репликации и типа подписки (по запросу или принудительная).  
  
 Расписание определяется следующими параметрами, поведение которых наследуются от [sp_add_schedule & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md):  
  
-   **@frequency_type** -Тип частоты, используемых при составлении расписания агента.  
  
-   **@frequency_interval** — день недели, когда запускается агент.  
  
-   **@frequency_relative_interval** — неделя конкретного месяца, когда запуск агента ежемесячный запуск.  
  
-   **@frequency_recurrence_factor** — число частотных единиц, которые происходят между синхронизациями.  
  
-   **@frequency_subday** — Единица частоты, если агент запускается чаще, чем раз в день.  
  
-   **@frequency_subday_interval** -число единиц частоты между запусками агент запускается чаще, чем раз в день.  
  
-   **@active_start_time_of_day** — самое раннее время в указанный день начала запуска агента.  
  
-   **@active_end_time_of_day** — время в указанный день начала запуска агента.  
  
-   **@active_start_date** — первый день, расписание агента вступят в силу.  
  
-   **@active_end_date** — последний день, расписание агента вступят в силу.  
  
#### Определение расписания синхронизации для подписки по запросу на публикацию транзакций  
  
1.  Создайте подписку по запросу на публикацию транзакций. Дополнительные сведения см. в разделе [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
2.  На подписчике, выполните [sp_addpullsubscription_agent & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md). Укажите **@publisher**, **@publisher_db**, **@publication**, и [!INCLUDE[msCoName](../../includes/msconame-md.md)] учетные данные Windows, под которыми агент распространителя на подписчике **@job_name** и **@password**. Укажите описанные выше параметры синхронизации, определяющие расписание для задания агента распространителя, синхронизирующего подписку.  
  
#### Определение расписания синхронизации для принудительной подписки на публикацию транзакций  
  
1.  Создайте принудительную подписку на публикацию транзакций. Дополнительные сведения см. в статье [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
2.  На подписчике, выполните [sp_addpushsubscription_agent & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md). Укажите **@subscriber**, **@subscriber_db**, **@publication**, и учетные данные Windows, с которыми работает агент распространителя на подписчике **@job_name** и **@password**. Укажите описанные выше параметры синхронизации, определяющие расписание для задания агента распространителя, синхронизирующего подписку.  
  
#### Определение расписания синхронизации для подписки по запросу для публикации слиянием  
  
1.  Создайте подписку по запросу на публикацию слиянием. Дополнительные сведения см. в разделе [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
2.  На подписчике, выполните [sp_addmergepullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md). Укажите **@publisher**, **@publisher_db**, **@publication**, и учетные данные Windows, с которыми работает агент слияния на подписчике **@job_name** и **@password**. Укажите описанные выше параметры синхронизации, определяющие расписание для задания агента слияния, синхронизирующего подписку.  
  
#### Определение расписания синхронизации для принудительной подписки на публикацию слиянием  
  
1.  Создайте принудительную подписку на публикацию слиянием. Дополнительные сведения см. в статье [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
2.  На подписчике, выполните [sp_addmergepushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md). Укажите **@subscriber**, **@subscriber_db**, **@publication**, и учетные данные Windows, с которыми работает агент слияния на подписчике **@job_name** и **@password**. Укажите описанные выше параметры синхронизации, определяющие расписание для задания агента слияния, синхронизирующего подписку.  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 При выполнении репликации агент SQL Server производит планирование заданий для создания моментальных снимков и синхронизации подписок. Расписание заданий агента репликации может быть задано программным путем с помощью объектов RMO.  
  
> [!NOTE]  
>  При создании подписки и укажите значение **false** для **CreateSyncAgentByDefault** (поведение по умолчанию для подписок по запросу) задание агента не создается, и параметры расписания учитываются. В этом случае расписание синхронизации задается приложением. Дополнительные сведения см. в разделах [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md) и [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
#### Создание нового расписания агента репликации при создании принудительной подписки на публикацию транзакций  
  
1.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.TransSubscription> класс для создаваемой подписки. Дополнительные сведения см. в статье [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
2.  Перед вызовом метода <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>, задайте одно или несколько из следующих полей <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> свойство:  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> -Тип частоты (например, ежедневно или еженедельно), используемый при создании расписания для агента.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> — день недели, который запускается агент.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> — неделя конкретного месяца, когда запуск агента ежемесячный запуск.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> — число частотных единиц, которые происходят между синхронизациями.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> — Единица частоты, если агент запускается чаще, чем раз в день.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> -число единиц частоты между запусками агент запускается чаще, чем раз в день.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> — самое раннее время запуска агента в заданный день.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> — время последнего запуска агента в заданный день.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> — первый день, расписания агента.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> — последний день, расписания агента.  
  
    > [!NOTE]  
    >  Если не задать одно из этих свойств, будет использоваться значение по умолчанию.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> метод для создания подписки.  
  
#### Создание расписания агента репликации при создании подписки по запросу на публикацию транзакций  
  
1.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.TransPullSubscription> класс для создаваемой подписки. Дополнительные сведения см. в разделе [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
2.  Перед вызовом метода <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>, задайте одно или несколько из следующих полей <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> свойство:  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> -Тип частоты (например, ежедневно или еженедельно), используемого при создании расписания для агента.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> — день недели, который запускается агент.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> — неделя конкретного месяца, запланированное ежемесячный запуск агента.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> — число частотных единиц, которые происходят между синхронизациями.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> — Единица частоты, если агент запускается чаще, чем раз в день.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> -число единиц частоты между запусками агент запускается чаще, чем раз в день.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> — самое раннее время запуска агента в заданный день.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> — время последнего запуска агента в заданный день.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> — первый день, расписания агента.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> — последний день, расписания агента.  
  
    > [!NOTE]  
    >  Если не задать одно из этих свойств, будет использоваться значение по умолчанию.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> метод для создания подписки.  
  
#### Создание расписания агента репликации при создании подписки по запросу на публикацию слиянием  
  
1.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergePullSubscription> класс для создаваемой подписки. Дополнительные сведения см. в разделе [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md).  
  
2.  Перед вызовом метода <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>, задайте одно или несколько из следующих полей <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> свойство:  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> -Тип частоты (например, ежедневно или еженедельно), используемого при создании расписания для агента.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> — день недели, который запускается агент.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> — неделя конкретного месяца, запланированное ежемесячный запуск агента.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> — число частотных единиц, которые происходят между синхронизациями.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> — Единица частоты, если агент запускается чаще, чем раз в день.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> -число единиц частоты между запусками агент запускается чаще, чем раз в день.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> — самое раннее время запуска агента в заданный день.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> — время последнего запуска агента в заданный день.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> — первый день, расписания агента.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> — последний день, расписания агента.  
  
    > [!NOTE]  
    >  Если не задать одно из этих свойств, будет использоваться значение по умолчанию.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> метод для создания подписки.  
  
#### Создание расписания агента репликации при создании принудительной подписки на публикацию слиянием  
  
1.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergeSubscription> класс для создаваемой подписки. Дополнительные сведения см. в статье [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
2.  Перед вызовом метода <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>, задайте одно или несколько из следующих полей <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> свойство:  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> -Тип частоты (например, ежедневно или еженедельно), используемого при создании расписания для агента.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> — день недели, который запускается агент.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> — неделя конкретного месяца, запланированное ежемесячный запуск агента.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> — число частотных единиц, которые происходят между синхронизациями.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> — Единица частоты, если агент запускается чаще, чем раз в день.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> -число единиц частоты между запусками агент запускается чаще, чем раз в день.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> — самое раннее время запуска агента в заданный день.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> — время последнего запуска агента в заданный день.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> — первый день, расписания агента.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> — последний день, расписания агента.  
  
    > [!NOTE]  
    >  Если не задать одно из этих свойств, будет использоваться значение по умолчанию.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> метод для создания подписки.  
  
###  <a name="PShellExample"></a> Пример (объекты RMO)  
 В следующем примере производится создание принудительной подписки на публикацию слиянием, а также задается расписание синхронизации указанной подписки.  
  
 [!code-csharp[HowTo#rmo_CreateMergePushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepushsub)]  
  
## См. также:  
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)   
 [Синхронизация принудительной подписки](../../relational-databases/replication/synchronize-a-push-subscription.md)   
 [Синхронизация подписки по запросу](../../relational-databases/replication/synchronize-a-pull-subscription.md)   
 [Синхронизация данных](../../relational-databases/replication/synchronize-data.md)  
  
  