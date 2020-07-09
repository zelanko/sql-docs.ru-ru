---
title: Проверка реплицированных данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Subscribers [SQL Server replication], data validation
- replication [SQL Server], validating data
- transactional replication, validating data
- validating data
- merge replication data validation [SQL Server replication], SQL Server Management Studio
ms.assetid: 215b4c9a-0ce9-4c00-ac0b-43b54151dfa3
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: e666a14b93725b833ec8a050bb637ee71c39c6ee
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85720654"
---
# <a name="validate-replicated-data"></a>Проверка реплицированных данных
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md.md](../../includes/applies-to-version/sql-asdb.md)]
  В данном разделе описывается процесс проверки данных на подписчике в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или объектов RMO.  
  
Репликация транзакций, а также репликация слиянием позволяет проверять соответствие данных подписчика данным издателя. Проверку можно выполнять как для определенных подписок, так и для всех подписок в публикации. Задайте один из следующих типов проверки и агент распространителя или агент слияния проверят данные при следующем запуске.  
  
-   **Только подсчет строк**. При проверке этого типа проверяется совпадение числа строк таблицы на подписчике с числом строк таблицы на издателе, но не проверяется содержимое строк на совпадение. Проверка количества строк обеспечивает упрощенный подход к проверке, который может уведомить о проблемах с данными.   
-   **Подсчет количества строк и двоичной контрольной суммы**. Кроме подсчета количества строк на подписчике и на издателе, вычисляется контрольная сумма всех данных с помощью алгоритма подсчета контрольной суммы. Если количество строк не совпадает, то контрольная сумма не проверяется.  
  
 Кроме проверки совпадения данных на подписчике и издателе, репликация слиянием предоставляет возможность удостовериться, правильно ли данные секционированы для каждого подписчика. Дополнительные сведения см. в статье [Проверка сведений о секции для подписчика на публикацию слиянием](../../relational-databases/replication/validate-partition-information-for-a-merge-subscriber.md).  

[!INCLUDE[azure-sql-db-replication-supportability-note](../../includes/azure-sql-db-replication-supportability-note.md)]
   
## <a name="how-data-validation-works"></a>Как работает проверка данных  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверяет данные путем подсчета числа строк или контрольной суммы на издателе и последующего сравнения этих значений с соответствующими значениями числа строк и контрольной суммы, вычисленными на подписчике. Одно значение вычисляется для всей таблицы публикации, одно — для всей таблицы подписки, но данные в столбцах типа **text**, **ntext**и **image** в вычислении не участвуют.  
  
 При выполнении вычислений временно устанавливаются совместные блокировки таблиц, для которых производится подсчет числа строк или контрольных сумм, однако вычисления вскоре завершаются и общие блокировки снимаются, обычно в течение нескольких секунд.  
  
 При использовании двоичных контрольных сумм выполняется последовательная проверка столбцов избыточным 32-разрядным кодом (CRC) вместо проверки циклическим избыточным кодом (CRC) физической строки на странице данных. Это позволяет столбцам таблицы располагаться физически в любом порядке на странице данных, и при этом CRC-код для строки будет оставаться прежним. Проверка по двоичной контрольной сумме может использоваться при наличии у публикации фильтров по строкам или столбцам.  

 Проверка данных состоит из трех этапов:  
  
