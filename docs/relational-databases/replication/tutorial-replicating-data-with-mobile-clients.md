---
title: Учебник. Настройка репликации между сервером и мобильными клиентами (репликация слиянием) | Документы Майкрософт
ms.custom: ''
ms.date: 04/03/2018
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: af673514-30c7-403a-9d18-d01e1a095115
caps.latest.revision: 24
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d9751b7adc3d2cd4169bcd6b3a174de720c05eb9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="tutorial-configure-replication-between-a-server-and-mobile-clients-merge"></a>Учебник. Настройка репликации между сервером и мобильными клиентами (репликация слиянием)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Репликация слиянием является хорошим решением проблемы перемещения данных между центральным сервером и мобильными клиентами, не имеющими постоянного подключения. С помощью мастеров репликации можно легко настроить и администрировать топологию репликации слиянием. В этом учебнике демонстрируется, как настроить топологию репликации для мобильных клиентов.  Дополнительные сведения о репликации слиянием см. в разделе [Обзор репликации слиянием](https://docs.microsoft.com/en-us/sql/relational-databases/replication/merge/merge-replication)
  
## <a name="what-you-will-learn"></a>Обзор учебника  
В этом учебнике используется репликация слиянием, чтобы опубликовать данные из центральной базы данных для одного или более мобильных пользователей так, что каждый пользователь получит уникальным образом фильтрованное подмножество данных. 

В этом учебнике рассматривается следующее.
> [!div class="checklist"]
> * Настройка издателя для репликации слиянием
> * Добавление мобильных устройств подписчика для публикации слиянием
> * Синхронизация подписки на публикацию слиянием
  
## <a name="prerequisites"></a>предварительные требования  
Этот учебник предназначен для пользователей, знакомых с основными операциями с базами данных, но имеющих ограниченный опыт работы с репликацией. Перед тем как приступить к работе с этим учебником, необходимо освоить [Учебник. Подготовка сервера к репликации](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md).  
  
Для работы с этим учебником в вашей системе должны быть установлены среда SQL Server Management Studio и следующие компоненты:  
  
-   На сервере-издателе (источник):  
  
    -   Любой выпуск SQL Server, кроме SQL Server Express или SQL Server Compact. Эти выпуски не могут быть издателями репликации.   
    -   Образец базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . В целях повышения безопасности образцы баз данных по умолчанию не устанавливаются.  
  
-   На сервере-подписчике (целевом):  
  
    -   Любой выпуск SQL Server, за исключением [!INCLUDE[ssEW](../../includes/ssew-md.md)]. [!INCLUDE[ssEW](../../includes/ssew-md.md)] не поддерживается публикацией, созданной в этом учебнике. 

- Установите [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).
- Установите выпуск [SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads).
- Скачайте [образцы баз данных AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases). Инструкции по восстановлению базы данных из копии в среде SSMS см. в разделе [Восстановление базы данных](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms).  
 
  
>[!NOTE]
> - Репликация не поддерживается на серверах SQL Server, которые отличаются друг от друга более чем на две версии. Дополнительные сведения см. в разделе [Поддерживаемые версии SQL в топологии репликации](https://blogs.msdn.microsoft.com/repltalk/2016/08/12/suppported-sql-server-versions-in-replication-topology/).
> - В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]необходимо подключиться к издателю и подписчику с помощью имени входа, которое является членом предопределенной роли сервера **sysadmin** . Дополнительные сведения о роли sysadmin см. в разделе [Роли уровня сервера](https://docs.microsoft.com/en-us/sql/relational-databases/security/authentication-access/server-level-roles).  
  
  
**Предполагаемое время для выполнения заданий данного учебника: 60 минут.**  
  
## <a name="configure-a-publisher-for-merge-replication"></a>Настройка издателя для репликации слиянием
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
В этом разделе с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] создается публикация слиянием с целью публикации подмножества таблиц **Employee**, **SalesOrderHeader** и **SalesOrderDetail** в образце базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Эти таблицы фильтруются с помощью параметризованных фильтров строк, так что каждая подписка содержит уникальную секцию данных. Также в список доступа к публикации добавляется имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , используемое агентом слияния.  
  
### <a name="create-merge-publication-and-define-articles"></a>Создание публикации слиянием и определение статей  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2. Запустите **агент SQL Server**. Для этого щелкните правой кнопкой мыши в **обозревателе объектов** и выберите **Запустить**. Если агент не запускается, это необходимо сделать вручную с помощью **диспетчера конфигурации SQL Server Configuration**.  
3. Разверните папку **Репликация**, щелкните правой кнопкой мыши элемент **Локальные публикации** и выберите пункт **Создать публикацию**.  Будет запущен мастер настройки публикации:  

    ![Запуск мастер создания публикации](media/tutorial-replicating-data-between-continuously-connected-servers/newpublication.png)
  
3.  На странице "База данных публикации" выберите [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] и нажмите кнопку **Далее**. 

      
4.  На странице "Тип публикации" выберите **Публикация слиянием**и нажмите кнопку **Далее**.  
    A. На странице "Типы подписчиков" убедитесь, что выбрана только [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или более поздняя версия, и нажмите кнопку **Далее**: 

    ![Репликация слиянием](media/tutorial-replicating-data-with-mobile-clients/mergerpl.png)
  
   
6.  На странице "Статьи" разверните узел **Таблицы** и выберите следующие три таблицы: **Employee**, **SalesOrderHeader** и **SalesOrderDetail**. Нажмите кнопку **Далее**:  

    ![Слияние статей](media/tutorial-replicating-data-with-mobile-clients/mergearticles.png)

    >[!NOTE]
    > Таблица Employee содержит столбец (OrganizationNode) с типом данных hierarchyid, который поддерживается для репликации только в SQL 2017. Если вы используете сборку ниже версии SQL 2017, в нижней части экрана появится сообщение с уведомлением о риске потери данных при использовании этого столбца для двусторонней репликации. В рамках этого учебника данное сообщение можно игнорировать. Тем не менее, если вы не используете поддерживаемую сборку в рабочей среде, этот тип данных не должен участвовать в репликации. Дополнительные сведения о репликации типа данных hierarchyid см. в разделе [Использование столбцов Hierarchyid в репликации](https://docs.microsoft.com/en-us/sql/t-sql/data-types/hierarchyid-data-type-method-reference#using-hierarchyid-columns-in-replicated-tables)
    
  
7.  На странице "Фильтрация строк таблицы" выберите **Добавить**, а затем щелкните **Добавить фильтр**.  
  
8.  В диалоговом окне **Добавить фильтр** выберите **Employee (HumanResources)** в поле **Выбрать таблицу для фильтрации**. Щелкните столбец **LoginID**, щелкните стрелку вправо, чтобы добавить столбец в предложение WHERE фильтрующего запроса, и измените предложение WHERE следующим образом:  
  
    ```sql 
    WHERE [LoginID] = HOST_NAME()  
    ```  
  
    A. Щелкните элемент **Строка из этой таблицы будет отправлена только одной подписке** и нажмите кнопку **ОК**:  
 
    ![Добавление фильтра](media/tutorial-replicating-data-with-mobile-clients/mergeaddfilter.png)

    
  
10. На странице **Фильтрация строк таблицы** выберите **Employee (Human Resources)**, нажмите **Добавить**, а затем **Добавить соединение для расширения выбранного фильтра**.  
  
    A. В диалоговом окне **Добавление соединения** выберите **Sales.SalesOrderHeader** в поле **Соединяемая таблица**. Выберите **Записать инструкцию соединения вручную** и завершите инструкцию соединения следующим образом:  
  
    ```sql  
    ON [Employee].[BusinessEntityID] =  [SalesOrderHeader].[SalesPersonID] 
    ```  
  
    Б. В поле **Укажите параметры соединения** выберите **Уникальный ключ**, а затем нажмите кнопку **ОК**:

    ![Добавление соединения в фильтр](media/tutorial-replicating-data-with-mobile-clients/mergeaddjoin.png)

  
13. На странице "Фильтрация строк таблицы" выберите **SalesOrderHeader**, щелкните **Добавить** и выберите **Добавить соединение для расширения выбранного фильтра**.  
  
    A. В диалоговом окне **Добавление соединения** выберите **Sales.SalesOrderDetail** в поле **Соединяемая таблица**.    
    Б. Выберите **Использовать конструктор для создания инструкции**.  
    в. В поле **Предварительный просмотр** убедитесь, что инструкция соединения выглядит следующим образом:  
  
    ```sql  
    ON [SalesOrderHeader].[SalesOrderID] = [SalesOrderDetail].[SalesOrderID] 
    ```  
  
    г. В поле **Укажите параметры соединения** выберите **Уникальный ключ**, а затем нажмите кнопку **ОК**. Нажмите кнопку **Далее**: 

       ![Соединение таблиц заказов на продажу](media/tutorial-replicating-data-with-mobile-clients/joinsalestables.png)
  
21. Установите флажок **Создать моментальный снимок немедленно**, снимите флажок **Запланировать запуск агента моментальных снимков в следующее время** и нажмите кнопку **Далее**:  

    ![Немедленное создание моментального снимка](media/tutorial-replicating-data-with-mobile-clients/snapshotagent.png)
  
22. На странице "Безопасность агента" щелкните **Настройки безопасности**, введите <*имя_кмопьютера_издателя>***\repl_snapshot** в поле **Учетная запись процесса**, укажите пароль для учетной записи и нажмите кнопку **ОК**. Нажмите кнопку **Далее**:  

    ![Безопасность агента моментальных снимков](media/tutorial-replicating-data-with-mobile-clients/snapshotagentsecurity.png)
  
23. На странице **Завершение работы мастера** введите **AdvWorksSalesOrdersMerge** в поле **Имя публикации** и нажмите кнопку **Готово**:  

    ![Присвоение имени репликации слиянием](media/tutorial-replicating-data-with-mobile-clients/namemergerepl.png)
  
24. По завершении создания публикации нажмите кнопку **Закрыть**. В узле **Репликация** в **обозревателе объектов** щелкните правой кнопкой мыши элемент **Локальные публикации** и выберите **Обновить**, чтобы просмотреть новую репликацию слиянием.  
  
### <a name="to-view-the-status-of-snapshot-generation"></a>Просмотр состояния создания моментального снимка  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера и папку **Репликация** .  
  
2.  В папке "Локальные публикации" щелкните правой кнопкой мыши публикацию **AdvWorksSalesOrdersMerge** и выберите пункт **Просмотр состояния агента моментальных снимков**:  

    ![Просмотр состояния агента моментальных снимков](media/tutorial-replicating-data-with-mobile-clients/viewsnapshotagentstatus.png)
  
3.  Отобразится текущее состояние задания агента моментальных снимков для публикации. Перед тем как перейти к следующему занятию, убедитесь, что задание моментального снимка выполнено успешно.  
  
### <a name="to-add-the-merge-agent-login-to-the-pal"></a>Добавление имени входа агента слияния в список доступа к публикации  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера и папку **Репликация** .  
  
2.  В папке "Локальные публикации" щелкните правой кнопкой мыши публикацию **AdvWorksSalesOrdersMerge** и выберите пункт **Свойства**.  
  
    A. Выберите страницу **Список доступа к публикации** и нажмите кнопку **Добавить**. 
  
    Б. В диалоговом окне "Добавление доступа к публикации" выберите <*имя_компьютера_издателя>***\repl_merge** и нажмите кнопку **ОК**. Нажмите кнопку **ОК**: 

    ![Список доступа к публикации слиянием](media/tutorial-replicating-data-with-mobile-clients/mergepal.png) 

  
**См. также**:  
[Фильтрация опубликованных данных](../../relational-databases/replication/publish/filter-published-data.md)  
[Параметризованные фильтры строк](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)  
[Определение статьи](../../relational-databases/replication/publish/define-an-article.md)  
  
  
## <a name="creating-a-subscription-to-the-merge-publication"></a>Создание подписки на публикацию слиянием
В этом разделе описывается добавление подписки к ранее созданной публикации слиянием. В этом учебнике используется удаленный подписчик (NODE2\SQL2016). Затем будут установлены разрешения на базу данных подписки и вручную будет сформирован моментальный снимок отфильтрованных данных для новой подписки.   
  
### <a name="add-a-subscriber-for-merge-publication"></a>Добавление подписчика для публикации слиянием
  
1.  Подключитесь к подписчику в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и раскройте узел сервера. Разверните папку **Репликация**, щелкните правой кнопкой мыши папку **Локальные подписки** и выберите пункт **Создать подписку**. Откроется мастер создания подписки:

    ![Создать подписку](media/tutorial-replicating-data-with-mobile-clients/newsub.png)
  
2.  На странице **Публикация** из списка **Издатель** выберите **Найти издатель SQL Server**.  
  
    A. В диалоговом окне **Соединение с сервером** введите имя экземпляра издателя в поле **Имя сервера**, а затем щелкните **Подключиться**: 

    ![Добавление издателя в публикацию](media/tutorial-replicating-data-with-mobile-clients/publication.png)
  
4.  Щелкните элемент **AdvWorksSalesOrdersMerge**, а затем нажмите кнопку **Далее**.  
  
5.  На странице "Расположение агента слияния" щелкните **Выполнять каждый агент на своем подписчике** и нажмите кнопку **Далее**:  

    ![Подписка по запросу](media/tutorial-replicating-data-with-mobile-clients/pullsub.png)
  
6.  На странице "Подписчики" выберите имя экземпляра сервера подписчика и в списке **База данных подписки** выберите **Новая база данных**.  
  
    A. В диалоговом окне **Новая база данных** введите **SalesOrdersReplica** в поле **Имя базы данных**, нажмите кнопку **ОК**, а затем кнопку **Далее**: 

    ![Добавление базы данных для подписчика](media/tutorial-replicating-data-with-mobile-clients/addsubdb.png)
  
8.  На странице "Безопасность агента слияния" нажмите кнопку с многоточием (**…**), введите <*имя_компьютера_подписчика>***\repl_merge** в поле **Учетная запись процесса**, введите пароль для этой учетной записи, нажмите кнопку **ОК**, нажмите кнопку **Далее** и еще раз кнопку **Далее**:  

    ![Безопасность агента слияния](media/tutorial-replicating-data-with-mobile-clients/mergeagentsecurity.png)

9. В разделе **Расписание синхронизации**, присвойте параметру **Расписание агента** значение **Выполнение по требованию**. Нажмите кнопку **Далее**:  

    ![Расписание синхронизации](media/tutorial-replicating-data-with-mobile-clients/mergesyncschedule.png)
  
9. На странице "Инициализация подписок" выберите из списка **Инициализировать, когда** пункт **При первой синхронизации**, нажмите кнопку **Далее**, а затем снова кнопку **Далее**: 

    ![Первая синхронизация](media/tutorial-replicating-data-with-mobile-clients/firstsync.png)

10. На странице "Значения HOST_NAME" введите значение **adventure-works\pamela0** в поле **Значение HOST_NAME** и нажмите кнопку **Готово**:  

    ![Имя узла](media/tutorial-replicating-data-with-mobile-clients/hostname.png)
  
11. Нажмите снова кнопку **Готово** и после создания подписки нажмите кнопку **Закрыть**.  

### <a name="setting-server-permissions-at-the-subscriber"></a>Установка разрешений сервера на подписчике  
  
1.  Подключитесь к подписчику в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], разверните узел **Безопасность**, щелкните правой кнопкой мыши **Имена для входа**, а затем выберите пункт **Создать имя для входа**.  
  
    A. На странице **Общие** выберите **Найти**, введите <*имя_компьютера_подписчика>***\repl_merge** в поле **Введите имя объекта**, выберите **Проверить имена** и нажмите кнопку **ОК**: 
    
    ![Вход в подписчик](media/tutorial-replicating-data-with-mobile-clients/sublogin.png)
  
1. На странице **Сопоставление пользователей** выберите базу данных **SalesOrdersReplica** и роль **db_owner**.  На странице **Защищаемые объекты** предоставьте разрешение "Явное" для элемента **Изменение трассировки**. Нажмите кнопку **ОК**:

    ![Установка имени для входа в качестве владельца базы данных на подписчике](media/tutorial-replicating-data-with-mobile-clients/setdbo.png)
  
### <a name="to-create-the-filtered-data-snapshot-for-the-subscription"></a>Создание моментального снимка отфильтрованных данных подписки  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера и папку **Репликация** .  
  
2.  В папке **Локальные публикации** щелкните правой кнопкой мыши публикацию **AdvWorksSalesOrdersMerge** и выберите пункт **Свойства**.  
   
    A. Выберите страницу **Секции данных** и нажмите кнопку **Добавить**.   
    Б. В диалоговом окне **Добавление секции данных** введите значение **adventure-works\pamela0** в поле **Значение HOST_NAME** и нажмите кнопку **ОК**.  
    в. Выберите добавленную секцию, щелкните **Создать выбранные моментальные снимки** и нажмите кнопку **ОК**: 

    ![Добавление секции](media/tutorial-replicating-data-with-mobile-clients/partition.png)
  
  
**См. также**:  
[Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  
[Создание подписки по запросу](../../relational-databases/replication/create-a-pull-subscription.md)  
[Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  

## <a name="synchronize-the-subscription-to-the-merge-publication"></a>Синхронизация подписки на публикацию слиянием

В этом разделе будет запущен агент слияния для инициализации подписки с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Эта процедура также используется для синхронизации с издателем.   
  
### <a name="to-start-synchronization-and-initialize-the-subscription"></a>Запуск синхронизации и инициализация подписки  
  
1.  Установите подключение к подписчику в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
2. Убедитесь, что **агент SQL Server** запущен. Если это не так, запустите **агент SQL Server**. Для этого щелкните правой кнопкой мыши в **обозревателе объектов** и выберите **Запустить**. Если агент не запускается, это необходимо сделать вручную с помощью **диспетчера конфигурации SQL Server Configuration**. 
  
2.  Разверните узел **Репликация**. В папке **Локальные подписки** щелкните правой кнопкой мыши подписку в базе данных **SalesOrdersReplica** и выберите пункт **Просмотр состояния синхронизации**.  
  
    A. Нажмите кнопку **Запустить**, чтобы инициализировать подписку: 

    ![Состояние синхронизации](media/tutorial-replicating-data-with-mobile-clients/mergesyncstatus.png)
    
  
  
### <a name="next-steps"></a>Next Steps  
Вы успешно настроили издатель и подписчик для репликации слиянием.  Можно вставить, обновить или удалить данные из таблицы **SalesOrderHeader** или **SalesOrderDetail** на стороне издателя или подписчика, повторить эту процедуру, когда доступно соединение сети, для синхронизации данных между издателем и подписчиком, после чего выполнить запросы к таблице **SalesOrderHeader** или **SalesOrderDetail** на другом сервере, чтобы просмотреть реплицированные изменения.  
  
**См. также**:   
[Инициализация подписки с помощью моментального снимка](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
[Синхронизация данных](../../relational-databases/replication/synchronize-data.md)  
[Синхронизация подписки по запросу](../../relational-databases/replication/synchronize-a-pull-subscription.md)  
  
  
  
  
