---
title: "Проверка данных на подписчике | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Подписчики [репликация SQL Server], проверка данных"
  - "репликация [SQL Server], проверка данных"
  - "репликация транзакций, проверка данных"
  - "проверка данных"
  - "проверка данных репликации слиянием [репликация SQL Server], среда SQL Server Management Studio"
ms.assetid: 215b4c9a-0ce9-4c00-ac0b-43b54151dfa3
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Проверка данных на подписчике
  В данном разделе описывается процесс проверки данных на подписчике в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или объектов RMO.  
  
 Проверка данных состоит из трех этапов:  
  
1.  Одна или все подписки на публикацию *помечаются* для проверки. Пометьте подписки для проверки в диалоговых окнах **Проверить подписку**, **Проверить подпискуs**и **Проверить все подписки** , доступные из папок **Локальные публикации** и **Локальные подписки** в среде [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Все подписки можно также пометить на вкладке **Все подписки** , вкладке **Список наблюдения за подписками** и в узле публикаций монитора репликации. Сведения о запуске монитора репликации см. в разделе [запустить монитор репликации](../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
2.  Подписка проверяется при следующей синхронизации, выполняемой агентом распространителя (для репликации транзакций) или агентом слияния (для репликации слиянием). Агент распространителя, как правило, работает постоянно, то есть проверка выполняется немедленно. Агент слияния запускается по запросу, в этом случае проверка выполняется после запуска агента.  
  
3.  Просмотрите результаты проверки.  
  
    -   В окнах сведений монитора репликации: на вкладке **Журнал операций от распространителя к подписчику** для репликации транзакций и на вкладке **Журнал синхронизации** для репликации слиянием.  
  
    -   В диалоговом окне **Просмотр состояния синхронизации** в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
-   **Для проверки данных на подписчике используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Процедуры монитора репликации используются только для принудительных подписок, так как в мониторе репликации нельзя синхронизировать подписки по запросу. Однако в мониторе репликации можно пометить подписку для проверки и просмотреть результаты проверки для подписок по запросу.  
  
-   Результаты показывают, как завершилась проверка — успешно или неудачно, но в случае ошибки строки, не прошедшие проверку, не указываются. Для сравнения данных издателя и подписчика используется [tablediff Utility](../../tools/tablediff-utility.md). Дополнительные сведения об использовании этой программы с реплицированными данными см. в разделе [сравнения реплицированных таблицах для различия & #40; Программирование репликации на & #41;](../../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Проверка данных подписок на публикацию транзакций (среда Management Studio)  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Щелкните правой кнопкой мыши публикацию, для которой вы хотите проверить подписки, затем нажмите кнопку **Проверить подписки**.  
  
4.  В диалоговом окне **Проверка подписок** выберите подписки, которые надо проверить:  
  
    -   Выберите **Проверить все подписки SQL Server**.  
  
    -   Выберите **Проверить следующие подписки**и укажите одну или несколько подписок.  
  
5.  Чтобы указать тип проверки (подсчет строк или подсчет строк и контрольной суммы), щелкните **Параметры проверки**, а затем укажите параметры в **Параметры проверки подписки** диалоговое окно.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
7.  Просмотрите результаты проверки в мониторе репликации или в диалоговом окне **Просмотр состояния синхронизации** . Для каждой подписки:  
  
    1.  Раскройте публикацию, щелкните правой кнопкой мыши подписку и нажмите кнопку **Просмотр состояния синхронизации**.  
  
    2.  2. Если агент не запущен, нажмите кнопку **Пуск** в диалоговом окне **Просмотр состояния синхронизации** . В диалоговом окне появятся информационные сообщения о проверке.  
  
     Если нет никаких сообщений, касающихся проверки, значит, агент уже зарегистрировал сообщение ранее. В этом случае просмотрите результаты проверки в мониторе репликации. Дополнительные сведения см. в описании процедур монитора репликации данного раздела.  
  
#### Проверка данных отдельной подписки на публикацию слиянием (среда Management Studio)  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Раскройте публикацию, для которой вы хотите проверить подписки, щелкните правой кнопкой мыши подписку и нажмите кнопку **Проверка подписки**.  
  
4.  В диалоговом окне **Проверка подписки** выберите **Проверить эту подписку**.  
  
5.  Чтобы указать тип проверки (подсчет строк или подсчет строк и контрольной суммы) щелкните **Параметры**, и укажите параметры в **Параметры проверки подписки** диалоговое окно.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
7.  Просмотрите результаты проверки в мониторе репликации или в диалоговом окне **Просмотр состояния синхронизации** .  
  
    1.  Раскройте публикацию, щелкните правой кнопкой мыши подписку и нажмите кнопку **Просмотр состояния синхронизации**.  
  
    2.  Если агент не запущен, нажмите кнопку **Пуск** в диалоговом окне **Просмотр состояния синхронизации** . В диалоговом окне появятся информационные сообщения о проверке.  
  
     Если нет никаких сообщений, касающихся проверки, значит, агент уже зарегистрировал сообщение ранее. В этом случае просмотрите результаты проверки в мониторе репликации. Дополнительные сведения см. в описании процедур монитора репликации данного раздела.  
  
#### Проверка данных всех подписок на публикацию слиянием (среда Management Studio)  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Щелкните правой кнопкой мыши публикацию, для которой вы хотите проверить подписки, затем нажмите кнопку **Проверка всех подписок**.  
  
4.  В **Проверка всех подписок** диалоговом окне укажите тип проверки (подсчет строк или подсчет строк и контрольная сумма).  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  Просмотрите результаты проверки в мониторе репликации или в диалоговом окне **Просмотр состояния синхронизации** . Для каждой подписки:  
  
    1.  Раскройте публикацию, щелкните правой кнопкой мыши подписку и нажмите кнопку **Просмотр состояния синхронизации**.  
  
    2.  Если агент не запущен, нажмите кнопку **Пуск** в диалоговом окне **Просмотр состояния синхронизации** . В диалоговом окне появятся информационные сообщения о проверке.  
  
     Если нет никаких сообщений, касающихся проверки, значит, агент уже зарегистрировал сообщение ранее. В этом случае просмотрите результаты проверки в мониторе репликации. Дополнительные сведения см. в описании процедур монитора репликации данного раздела.  
  
#### Проверка данных всех принудительных подписок на публикацию транзакций (монитор репликации)  
  
1.  В мониторе репликации раскройте группу издателей на левой панели, а затем раскройте нужного издателя.  
  
2.  Щелкните правой кнопкой мыши публикацию, для которой вы хотите проверить подписки, затем нажмите кнопку **Проверить подписки**.  
  
3.  В диалоговом окне **Проверка подписок** выберите подписки, которые надо проверить:  
  
    -   Выберите **Проверить все подписки SQL Server**.  
  
    -   Выберите **Проверить следующие подписки**и укажите одну или несколько подписок.  
  
4.  Чтобы указать тип проверки (подсчет строк или подсчет строк и контрольной суммы), щелкните **Параметры проверки**, а затем укажите параметры в **Параметры проверки подписки** диалоговое окно.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  Перейдите на вкладку **Все подписки** .  
  
7.  Просмотрите результаты проверки. Для каждой принудительной подписки:  
  
    1.  Если агент не запущен, щелкните правой кнопкой мыши подписку и нажмите кнопку **запустить синхронизацию**.  
  
    2.  Щелкните правой кнопкой мыши подписку и нажмите кнопку **Просмотр сведений о**.  
  
    3.  3.Просмотрите сведения на вкладке **Журнал операций от распространителя к подписчику** в текстовом поле **Действия в выбранном сеансе** .  
  
#### Проверка данных отдельной принудительной подписки на публикацию слиянием (монитор репликации)  
  
1.  В мониторе репликации раскройте группу издателей на левой панели, раскройте нужного издателя, а затем выберите публикацию.  
  
2.  Перейдите на вкладку **Все подписки** .  
  
3.  Щелкните правой кнопкой мыши подписку, которую нужно проверить, а затем щелкните **Проверка подписки**.  
  
4.  В диалоговом окне **Проверка подписки** выберите **Проверить эту подписку**.  
  
5.  Чтобы указать тип проверки (подсчет строк или подсчет строк и контрольной суммы) щелкните **Параметры**, и укажите параметры в **Параметры проверки подписки** диалоговое окно.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
7.  Перейдите на вкладку **Все подписки** .  
  
8.  Просмотрите результаты проверки:  
  
    1.  Если агент не запущен, щелкните правой кнопкой мыши подписку и нажмите кнопку **запустить синхронизацию**.  
  
    2.  Щелкните правой кнопкой мыши подписку и нажмите кнопку **Просмотр сведений о**.  
  
    3.  Просмотрите сведения на вкладке **Журнал синхронизации** в текстовом поле **Последнее сообщение выбранного сеанса** .  
  
#### Проверка данных всех принудительных подписок на публикацию слиянием (монитор репликации)  
  
1.  В мониторе репликации раскройте группу издателей на левой панели, а затем раскройте нужного издателя.  
  
2.  Щелкните правой кнопкой мыши публикацию, для которой вы хотите проверить подписки, затем нажмите кнопку **Проверка всех подписок**.  
  
3.  В **Проверка всех подписок** диалоговом окне укажите тип проверки (подсчет строк или подсчет строк и контрольная сумма).  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  Перейдите на вкладку **Все подписки** .  
  
6.  Просмотрите результаты проверки. Для каждой принудительной подписки:  
  
    1.  Если агент не запущен, щелкните правой кнопкой мыши подписку и нажмите кнопку **запустить синхронизацию**.  
  
    2.  Щелкните правой кнопкой мыши подписку и нажмите кнопку **Просмотр сведений о**.  
  
    3.  Просмотрите сведения на вкладке **Журнал синхронизации** в текстовом поле **Последнее сообщение выбранного сеанса** .  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Проверка данных для всех статей в публикации транзакций  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_publication_validation & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md). Укажите **@publication** и одно из следующих значений для **@rowcount_only**:  
  
    -   **1** -только проверка по количеству строк (по умолчанию)  
  
    -   **2** -достоверности по количеству строк и двоичной контрольной суммы.  
  
    > [!NOTE]  
    >  При выполнении [sp_publication_validation & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md), [sp_article_validation & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) выполняется для каждой статьи в публикации. Для успешного выполнения [sp_publication_validation & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md), необходимо иметь разрешения SELECT для всех столбцов в опубликованных базовых таблицах.  
  
2.  Если агент распространителя для каждой подписки еще не запущен, запустите его (необязательно). Дополнительные сведения см. в разделах [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) и [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
3.  Просмотрите результаты проверки в выходном файле агента. Дополнительные сведения см. в разделе [проверки репликации данных](../../relational-databases/replication/validate-replicated-data.md).  
  
#### Проверка данных для одной статьи в публикации транзакций  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_article_validation & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md). Укажите **@publication**, имя статьи для **@article**, и одно из следующих значений для **@rowcount_only**:  
  
    -   **1** -только проверка по количеству строк (по умолчанию)  
  
    -   **2** -достоверности по количеству строк и двоичной контрольной суммы.  
  
    > [!NOTE]  
    >  Для успешного выполнения [sp_article_validation & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md), необходимо иметь разрешения SELECT для всех столбцов в опубликованной базовой таблицы.  
  
2.  Если агент распространителя для каждой подписки еще не запущен, запустите его (необязательно). Дополнительные сведения см. в разделах [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) и [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
3.  Просмотрите результаты проверки в выходном файле агента. Дополнительные сведения см. в разделе [проверки репликации данных](../../relational-databases/replication/validate-replicated-data.md).  
  
#### Проверка данных по одному подписчику на публикацию транзакций  
  
1.  На издателе в базе данных публикации, откройте явную транзакцию с помощью [BEGIN TRANSACTION & #40; Transact-SQL & #41;](../../t-sql/language-elements/begin-transaction-transact-sql.md).  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_marksubscriptionvalidation & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-marksubscriptionvalidation-transact-sql.md). Задайте публикацию для **@publication**, имя подписчика для **@subscriber**, и имя базы данных подписки для **@destination_db**.  
  
3.  Повторите шаг 2 для каждой проверяемой подписки (необязательно).  
  
4.  На издателе в базе данных публикации выполните хранимую процедуру [sp_article_validation & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md). Укажите **@publication**, имя статьи для **@article**, и одно из следующих значений для **@rowcount_only**:  
  
    -   **1** -только проверка по количеству строк (по умолчанию)  
  
    -   **2** -достоверности по количеству строк и двоичной контрольной суммы.  
  
    > [!NOTE]  
    >  Для успешного выполнения [sp_article_validation & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md), необходимо иметь разрешения SELECT для всех столбцов в опубликованной базовой таблицы.  
  
5.  На издателе в базе данных публикации, зафиксировать транзакцию с помощью [ФИКСАЦИИ ТРАНЗАКЦИИ & #40; Transact-SQL & #41;](../../t-sql/language-elements/commit-transaction-transact-sql.md).  
  
6.  Повторите шаги 1 – 5 для каждой проверяемой статьи (необязательно).  
  
7.  Запустите агент распространителя, если он еще не работает (необязательно). Дополнительные сведения см. в разделах [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) и [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
8.  Просмотрите результаты проверки в выходном файле агента. Дополнительные сведения см. в разделе [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md).  
  
#### Проверка данных всех подписок на публикацию слиянием  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_validatemergepublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-validatemergepublication-transact-sql.md). Задайте параметр **@publication** и одно из следующих значений в параметре **@level**:  
  
    -   **1** -Проверка достоверности только.  
  
    -   **3** -Проверка двоичной контрольной суммы.  
  
     Таким образом будут отмечены для проверки все публикации.  
  
2.  Запустите агент слияния для каждой подписки. Дополнительные сведения см. в разделах [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) и [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
3.  Просмотрите результаты проверки в выходном файле агента. Дополнительные сведения см. в разделе [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md).  
  
#### Проверка данных по выбранным подпискам на публикацию слиянием  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_validatemergesubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-validatemergesubscription-transact-sql.md). Укажите **@publication**, имя подписчика для **@subscriber**, имя базы данных подписки для **@subscriber_db**, и одно из следующих значений для **@level**:  
  
    -   **1** -Проверка достоверности только.  
  
    -   **3** -Проверка двоичной контрольной суммы.  
  
     Выбранная подписка будет помечена для проверки.  
  
2.  Запустите агент слияния для каждой подписки. Дополнительные сведения см. в разделах [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) и [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
3.  Просмотрите результаты проверки в выходном файле агента.  
  
4.  Повторите шаги 1 – 3 для каждой проверяемой подписки.  
  
> [!NOTE]  
>  Подписка на публикацию слиянием могут также проверяться в конце процесса синхронизации, указав **-проверять** при выполнении [агент слияния репликации](../../relational-databases/replication/agents/replication-merge-agent.md).  
  
#### Проверка данных в подписке с помощью параметров агента слияния  
  
1.  Запустите агент слияния на подписчике (подписка по запросу) или на распространителе (принудительная подписка) из командной строки одним из следующих способов.  
  
    -   При значении **1** (количество строк) или **3** (количество строк и двоичной контрольной суммы) для **-Проверка** параметр.  
  
    -   Указание **проверки достоверности по количеству строк** или **проверки достоверности по количеству строк и контрольной суммы** для **- ProfileName** параметр.  
  
     Дополнительные сведения см. в разделе [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) или [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Репликация позволяет использовать объекты RMO для программной проверки того, что данные на подписчике совпадают с данными на издателе. Выбор объектов зависит от типа топологии репликации. Для репликации транзакций необходима проверка всех подписок на публикацию.  
  
> [!NOTE]  
>  Например, в разделе [Пример RMO](#RMOExample), Далее в этом разделе.  
  
#### Проверка данных для всех статей в публикации транзакций  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.TransPublication> класса. Задайте <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Свойства для публикации. Задайте <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства подключения, созданной на шаге 1.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить оставшиеся свойства объекта. Если этот метод возвращает **false**, то либо на шаге 2 были неверно определены свойства публикации, либо публикация не существует.  
  
4.  Вызов <xref:Microsoft.SqlServer.Replication.TransPublication.ValidatePublication%2A> метод. Передайте следующие параметры:  
  
    -   <xref:Microsoft.SqlServer.Replication.ValidationOption>  
  
    -   <xref:Microsoft.SqlServer.Replication.ValidationMethod>  
  
    -   Логическое значение, указывающее, нужно ли прекращать выполнение агента распространителя после окончания проверки.  
  
     Будут отмечены статьи для проверки.  
  
5.  Если агент распространителя еще не работает, запустите его для синхронизации каждой подписки. Дополнительные сведения см. в разделе [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md) или [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md). Результат операции проверки записывается в журнал агента. Дополнительные сведения см. в разделе [Monitoring Replication](../../relational-databases/replication/monitor/monitoring-replication-overview.md).  
  
#### Проверка данных всех подписок на публикацию слиянием  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergePublication> класса. Задайте <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Свойства для публикации. Задайте <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства подключения, созданной на шаге 1.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить оставшиеся свойства объекта. Если этот метод возвращает **false**, то либо на шаге 2 были неверно определены свойства публикации, либо публикация не существует.  
  
4.  Вызов <xref:Microsoft.SqlServer.Replication.MergePublication.ValidatePublication%2A> метод. Передайте нужный <xref:Microsoft.SqlServer.Replication.ValidationOption>.  
  
5.  Выполните агент слияния для каждой подписки, чтобы начать проверку, или подождите следующего планового запуска агента. Дополнительные сведения см. в разделах [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) и [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md). Результат проверки записывается в журнал агента, который можно просмотреть с помощью монитора репликации. Дополнительные сведения см. в разделе [Monitoring Replication](../../relational-databases/replication/monitor/monitoring-replication-overview.md).  
  
#### Проверка данных в одной подписке на публикацию слиянием  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergePublication> класса. Задайте <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Свойства для публикации. Задайте <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства подключения, созданной на шаге 1.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить оставшиеся свойства объекта. Если этот метод возвращает **false**, то либо на шаге 2 были неверно определены свойства публикации, либо публикация не существует.  
  
4.  Вызов <xref:Microsoft.SqlServer.Replication.MergePublication.ValidateSubscription%2A> метод. Передайте имя подписчика и подписки, проверяемую базу данных и нужный <xref:Microsoft.SqlServer.Replication.ValidationOption>.  
  
5.  Выполните агент слияния для каждой подписки, чтобы начать проверку, или подождите следующего планового запуска агента. Дополнительные сведения см. в разделах [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) и [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md). Результат проверки записывается в журнал агента, который можно просмотреть с помощью монитора репликации. Дополнительные сведения см. в статье [Monitoring Replication](../../relational-databases/replication/monitor/monitoring-replication-overview.md).  
  
###  <a name="RMOExample"></a> Пример (объекты RMO)  
 В этом примере помечаются все подписки на публикацию транзакций для проверки количества строк.  
  
 [!code-csharp[HowTo#rmo_ValidateTranPub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_validatetranpub)]  
  
 [!code-vb[HowTo#rmo_vb_ValidateTranPub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_validatetranpub)]  
  
 В этом примере помечается определенная подписка на публикацию слиянием для проверки количества строк.  
  
 [!code-csharp[HowTo#rmo_ValidateMergeSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_validatemergesub)]  
  
 [!code-vb[HowTo#rmo_vb_ValidateMergeSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_validatemergesub)]  
  
  