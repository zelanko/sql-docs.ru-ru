---
title: Учебник. Настройка репликации между двумя полностью подключенными серверами (репликация транзакций) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- tutorials [SQL Server replication]
- replication [SQL Server], tutorials
- wizards [SQL Server replication]
ms.assetid: 7b18a04a-2c3d-4efe-a0bc-c3f92be72fd0
caps.latest.revision: 21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: de374f4372f62741ff3c49a9433cf339cecf3d26
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="tutorial-configure-replication-between-two-fully-connected-servers-transactional"></a>Учебник. Настройка репликации между двумя полностью подключенными серверами (репликация транзакций)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Репликация транзакций представляет собой хорошее решение проблемы перемещения данных между постоянно подключенными серверами. С помощью мастера репликации можно легко настроить и администрировать топологию репликации. В этом учебнике рассказывается о настройке топологии репликации транзакций для постоянно подключенных серверов. Дополнительные сведения о том, как работает репликация транзакций, см. в разделе [Общие сведения о репликации транзакций](https://docs.microsoft.com/en-us/sql/relational-databases/replication/transactional/transactional-replication). 
  
## <a name="what-you-will-learn"></a>Обзор учебника  
В этом учебнике рассказывается о публикации данных из одной базы данных в другую при помощи репликации транзакций. 

В этом учебнике рассматривается следующее.
> [!div class="checklist"]
> * Создание издателя посредством репликации транзакций
> * Создание подписчика для издателя транзакций
> * Проверка подписки и измерение задержки
> * Методы устранения неполадок
  
  
## <a name="prerequisites"></a>предварительные требования  
Этот учебник предназначен для пользователей, знакомых с основными операциями с базами данных, но имеющих ограниченный опыт в работе с репликацией. Для работы с этим учебником требуется завершить работу с предыдущим учебником, [Подготовка сервера для репликации](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md).  
  
Для работы с этим учебником в вашей системе должны быть установлены среда SQL Server Management Studio (SSMS) и следующие компоненты:  
  
-   На сервере-издателе (источник):  
  
    -   Любой выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], кроме SQL Server Express или SQL Compact. Эти выпуски не могут быть издателями репликации.   
    -   [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] . В целях повышения безопасности образцы баз данных по умолчанию не устанавливаются.  
  
-   На сервере-подписчике (целевом):  
  
    -   Любой выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], за исключением [!INCLUDE[ssEW](../../includes/ssew-md.md)]. [!INCLUDE[ssEW](../../includes/ssew-md.md)] не может быть подписчиком в репликации транзакций.  
  
- Установите [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).
- Установите выпуск [SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads).
- Скачайте [образцы баз данных AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases). Инструкции по восстановлению базы данных из копии в среде SSMS см. в разделе [Восстановление базы данных](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms). 
 
>[!NOTE]
> - Репликация не поддерживается на серверах SQL Server, которые отличаются друг от друга более чем на две версии. Дополнительные сведения см. в разделе [Поддерживаемые версии SQL в топологии репликации](https://blogs.msdn.microsoft.com/repltalk/2016/08/12/suppported-sql-server-versions-in-replication-topology/).
> - В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]необходимо подключиться к издателю и подписчику с помощью имени входа, которое является членом предопределенной роли сервера **sysadmin** . Дополнительные сведения о роли sysadmin см. в разделе [Роли уровня сервера](https://docs.microsoft.com/en-us/sql/relational-databases/security/authentication-access/server-level-roles).  
  
  
**Предполагаемое время для выполнения заданий данного учебника: 60 минут.**  
  
## <a name="configure-the-publisher-for-transactional-replication"></a>Настройка издателя для репликации транзакций
В этом разделе с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] создается публикация транзакций с целью публикации фильтрованного подмножества таблицы **Product** из образца базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Также в список доступа к публикации (PAL) добавляется имя входа SQL Server, используемое агентом распространителя. Перед началом работы с этим учебником необходимо завершить работу с предыдущим учебником, [Подготовка сервера к репликации](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md).