1.  Одна или все подписки на публикацию *помечаются* для проверки. Пометьте подписки для проверки в диалоговых окнах **Проверить подписку**, **Проверить подписки**и **Проверить все подписки** , доступные из папок **Локальные публикации** и **Локальные подписки** в среде [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Все подписки можно также пометить на вкладке **Все подписки** , вкладке **Список наблюдения за подписками** и в узле публикаций монитора репликации. Сведения о запуске монитора репликации см. в [этой статье](../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
2.  Подписка проверяется при следующей синхронизации, выполняемой агентом распространителя (для репликации транзакций) или агентом слияния (для репликации слиянием). Агент распространителя, как правило, работает постоянно, то есть проверка выполняется немедленно. Агент слияния запускается по запросу, в этом случае проверка выполняется после запуска агента.  
  
3.  Просмотрите результаты проверки.   
    -   В окнах сведений монитора репликации: на вкладке **Журнал операций от распространителя к подписчику** для репликации транзакций и на вкладке **Журнал синхронизации** для репликации слиянием.    
    -   В диалоговом окне **Просмотр состояния синхронизации** в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
 
## <a name="considerations-and-restrictions"></a>Рекомендации и ограничения  
 При проверке данных учитывайте следующие соображения.  
  
-   Перед проверкой данных следует остановить все действия по обновлению на подписчиках (при выполнении проверки нет необходимости останавливать действия на издателе).  
-   Ввиду того что простые и двоичные контрольные суммы могут требовать больших вычислительных мощностей при проверке большого количества данных, следует назначать проверку на время, когда активность используемых в репликации серверов минимальна.   
-   Репликация проверяет только таблицы; она не проверяет, совпадают ли в схеме на издателе и подписчике только статьи (например, хранимые процедуры).   
-   Двоичная контрольная сумма может использоваться с любой опубликованной таблицей. С помощью контрольной суммы нельзя проверить таблицы с фильтрацией по столбцам, или логические структуры таблиц, отличающиеся смещением столбцов (из-за инструкций ALTER TABLE, удаляющих или добавляющих столбцы).   
-   При проверке репликации вызываются функции **checksum** и **binary_checksum** . Сведения об их поведении см. в статьях [CHECKSUM (Transact-SQL)](../../t-sql/functions/checksum-transact-sql.md) и [BINARY_CHECKSUM (Transact-SQL)](../../t-sql/functions/binary-checksum-transact-sql.md).   
-   Проверка с использованием двоичной контрольной суммы может неверно сообщить об отказе, если типы данных на подписчике и издателе отличаются. К этому может привести выполнение одного из следующих действий.    
    -   Явная установка параметров схемы для соответствия типам данных в ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
    -   Установка уровня совместимости публикации для публикации слиянием в соответствии с более ранней версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в то время как опубликованные таблицы содержат один или несколько типов данных, которые должны соответствовать текущей версии.    
    -   Инициализация подписки вручную при использовании разных типов данных на подписчике.   
-   Проверки двоичной контрольной суммы и простой контрольной суммы не поддерживаются трансформируемыми подписками для репликации транзакций.   
-   Также не поддерживается проверка данных, реплицированных на подписчики, отличные от[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .    
-   Процедуры монитора репликации используются только для принудительных подписок, так как в мониторе репликации нельзя синхронизировать подписки по запросу. Однако в мониторе репликации можно пометить подписку для проверки и просмотреть результаты проверки для подписок по запросу.    
-   Результаты показывают, как завершилась проверка — успешно или неудачно, но в случае ошибки строки, не прошедшие проверку, не указываются. Для сравнения данных издателя и подписчика используется [tablediff Utility](../../tools/tablediff-utility.md). Дополнительные сведения об использовании этой программы с реплицированными данными см. в статье [Compare Replicated Tables for Differences (Replication Programming)](../../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md) (Сравнение реплицируемых таблиц на предмет различий (программирование репликации)).  


## <a name="data-validation-results"></a>Результаты проверки данных  
 Когда проверка заканчивается, агент распространителя или агент слияния заносит в журнал сообщения касательно успеха или неудачи (репликация не сообщает, на каких строках возникла ошибка). Эти сообщения можно просмотреть в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], мониторе репликации и в системных таблицах репликации. В перечисленных выше разделах руководства описывается, как запустить проверку и просмотреть ее результаты.  
  
 Чтобы обработать ошибки проверки, рассмотрите следующее.  
  
-   Настройте предупреждение репликации под названием **Репликация: ошибка проверки данных подписчиком** , чтобы получать уведомление об ошибке. Дополнительные сведения см. в статье [Настройка стандартных предупреждений репликации (среда SQL Server Management Studio)](../../relational-databases/replication/administration/configure-predefined-replication-alerts-sql-server-management-studio.md).  
  
-   Является ли неудачная проверка данных проблемой для приложения? Если неудачная проверка данных представляет собой проблему, обновите данные вручную, чтобы они были синхронизированы, или повторно инициализируйте подписку.  
  
    -   Данные можно обновить с помощью [программы tablediff](../../tools/tablediff-utility.md). Дополнительные сведения об использовании этой программы см. в статье [Сравнение реплицируемых таблиц на предмет различий (программирование репликации)](../../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md).  
  
    -   Дополнительные сведения о повторной инициализации см. в статье [Повторная инициализация подписок](../../relational-databases/replication/reinitialize-subscriptions.md).  

  
  
## <a name="articles-in-transactional-replication"></a>Статьи при репликации транзакций 

### <a name="using-sql-server-management-studio"></a>Использование среды SQL Server Management Studio
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.    
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .    
3.  Щелкните правой кнопкой мыши публикацию, для которой хотите проверить подписки, затем выберите **Проверить подписки**.    
4.  В диалоговом окне **Проверка подписок** выберите подписки, которые надо проверить:   
    -   Выберите **Проверить все подписки SQL Server**.    
    -   Выберите **Проверить следующие подписки**и укажите одну или несколько подписок.    
5.  Чтобы задать тип проверки (подсчет строк или подсчет строк с контрольной суммой), щелкните **Параметры проверки**и укажите параметры в диалоговом окне **Параметры проверки подписки** .  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]   
7.  Просмотрите результаты проверки в мониторе репликации или в диалоговом окне **Просмотр состояния синхронизации** . Для каждой подписки:   
    1.  Раскройте публикацию и щелкните правой кнопкой мыши подписку, затем выберите **Просмотр состояния синхронизации**.    
    2.  2\. Если агент не запущен, нажмите кнопку **Пуск** в диалоговом окне **Просмотр состояния синхронизации** . В диалоговом окне появятся информационные сообщения о проверке.    
     Если нет никаких сообщений, касающихся проверки, значит, агент уже зарегистрировал сообщение ранее. В этом случае просмотрите результаты проверки в мониторе репликации. Дополнительные сведения см. в описании процедур монитора репликации данного раздела.  

### <a name="using-transact-sql"></a>Использование Transact-SQL

#### <a name="all-articles"></a>Все статьи 
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_publication_validation (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md). Задайте параметр `@publication` и одно из следующих значений для `@rowcount_only`:  
  
    -   **1** — проверка только количества строк (по умолчанию);    
    -   **2** — проверка количества строк и двоичной контрольной суммы.  
  
    > [!NOTE]  
    >  Если выполняется процедура [sp_publication_validation (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md), то процедура [sp_article_validation (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) выполняется для каждой статьи в публикации. Для успешного выполнения [sp_publication_validation (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md) необходимо иметь разрешения SELECT для всех столбцов в опубликованных базовых таблицах.    
2.  Если агент распространителя для каждой подписки еще не запущен, запустите его (необязательно). Дополнительные сведения см. в разделах [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) и [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).    
3.  Просмотрите результаты проверки в выходном файле агента. 
  
#### <a name="single-article"></a>Одна статья  
  
1.  На издателе в базе данных публикации выполните процедуру [sp_article_validation (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md). Задайте параметр `@publication`, имя статьи в параметре `@article` и одно из следующих значений в параметре `@rowcount_only`:  
  
    -   **1** — проверка только количества строк (по умолчанию)    
    -   **2** — проверка количества строк и двоичной контрольной суммы.  
  
    > [!NOTE]  
    >  Для успешного выполнения процедуры [sp_article_validation (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) необходимо иметь разрешения SELECT для всех столбцов в опубликованных базовых таблицах.  
  
2.  Если агент распространителя для каждой подписки еще не запущен, запустите его (необязательно). Дополнительные сведения см. в разделах [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) и [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).    
3.  Просмотрите результаты проверки в выходном файле агента.
  
#### <a name="single-subscriber"></a>Один подписчик 
  
1.  На издателе в базе данных публикации откройте явную транзакцию с помощью [BEGIN TRANSACTION (Transact-SQL)](../../t-sql/language-elements/begin-transaction-transact-sql.md).    
2.  На издателе в базе данных публикации выполните процедуру [sp_marksubscriptionvalidation (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-marksubscriptionvalidation-transact-sql.md). Задайте публикацию в параметре `@publication`, имя подписчика в параметре `@subscriber` и имя базы данных подписки для `@destination_db`.    
3.  Повторите шаг 2 для каждой проверяемой подписки (необязательно).    
4.  На издателе в базе данных публикации выполните процедуру [sp_article_validation (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md). Задайте параметр `@publication`, имя статьи в параметре `@article` и одно из следующих значений в параметре `@rowcount_only`:    
    -   **1** — проверка только количества строк (по умолчанию)    
    -   **2** — проверка количества строк и двоичной контрольной суммы.  
  
    > [!NOTE]  
    >  Для успешного выполнения процедуры [sp_article_validation (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) необходимо иметь разрешения SELECT для всех столбцов в опубликованных базовых таблицах.  
  
5.  На издателе в базе данных публикации зафиксируйте транзакцию с помощью [COMMIT TRANSACTION (Transact-SQL)](../../t-sql/language-elements/commit-transaction-transact-sql.md).    
6.  Повторите шаги 1 – 5 для каждой проверяемой статьи (необязательно).   
7.  Запустите агент распространителя, если он еще не работает (необязательно). Дополнительные сведения см. в разделах [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) и [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).    
8.  Просмотрите результаты проверки в выходном файле агента. Дополнительные сведения см. в разделе [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md).  

## <a name="all-push-subscriptions-to-a-transactional-publication"></a>Все принудительные подписки на публикации транзакций 

### <a name="using-replication-monitor"></a>Использование монитора репликации
  
1.  В мониторе репликации раскройте группу издателей на левой панели, а затем раскройте нужного издателя.   
2.  Щелкните правой кнопкой мыши публикацию, для которой хотите проверить подписки, затем выберите **Проверить подписки**.   
3.  В диалоговом окне **Проверка подписок** выберите подписки, которые надо проверить:  
  
    -   Выберите **Проверить все подписки SQL Server**.    
    -   Выберите **Проверить следующие подписки**и укажите одну или несколько подписок.    
4.  Чтобы задать тип проверки (подсчет строк или подсчет строк с контрольной суммой), щелкните **Параметры проверки**и укажите параметры в диалоговом окне **Параметры проверки подписки** .    
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]    
6.  Перейдите на вкладку **Все подписки** .  
7.  Просмотрите результаты проверки. Для каждой принудительной подписки:    
    1.  1\. Если агент не запущен, щелкните правой кнопкой мыши подписку и выберите **Запустить синхронизацию**.    
    2.  Щелкните правой кнопкой мыши подписку, затем выберите **Просмотреть подробности**.   
    3.  3\.Просмотрите сведения на вкладке **Журнал операций от распространителя к подписчику** в текстовом поле **Действия в выбранном сеансе** .  
  
## <a name="for-a-single-subscription-to-a-merge-publication"></a>Для одной подписки на публикацию слиянием

### <a name="using-sql-server-management-studio"></a>Использование среды SQL Server Management Studio
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.    
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .   
3.  Раскройте публикацию, для которой требуется проверить подписки, щелкните правой кнопкой мыши подписку и затем выберите **Проверить подписку**.    
4.  В диалоговом окне **Проверка подписки** выберите **Проверить эту подписку**.    
5.  Чтобы задать тип проверки (подсчет строк или подсчет строк с контрольной суммой), щелкните **Параметры**и укажите параметры в диалоговом окне **Параметры проверки подписки** .    
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]    
7.  Просмотрите результаты проверки в мониторе репликации или в диалоговом окне **Просмотр состояния синхронизации** .  
  
    1.  Раскройте публикацию и щелкните правой кнопкой мыши подписку, затем выберите **Просмотр состояния синхронизации**.    
    2.  Если агент не запущен, нажмите кнопку **Пуск** в диалоговом окне **Просмотр состояния синхронизации** . В диалоговом окне появятся информационные сообщения о проверке.  
  
     Если нет никаких сообщений, касающихся проверки, значит, агент уже зарегистрировал сообщение ранее. В этом случае просмотрите результаты проверки в мониторе репликации. Дополнительные сведения см. в описании процедур монитора репликации данного раздела.  
  
## <a name="for-all-subscriptions-to-a-merge-publication"></a>Для всех подписок на публикацию слиянием

### <a name="using-sql-server-management-studio"></a>Использование среды SQL Server Management Studio  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.    
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .   
3.  Щелкните правой кнопкой мыши публикацию, для которой хотите проверить подписки, затем нажмите кнопку **Проверить все подписки**.    
4.  В диалоговом окне **Проверка всех подписок** задайте тип проверки (подсчет строк или подсчет строк с контрольной суммой).   
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]    
6.  Просмотрите результаты проверки в мониторе репликации или в диалоговом окне **Просмотр состояния синхронизации** . Для каждой подписки:    
    1.  Раскройте публикацию и щелкните правой кнопкой мыши подписку, затем выберите **Просмотр состояния синхронизации**.    
    2.  Если агент не запущен, нажмите кнопку **Пуск** в диалоговом окне **Просмотр состояния синхронизации** . В диалоговом окне появятся информационные сообщения о проверке.  
  
     Если нет никаких сообщений, касающихся проверки, значит, агент уже зарегистрировал сообщение ранее. В этом случае просмотрите результаты проверки в мониторе репликации. Дополнительные сведения см. в описании процедур монитора репликации данного раздела.  
  
 
## <a name="for-a-single-push-subscription-to-a-merge-publication"></a>Для одной принудительной подписки на публикацию слиянием 

### <a name="using-replication-monitor"></a>Использование монитора репликации  
1.  В мониторе репликации раскройте группу издателей на левой панели, раскройте нужного издателя, а затем выберите публикацию.    
2.  Перейдите на вкладку **Все подписки** .    
3.  Щелкните правой кнопкой мыши подписку, для которой требуется выполнить проверку, а затем щелкните **Проверить подписку**.    
4.  В диалоговом окне **Проверка подписки** выберите **Проверить эту подписку**.    
5.  Чтобы задать тип проверки (подсчет строк или подсчет строк с контрольной суммой), щелкните **Параметры**и укажите параметры в диалоговом окне **Параметры проверки подписки** .    
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]    
7.  Перейдите на вкладку **Все подписки** .    
8.  Просмотрите результаты проверки:    
    1.  1\. Если агент не запущен, щелкните правой кнопкой мыши подписку и выберите **Запустить синхронизацию**.    
    2.  Щелкните правой кнопкой мыши подписку, затем выберите **Просмотреть подробности**.    
    3.  Просмотрите сведения на вкладке **Журнал синхронизации** в текстовом поле **Последнее сообщение выбранного сеанса** .  

### <a name="using-transact-sql"></a>Использование Transact-SQL
1.  На издателе в базе данных публикации выполните процедуру [sp_validatemergesubscription (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-validatemergesubscription-transact-sql.md). Задайте параметр `@publication`, имя подписчика в параметре `@subscriber`, имя базы данных подписки в параметре `@subscriber_db` и одно из следующих значений в параметре `@level`:   
    -   **1** — проверка только количества строк.    
    -   **3** — проверка двоичной контрольной суммы.  
  
     Выбранная подписка будет помечена для проверки.  
  
2.  Запустите агент слияния для каждой подписки. Дополнительные сведения см. в разделах [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) и [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
3.  Просмотрите результаты проверки в выходном файле агента.   
4.  Повторите шаги 1 – 3 для каждой проверяемой подписки.  
  
> [!NOTE]  
>  Подписка на публикацию слиянием может быть проверена и в конце синхронизации с помощью параметра **-Validate** , когда работает [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md).  
  
## <a name="for-all-push-subscriptions-to-a-merge-publication"></a>Для всех принудительных подписок на публикацию слиянием
  
### <a name="using-replication-monitor"></a>Использование монитора репликации    
1.  В мониторе репликации раскройте группу издателей на левой панели, а затем раскройте нужного издателя.    
2.  Щелкните правой кнопкой мыши публикацию, для которой хотите проверить подписки, затем нажмите кнопку **Проверить все подписки**.    
3.  В диалоговом окне **Проверка всех подписок** задайте тип проверки (подсчет строк или подсчет строк с контрольной суммой).    
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]    
5.  Перейдите на вкладку **Все подписки** .    
6.  Просмотрите результаты проверки. Для каждой принудительной подписки:    
    1.  1\. Если агент не запущен, щелкните правой кнопкой мыши подписку и выберите **Запустить синхронизацию**.    
    2.  Щелкните правой кнопкой мыши подписку, затем выберите **Просмотреть подробности**.    
    3.  Просмотрите сведения на вкладке **Журнал синхронизации** в текстовом поле **Последнее сообщение выбранного сеанса** . 
  
### <a name="using-transact-sql"></a>Использование Transact-SQL
1.  На издателе в базе данных публикации выполните процедуру [sp_validatemergepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-validatemergepublication-transact-sql.md). Задайте параметр `@publication` и одно из следующих значений для `@level`:    
    -   **1** — проверка только количества строк.   
    -   **3** — проверка двоичной контрольной суммы.  
  
     Таким образом будут отмечены для проверки все публикации.   
2.  Запустите агент слияния для каждой подписки. Дополнительные сведения см. в разделах [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) и [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
3.  Просмотрите результаты проверки в выходном файле агента. Дополнительные сведения см. в разделе [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md).  

  
## <a name="validate-data-using-merge-agent-parameters"></a>Проверка данных с помощью параметров агента слияния  
  
1.  Запустите агент слияния на подписчике (подписка по запросу) или на распространителе (принудительная подписка) из командной строки одним из следующих способов.   
    -   Задайте значение **1** (количество строк) или **3** (количество строк и двоичная контрольная сумма) в параметре **-Validate** .    
    -   Задайте **rowcount validation** (проверка количества строк) или **rowcount and checksum validation** (количество строк и контрольная сумма) в параметре **-ProfileName** .  
  
     Дополнительные сведения см. в разделе [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) или [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> При помощи объектов RMO  
 Репликация позволяет использовать объекты RMO для программной проверки того, что данные на подписчике совпадают с данными на издателе. Выбор объектов зависит от типа топологии репликации. Для репликации транзакций необходима проверка всех подписок на публикацию.  
  
> [!NOTE]  
>  См. приведенный ниже [Пример (объекты RMO)](#RMOExample).  
  
#### <a name="to-validate-data-for-all-articles-in-a-transactional-publication"></a>Проверка данных для всех статей в публикации транзакций  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransPublication>. Установите для публикации свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> . В свойстве <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> укажите созданное на шаге 1 соединение.  
  
3.  Чтобы получить оставшиеся свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает **false**, то либо на шаге 2 были неверно определены свойства публикации, либо публикация не существует.  
  
4.  Вызовите метод <xref:Microsoft.SqlServer.Replication.TransPublication.ValidatePublication%2A> . Передайте следующие параметры:  
  
    -   <xref:Microsoft.SqlServer.Replication.ValidationOption>  
  
    -   <xref:Microsoft.SqlServer.Replication.ValidationMethod>  
  
    -   Логическое значение, указывающее, нужно ли прекращать выполнение агента распространителя после окончания проверки.  
  
     Будут отмечены статьи для проверки.  
  
5.  Если агент распространителя еще не работает, запустите его для синхронизации каждой подписки. Дополнительные сведения см. в разделе [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md) или [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md). Результат операции проверки записывается в журнал агента. Дополнительные сведения см. в разделе [Monitoring Replication](../../relational-databases/replication/monitor/monitoring-replication.md).  
  
#### <a name="to-validate-data-in-all-subscriptions-to-a-merge-publication"></a>Проверка данных всех подписок на публикацию слиянием  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePublication>. Установите для публикации свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> . В свойстве <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> укажите созданное на шаге 1 соединение.  
  
3.  Чтобы получить оставшиеся свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает **false**, то либо на шаге 2 были неверно определены свойства публикации, либо публикация не существует.  
  
4.  Вызовите метод <xref:Microsoft.SqlServer.Replication.MergePublication.ValidatePublication%2A> . Передайте нужный параметр <xref:Microsoft.SqlServer.Replication.ValidationOption>.  
  
5.  Выполните агент слияния для каждой подписки, чтобы начать проверку, или подождите следующего планового запуска агента. Дополнительные сведения см. в разделах [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) и [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md). Результат проверки записывается в журнал агента, который можно просмотреть с помощью монитора репликации. Дополнительные сведения см. в разделе [Monitoring Replication](../../relational-databases/replication/monitor/monitoring-replication.md).  
  
#### <a name="to-validate-data-in-a-single-subscription-to-a-merge-publication"></a>Проверка данных в одной подписке на публикацию слиянием  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePublication>. Установите для публикации свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> . В свойстве <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> укажите созданное на шаге 1 соединение.  
  
3.  Чтобы получить оставшиеся свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает **false**, то либо на шаге 2 были неверно определены свойства публикации, либо публикация не существует.  
  
4.  Вызовите метод <xref:Microsoft.SqlServer.Replication.MergePublication.ValidateSubscription%2A> . Передайте имя подписчика, проверяемую базу данных подписки и нужный параметр <xref:Microsoft.SqlServer.Replication.ValidationOption>.  
  
5.  Выполните агент слияния для каждой подписки, чтобы начать проверку, или подождите следующего планового запуска агента. Дополнительные сведения см. в разделах [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) и [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md). Результат проверки записывается в журнал агента, который можно просмотреть с помощью монитора репликации. Дополнительные сведения см. в разделе [Monitoring Replication](../../relational-databases/replication/monitor/monitoring-replication.md).  
  
###  <a name="example-rmo"></a><a name="RMOExample"></a> Пример (объекты RMO)  
 В этом примере помечаются все подписки на публикацию транзакций для проверки количества строк.  
  
 [!code-cs[HowTo#rmo_ValidateTranPub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_validatetranpub)]  
  
 [!code-vb[HowTo#rmo_vb_ValidateTranPub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_validatetranpub)]  
  
 В этом примере помечается определенная подписка на публикацию слиянием для проверки количества строк.  
  
 [!code-cs[HowTo#rmo_ValidateMergeSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_validatemergesub)]  
  
 [!code-vb[HowTo#rmo_vb_ValidateMergeSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_validatemergesub)]  
  
 ## <a name="see-also"></a>См. также:  
[Best Practices for Replication Administration](../../relational-databases/replication/administration/best-practices-for-replication-administration.md)  
  
  