### <a name="create-a-publication-and-define-articles"></a>Создание публикации и определение статей
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2. Щелкните правой кнопкой мыши элемент **Агент SQL Server** и выберите пункт **Запустить**. Прежде чем приступить к созданию публикации, необходимо запустить агент SQL Server. Если агент не запущен, это необходимо сделать вручную с помощью **диспетчера конфигурации SQL Server Configuration**. 
3. Разверните папку **Репликация**, щелкните правой кнопкой мыши папку **Локальные публикации** и выберите пункт **Создать публикацию**.  Будет запущен мастер настройки публикации:  

    ![Создание публикации](media/tutorial-replicating-data-between-continuously-connected-servers/newpublication.png)
  
  
3. На странице "База данных публикации" выберите [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] и нажмите кнопку **Далее**.  
  
4. На странице "Тип публикации" выберите **Публикация транзакций** и нажмите кнопку **Далее**:  

    ![репликация транзакций](media/tutorial-replicating-data-between-continuously-connected-servers/tranrepl.png)
  
5. На странице "Статьи" разверните узел **Таблицы** и установите флажок **Продукт**. Затем разверните узел **Продукт** и снимите флажки **ListPrice** и **StandardCost**. Нажмите кнопку **Далее**:  

    ![Статьи для публикации](media/tutorial-replicating-data-between-continuously-connected-servers/replarticles.png)
  
6. На странице "Фильтр строк таблицы" нажмите кнопку **Добавить**.   
  
7. В диалоговом окне **Добавление фильтра** щелкните столбец **SafetyStockLevel**, щелкните стрелку вправо, чтобы добавить столбец в предложение WHERE инструкции фильтра запроса. После этого вручную введите следующий модификатор предложения WHERE:  
  
    ```sql  
    WHERE [SafetyStockLevel] < 500  
    ```
  
    ![Инструкция фильтра](media/tutorial-replicating-data-between-continuously-connected-servers/filter.png)
  
8. Нажмите кнопку **ОК**, а затем кнопку **Далее**.  
  
9. Установите флажок **Создать моментальный снимок немедленно и обеспечить доступ к нему для инициализации подписок** и нажмите кнопку **Далее**:  

    ![агент моментальных снимков](media/tutorial-replicating-data-between-continuously-connected-servers/snapshot.png)
  
10. На странице "Безопасность агента" снимите флажок **Использовать настройки безопасности агента моментальных снимков** .   
  
    A. Для агента моментальных снимков щелкните **Настройки безопасности**, введите <*имя_компьютера_издателя>***\repl_snapshot** в поле **Учетная запись процесса**, укажите пароль для этой учетной записи и нажмите кнопку **ОК**:  

    ![Безопасность агента моментальных снимков](media/tutorial-replicating-data-between-continuously-connected-servers/snapshotagentsecurity.png)
  
12. Повторите предыдущий шаг, чтобы установить <*имя_компьютера_издателя*>**\repl_logreader** в качестве учетной записи процесса для агента чтения журнала, а затем нажмите кнопку **ОК**:  

    ![Безопасность агента чтения журнала](media/tutorial-replicating-data-between-continuously-connected-servers/logreaderagentsecurity.png)   

  
13. На странице "Завершение работы мастера" введите **AdvWorksProductTrans** в поле **Имя публикации** и нажмите кнопку **Готово**:  

    ![Название публикации](media/tutorial-replicating-data-between-continuously-connected-servers/advworksproducttrans.png)
  
14. После создания публикации нажмите кнопку **Закрыть**, чтобы закрыть мастер. 

    Если при попытке создать публикацию обнаруживается, что не запущен агент SQL Server, может возникнуть следующая ошибка. Это указывает на то, что публикация была успешно создана, однако при этом не удалось запустить агент моментальных снимков. В этом случае необходимо запустить агент SQL Server, а затем вручную запустить агент моментальных снимков. Соответствующие инструкции приводятся в следующем разделе: 

    ![Ошибка запуска агента моментальных снимков](media/tutorial-replicating-data-between-continuously-connected-servers/snapshotagenterror.png)
    
  
### <a name="to-view-the-status-of-snapshot-generation"></a>Просмотр состояния создания моментального снимка  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера и папку **Репликация** .  
  
2.  В папке **Локальные публикации** щелкните правой кнопкой мыши публикацию **AdvWorksProductTrans** и выберите пункт **Просмотр состояния агента моментальных снимков**:  

    ![Состояние агента моментальных снимков](media/tutorial-replicating-data-between-continuously-connected-servers/viewsnapshot.png)
  
3.  Отобразится текущее состояние задания агента моментальных снимков для публикации. Перед тем как перейти к следующему разделу, убедитесь, что задание моментального снимка выполнено успешно.
          
    Если агент SQL Server не был запущен при первичном создании публикации, в **состоянии агента моментальных снимков** для публикации будет указано, что он никогда не запускался. В таком случае выберите **Запустить**, чтобы запустить агент моментальных снимков: 

       ![Запуск агента моментальных снимков](media/tutorial-replicating-data-between-continuously-connected-servers/startsnapshotagent.png)
     
       Если отображается сообщение об ошибке, ознакомьтесь с разделом [Устранение неполадок с агентом моментальных снимков](#troubleshoot-erros-with-snapshot-agent). 

  
### <a name="to-add-the-distribution-agent-login-to-the-pal"></a>Добавление имени входа агента распространителя в список доступа к публикации  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера и папку **Репликация** .  
  
2.  В папке **Локальные публикации** щелкните правой кнопкой мыши публикацию **AdvWorksProductTrans** и выберите пункт **Свойства**.  Откроется диалоговое окно **Свойства публикации** .    
  
    A. Выберите страницу **Список доступа к публикации** и нажмите кнопку **Добавить**.  
    Б. В диалоговом окне **Добавление доступа к публикации** выберите *<имя_компьютера_издателя>***\repl_distribution** и нажмите кнопку **ОК**. Нажмите кнопку **ОК**:

   
   ![Добавление имени для входа в список доступа к публикации](media/tutorial-replicating-data-between-continuously-connected-servers/tranreplproperties.png)

**См. также**:  
[Основные понятия программирования репликации](../../relational-databases/replication/concepts/replication-programming-concepts.md)  
  

## <a name="create-a-subscription-to-the-transactional-publication"></a>Создание подписки на публикацию транзакций
В этом разделе описывается добавление подписчика к ранее созданной публикации. В этом учебнике используется удаленный подписчик (NODE2\SQL2016), однако при необходимости подписку для издателя можно также добавить локально. 

### <a name="to-create-the-subscription"></a>Создание подписки  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера и папку **Репликация** .  
  
2.  В папке **Локальные публикации** щелкните правой кнопкой мыши публикацию **AdvWorksProductTrans** и выберите команду **Создать подписку**.  Откроется мастер создания подписки: 
 
    ![Создать подписку](media/tutorial-replicating-data-between-continuously-connected-servers/newsub.png)     
  
3.  На странице "Публикация" выберите публикацию **AdvWorksProductTrans** и нажмите кнопку **Далее**:  

    ![Выбор издателя транзакций](media/tutorial-replicating-data-between-continuously-connected-servers/selectpub.png)
  
4.  На странице "Расположение агента распространителя" установите флажок **Выполнять все агенты на распространителе** и нажмите кнопку **Далее**.  Дополнительные сведения о подписках см. в статье [Подписка на публикации](https://docs.microsoft.com/en-us/sql/relational-databases/replication/subscribe-to-publications):

    ![Выполнение агентов на распространителе](media/tutorial-replicating-data-between-continuously-connected-servers/runagentsatdist.png)
  
5.  На странице "Подписчики", если имя экземпляра подписчика не отображается, выберите пункт **Добавить подписчик**, а затем выберите **Добавить подписчик SQL Server** из раскрывающегося списка. Откроется диалоговое окно **Соединение с сервером**. Введите имя экземпляра подписчика, а затем выберите **Подключиться**.  
    
    A. После добавления подписчика установите флажок рядом с именем его экземпляра. Затем выберите пункт **Создать базу данных** в разделе **База данных подписки**:   

  ![Добавление сервера подписчика](media/tutorial-replicating-data-between-continuously-connected-servers/addsub.png)

7. Откроется диалоговое окно **Создание базы данных**. Введите **ProductReplica** в поле **Имя базы данных**, нажмите кнопку **ОК** и затем кнопку **Далее**: 
  
    ![Реплика базы данных продуктов](media/tutorial-replicating-data-between-continuously-connected-servers/productreplica.png)
  
8.  В диалоговом окне **Безопасность агента распространителя** нажмите кнопку с многоточием (**…**). Введите <*имя_компьютера_издателя>***\repl_distribution** в поле **Учетная запись процесса**, введите пароль этой учетной записи, нажмите кнопку **ОК** и затем кнопку **Далее**:

    ![Добавление учетной записи распространителя](media/tutorial-replicating-data-between-continuously-connected-servers/adddistaccount.png)
  
9. Нажмите кнопку **Готово**, чтобы принять значения по умолчанию на оставшихся страницах и завершить работу мастера.  
  
### <a name="setting-database-permissions-at-the-subscriber"></a>Установка разрешений базы данных на подписчике  
  
1.  Подключитесь к подписчику в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], разверните узел **Безопасность**, щелкните правой кнопкой мыши **Имена для входа**, а затем выберите пункт **Создать имя для входа**.     
  
    A. На странице **Общие** в разделе **Имя для входа** выберите **Найти** и добавьте имя для входа для <*имя_компьютера_подписчика>***\repl_distribution**.
    Б. На странице **Сопоставления пользователей** предоставьте имени для входа разрешения **db_owner** для базы данных **ProductReplica**: 

    ![Вход в подписчик](media/tutorial-replicating-data-between-continuously-connected-servers/loginforsub.png)

2. Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно **Создание имени для входа**. 

  
### <a name="to-view-the-synchronization-status-of-the-subscription"></a>Просмотр состояния синхронизации подписки  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера и папку **Репликация** .  
  
2.  В папке **Локальные публикации** разверните публикацию **AdvWorksProductTrans**, щелкните правой кнопкой мыши подписку в базе данных **ProductReplica** и выберите пункт **Просмотр состояния синхронизации**. Отобразится текущее состояние синхронизации подписки:  
    ![Просмотр состояния синхронизации](media/tutorial-replicating-data-between-continuously-connected-servers/viewsyncstatus.png)
3.  Если подписка не отображается под публикацией **AdvWorksProductTrans**, нажмите клавишу F5 для обновления списка.  
  
**См. также**:  
[Инициализация подписки с помощью моментального снимка](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
[Создание принудительной подписки](../../relational-databases/replication/create-a-push-subscription.md)  
[Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  

## <a name="measuring-replication-latency"></a>Измерение задержки репликации
В этом разделе необходимо использовать трассировочные токены, чтобы проверить выполнение репликации изменений и определить задержку. Задержка определяет время, необходимое для отображения в подписчике изменений, выполненных в издателе.
  
1. Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], разверните узел сервера, щелкните правой кнопкой мыши папку **Репликация** и выберите пункт **Запустить монитор репликации**:

    ![Запуск монитора репликации](media/tutorial-replicating-data-between-continuously-connected-servers/launchreplmonitor.png)

2. Разверните группу издателей на левой панели, затем экземпляр издателя и выберите публикацию **AdvWorksProductTrans**.  
  
    A. Откройте вкладку **Трассировочные токены**.  
    Б. Выберите команду **Вставить трассировочный токен**.    
    в. Просмотрите затраченное время для трассировочного маркера в следующих столбцах: **От издателя к распространителю**, **От распространителя к подписчику**, **Общая задержка**. Значение **Ожидание** указывает на то, что токен еще не достиг указанной точки:


   ![Трассировочный токен](media/tutorial-replicating-data-between-continuously-connected-servers/tracertoken.png)


**См. также**   
[Измерение задержки и проверка правильности соединений для репликации транзакций](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)

## <a name="error-troubleshooting-methodology"></a>Методы устранения неполадок
В этом разделе описывается порядок устранения основных ошибок синхронизации, связанных с репликацией. Обратите внимание, что в этом разделе описывается переход между компонентами репликации в целях устранения неполадок. Однако в реальности возникающие ошибки могут отличаться от описываемых здесь и в таких случаях будут требовать другого решения. В таком случае требуется выполнить дополнительные действия по устранению неполадок, которые не описываются в этом учебнике. 


### <a name="troubleshoot-errors-with-snapshot-agent"></a>Устранение неполадок с агентом моментальных снимков
**Агент моментальных снимков** создает моментальный снимок и записывает его в указанную папку. 

1. Чтобы просмотреть состояние агента моментальных снимков, разверните узел **Локальные публикации** для репликации, щелкните правой кнопкой мыши репликацию **AdvWorksProductTrans** >  и выберите **Просмотр состояния агента моментальных снимков**. 
2. Если в **состоянии агента моментальных снимков** присутствует сообщение об ошибке, дополнительные сведения можно просмотреть в журнале заданий **Агент моментальных снимков**. Для доступа к этому журналу разверните узел **Агент SQL Server** в **обозревателе объектов** и откройте элемент **Монитор активности заданий**. 

    A. Выполните сортировку по **категории** и определите **агент моментальных снимков** по категории "REPL: моментальный снимок". 

    Б. Щелкните правой кнопкой мыши элемент **Агент моментальных снимков** и выберите пункт **Просмотреть журнал**: 

   ![Журнал агента моментальных снимков](media/tutorial-replicating-data-between-continuously-connected-servers/snapshotagenthistory.png)
    
1. В окне **Журнал агента моментальных снимков** выберите соответствующую запись журнала. Как правило, она располагается за одну или две строки *до* записи с сообщением об ошибке (ошибки обозначаются красным значком X).  Ознакомьтесь с текстом сообщения в поле, расположенном под журналами: 

    ![Отказ в доступе к агенту моментальных снимков](media/tutorial-replicating-data-between-continuously-connected-servers/snapshotaccessdenied.png)

        The replication agent had encountered an exception.
        Exception Message: Access to path '\\node1\repldata.....' is denied.


  Если в Windows неправильно настроены разрешения для папки моментальных снимков, для **агента моментальных снимков** будет отображаться ошибка "Доступ запрещен". Вам необходимо проверить разрешения для учетной записи <*имя_компьютера_издателя>***\repl_snapshot** на папку repldata. Дополнительные сведения см. в разделе [Создание ресурса для папки моментальных снимков и настройка разрешений](tutorial-preparing-the-server-for-replication.md#create-a-share-for-the-snapshot-folder-and-assign-permissions).

### <a name="troubleshoot-errors-with-log-reader-agent"></a>Устранение неполадок с агентом чтения журнала
**Агент чтения журнала** подключается к базе данных издателя и просматривает журнал транзакций для всех транзакций, которые помечены "для репликации". После этого агент добавляет эти транзакции в базу данных **распространителя**. 

1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], разверните узел сервера, щелкните правой кнопкой мыши папку **Репликация** и выберите пункт **Запустить монитор репликации**:  

    ![Запуск монитора репликации](media/tutorial-replicating-data-between-continuously-connected-servers/launchreplmonitor.png)
  
    Дополнительные сведения о запуске монитора репликации см. в разделе ![Монитор репликации](media/tutorial-replicating-data-between-continuously-connected-servers/replmonitor.png) 
   
2. Наличие красного значка X свидетельствует о том, что публикация не синхронизируется. Разверните узел **Мои издатели** в левой части, а затем соответствующий сервер издателя.  
  
3.  Выберите публикацию **AdvWorksProductTrans** слева и проверьте наличие красного значка X на одной из вкладок, чтобы определить место возникновения проблемы. В этом случае красный значок X находится на вкладке **Агенты**, что свидетельствует об ошибке одного из выполняющихся агентов: 

    ![Ошибка агента](media/tutorial-replicating-data-between-continuously-connected-servers/agenterror.png)

4. Перейдите на вкладку **Агенты**, чтобы определить, какой агент является источником ошибки: 

    ![Ошибка агента чтения журнала](media/tutorial-replicating-data-between-continuously-connected-servers/logreaderagentfailure.png)


5. В этом представлении показаны **агент моментальных снимков** и **агент чтения журнала**. Рядом с **агентом чтения журнала** отображается красный значок X, что свидетельствует о возникшей в нем ошибке. Дважды щелкните строку с сообщением об ошибке (в этом случае строку **Агент чтения журнала**). Откроется **журнал** выбранного агента, то есть в этом случае журнал **агента чтения журнала**. В нем будут представлены более подробные сведения об ошибке: 
    
    ![Ошибка агента чтения журнала](media/tutorial-replicating-data-between-continuously-connected-servers/logreadererror.png)

       Status: 0, code: 20011, text: 'The process could not execute 'sp_replcmds' on 'NODE1\SQL2016'.'.
       The process could not execute 'sp_replcmds' on 'NODE1\SQL2016'.
       Status: 0, code: 15517, text: 'Cannot execute as the database principal because the principal "dbo" does not exist, this type of principal cannot be impersonated, or you do not have permission.'.
       Status: 0, code: 22037, text: 'The process could not execute 'sp_replcmds' on 'NODE1\SQL2016'.'.        

6. Указанная выше ошибка обычно возникает при неправильной настройке владельца базы данных публикации. Как правило, это происходит при восстановлении базы данных. Чтобы убедиться в этом, разверните узел **Базы данных** в **обозревателе объектов**, щелкните правой кнопкой мыши элемент **AdventureWorks2012** >  и выберите пункт **Свойства**. На странице **Файлы** проверьте наличие владельца. Если это поле пусто, скорее всего это и будет являться причиной проблемы: 

    ![Свойства базы данных](media/tutorial-replicating-data-between-continuously-connected-servers/dbproperties.png)

7. Если поле владельца на странице **Файлы** пусто, откройте **Новое окно запроса** в контексте базы данных **AdventureWorks2012**. Выполните следующий фрагмент кода T-SQL:

    ```sql
    -- set the owner of the database to 'sa' or a specific user account, without the brackets. 
    EXEC sp_changedbowner '<useraccount>'
    -- example for sa: exec sp_changedbowner 'sa'
    -- example for user account: exec sp_changedbowner 'sqlrepro\administrator' 
    ```

8. Вам потребуется перезапустить **агент чтения журнала**. Для этого разверните узел **Агент SQL Server** в **обозревателе объектов** и откройте элемент **Монитор активности заданий**. Выполните сортировку по **категории** и определите **агент чтения журнала** по категории **REPL: агент чтения журнала**. Щелкните правой кнопкой мыши задание **Агент чтения журнала** и выберите пункт **Запустить задание на шаге**: 

    ![Перезапуск агента чтения журнала](media/tutorial-replicating-data-between-continuously-connected-servers/startjobatstep.png)

9. Проверьте синхронизацию публикации, повторно открыв **Монитор репликации**. Если этот компонент еще не открыт, его можно найти, щелкнув правой кнопкой мыши элемент **Репликация** в **обозревателе объектов**. 
10. Выберите публикацию **AdvWorksProductTrans**, перейдите на вкладку **Агенты** и дважды щелкните **Агент чтения журнала**, чтобы открыть журнал агента. Вы должны увидеть, что **агент чтения журнала** запущен и выполняет репликацию команд или не имеет транзакций репликации:

    ![Запуск средства чтения журнала](media/tutorial-replicating-data-between-continuously-connected-servers/logreaderrunning.png)

### <a name="troubleshoot-errors-with-distribution-agent"></a>Устранение неполадок с агентом распространителя
**Агент распространителя** принимает данные, обнаруженные в базе данных **распространителя**, и применяет их к подписчику. 

1. Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], разверните узел сервера, щелкните правой кнопкой мыши папку **Репликация** и выберите пункт **Запустить монитор репликации**.  
2. В окне **Монитор репликации** выберите публикацию **AdvWorksProductTrans** и перейдите на вкладку **Все подписчики**. Щелкните правой кнопкой мыши подписку, затем выберите **Просмотреть подробности**:

    ![Просмотр сведений о распространителе](media/tutorial-replicating-data-between-continuously-connected-servers/viewdetails.png)

2. Откроется диалоговое окно журнала **От распространителя к подписчику**, в котором будут приведены подробные сведения о возникшей с агентом ошибке: 

     ![Ошибка в журнале агента распространителя](media/tutorial-replicating-data-between-continuously-connected-servers/disthistoryerror.png)
    
        Error messages:
        Agent 'NODE1\SQL2016-AdventureWorks2012-AdvWorksProductTrans-NODE2\SQL2016-7' is retrying after an error. 89 retries attempted. See agent job history in the Jobs folder for more details.

3. Эта ошибка указывает, что **агент распространителя** выполняет повторную попытку. Чтобы узнать больше, разверните узел **Агент SQL Server** в **обозревателе объектов** >  и выберите **Монитор активности заданий**. Выполните сортировку заданий по **категории**. 

    A. Определите **агент распространителя** по категории **REPL: распространение**. Щелкните агент правой кнопкой мыши и выберите пункт **Просмотреть журнал**:

    ![Просмотр журнала агента распространителя](media/tutorial-replicating-data-between-continuously-connected-servers/viewdistagenthistory.png)

5. Выберите одну из записей ошибок и просмотрите текст ошибки в нижней части окна:  

    ![Неверный пароль агента распространителя](media/tutorial-replicating-data-between-continuously-connected-servers/distpwwrong.png)
    
        Message:
        Unable to start execution of step 2 (reason: Error authenticating proxy NODE1\repl_distribution, system error: The user name or password is incorrect.)

6. Эта ошибка указывает на то, что **агент распространителя** использует неверный пароль. Чтобы устранить ее, разверните узел **Репликация** в **обозревателе объектов**, щелкните подписку правой кнопкой мыши и выберите пункт **Свойства**. Нажмите кнопку с многоточием (...) рядом с элементом **Учетная запись процесса агента** и измените пароль:

    ![Изменение пароля для агента распространителя](media/tutorial-replicating-data-between-continuously-connected-servers/distagentpwchange.png)

7. Снова проверьте **монитор репликации**, который можно найти, щелкнув правой кнопкой мыши элемент **Репликация** в **обозревателе объектов**. Красный значок X рядом с элементом **Все подписки** указывает, что ошибка этого **агента распространителя** по-прежнему не устранена. Откройте журнал **От распространителя к подписчику**, для чего выберите **Монитор репликации** > **Просмотреть подробности** и щелкните правой кнопкой мыши пункт "Подписка". В этом случае ошибка будет несколько иной: 

    ![Сбой подключения агента распространителя](media/tutorial-replicating-data-between-continuously-connected-servers/distagentcantconnect.png)
           
        Connecting to Subscriber 'NODE2\SQL2016'        
        Agent message code 20084. The process could not connect to Subscriber 'NODE2\SQL2016'.
        Number:  18456
        Message: Login failed for user 'NODE2\repl_distribution'.

8. Эта ошибка указывает, что **агенту распространителя** не удалось подключиться к подписчику из-за ошибки входа для пользователя **NODE2\repl_distribution**. Чтобы более детально проанализировать причины ошибки, подключитесь к подписчику и откройте *текущий* **журнал ошибок SQL** в узле **Управление** в **обозревателе объектов**: 

    ![Ошибка входа для подписчика](media/tutorial-replicating-data-between-continuously-connected-servers/loginfailed.png) Если отображается эта ошибка, значит, на подписчике не было предоставлено имя для входа. Инструкции по устранению этой ошибки см. в разделе [Установка разрешений базы данных на подписчике](#setting-database-permissions-at-the-subscriber).

9. После устранения ошибки со входом снова проверьте **монитор репликации**. Если все ошибки устранены, рядом с **именем публикации** появится зеленая стрелка, а также будет показано состояние **Выполняется** в разделе **Все подписки**. Щелкните **подписку** правой кнопкой мыши, чтобы открыть журнал **От распространителя к подписчику** еще раз и проверить успешность выполненных действий. Если агент распространителя запущен впервые, вы увидите, что было выполнено массовое копирование моментального снимка на подписчик, как показано на рисунке ниже: 

     ![Успешное выполнение операций агента распространителя](media/tutorial-replicating-data-between-continuously-connected-servers/distagentsuccess.png)   

  ## <a name="next-steps"></a>Следующие шаги
Вы успешно настроили издатель и подписчик для репликации транзакций.  Теперь вы можете вставлять, обновлять и удалять данные в таблице **Продукт** на стороне издателя. После этого вы можете выполнить запрос к таблице **Продукт** на подписчике, чтобы просмотреть реплицированные изменения. В следующей статье будет описана настройка репликации слиянием.  

Перейдите к следующей статье, чтобы узнать больше
> [!div class="nextstepaction"]
> [Следующие шаги](tutorial-replicating-data-with-mobile-clients.md)

  
