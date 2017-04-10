---
title: "Доставка моментального снимка через FTP | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "моментальные снимки [репликация SQL Server], моментальные снимки через FTP"
  - "моментальные снимки через FTP [репликация SQL Server]"
  - "репликация моментального снимка [SQL Server], FTP"
ms.assetid: 99872c4f-40ce-4405-8fd4-44052d3bd827
caps.latest.revision: 47
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 47
---
# Доставка моментального снимка через FTP
  В этом разделе описывается доставка моментального снимка по протоколу FTP в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Предварительные требования](#Prerequisites)  
  
     [Безопасность](#Security)  
  
-   **Для доставки моментального снимка по протоколу FTP используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Агент моментальных снимков должен иметь разрешения на запись в указанный каталог, а агент распространителя или агент слияния должен иметь разрешения на чтение из этого каталога. Если используются подписки по запросу, необходимо указать общий каталог как универсальных имен пути (UNC), например \\\ftpserver\home\snapshots. Дополнительные сведения см. в разделе [Безопасность папки моментальных снимков](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Для передачи файлов моментальных снимков с использованием протокола FTP (File Transfer Protocol) необходимо настроить FTP-сервер. Дополнительные сведения см. в документации служб IIS [!INCLUDE[msCoName](../../../includes/msconame-md.md)].  
  
###  <a name="Security"></a> Безопасность  
 В целях повышения безопасности рекомендуется реализовать частную виртуальную сеть (VPN) при доставке моментальных снимков по протоколу FTP через Интернет. Дополнительные сведения см. в разделе [Публикация данных через Интернет с помощью VPN](../../../relational-databases/replication/publish-data-over-the-internet-using-vpn.md).  
  
 Для обеспечения безопасности рекомендуется запретить анонимный вход на FTP-сервер. Агент моментальных снимков должен иметь разрешения на запись в указанный каталог, а агент распространителя или агент слияния должен иметь разрешения на чтение из этого каталога. Если используются подписки по запросу, необходимо указать общий каталог как универсальных имен пути (UNC), например \\\ftpserver\home\snapshots. Дополнительные сведения см. в разделе [Безопасность папки моментальных снимков](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
 По возможности запрашивайте у пользователей учетные данные в среде выполнения приложения. Если учетные данные хранятся в файле скрипта, необходимо защитить этот файл.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 После настройки FTP-сервера укажите каталог и сведения безопасности для этого сервера в **Свойства публикации — \< публикация>** диалоговое окно. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Указание сведений FTP  
  
1.  В **Свойства публикации — \< публикация>** диалоговом **разрешить подписчикам загружать файлы моментальных снимков по протоколу FTP** из одного из следующих страниц:  
  
    -   Страница **Моментальный снимок FTP** для публикаций моментальных снимков, публикаций транзакций и публикаций слиянием с издателей, использующих версии, предшествующие [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
    -   Страница **Моментальный снимок FTP и Интернет** для публикаций слиянием с издателей, использующих [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более позднюю версию.  
  
2.  Укажите значения для свойств **Имя FTP-сервера**, **Номер порта**, **Путь из корневой папки FTP**, **Имя входа**и **Пароль**.  
  
     Например, если корневой сервер FTP — \\\ftpserver\home и хотите, чтобы моментальные снимки хранились в \\\ftpserver\home\snapshots, укажите \snapshots\ftp для свойства **путь из корневой папки FTP** (репликация присоединяет 'ftp' к пути папки моментальных снимков при создании файлов моментальных снимков).  
  
3.  Укажите, что агент моментальных снимков должен записывать файлы моментальных снимков в каталог, указанный на шаге 2. Например, для моментального снимка агент записывать файлы моментальных снимков \\\ftpserver\home\snapshots\ftp, необходимо указать путь \\\ftpserver\home\snapshots в одном из двух мест:  
  
    -   Расположение моментальных снимков по умолчанию для распространителя, связанного с этой публикацией.  
  
         Дополнительные сведения об указании расположения моментальных снимков по умолчанию см. в разделе [Укажите местоположение моментальных снимков по умолчанию & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md).  
  
    -   Альтернативное расположение папки моментальных снимков для данной публикации. Если моментальный снимок сжимается, необходимо альтернативное расположение папки.  
  
         Введите путь в **поместить файлы в следующую папку** текстовое поле на странице моментальных снимков **Свойства публикации — \< публикация>** диалоговое окно. Дополнительные сведения об альтернативных местоположениях папки моментальных снимков см. в разделе [Alternate Snapshot Folder Locations](../../../relational-databases/replication/alternate-snapshot-folder-locations.md).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Можно установить параметр, который сделает доступными файлы моментальных снимков на сервере, а настройки FTP можно изменить программно с помощью хранимых процедур репликации. Эта процедура зависит от типа публикации. Доставка моментальных снимков по протоколу FTP используется только с подписками по запросу.  
  
#### Включение доставки моментальных снимков по протоколу FTP для публикации моментальных снимков или публикации транзакций  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addpublication](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md). Укажите **@publication**, значение **true** для **@enabled_for_internet**, и соответствующие значения для следующих параметров:  
  
    -   **@ftp_address** -адрес FTP-сервера, используемого для доставки моментального снимка.  
  
    -   (Необязательно) **@ftp_port** -порт, используемый FTP-сервера.  
  
    -   (Необязательно) **@ftp_subdirectory** — подкаталог FTP-каталога по умолчанию назначена учетная запись FTP. Например, если корневой сервер FTP — \\\ftpserver\home и хотите, чтобы моментальные снимки хранились в \\\ftpserver\home\snapshots, укажите **\snapshots\ftp** для **@ftp_subdirectory** (репликация присоединяет 'ftp' к пути папки моментальных снимков при создании файлов моментальных снимков).  
  
    -   (Необязательно) **@ftp_login** -учетной записи входа, используемое при подключении к FTP-серверу.  
  
    -   (Необязательно) **@ftp_password** -пароль для ИМЕНИ входа.  
  
     Таким образом создается публикация, использующая протокол FTP. Дополнительные сведения см. в статье [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### Включение доставки моментальных снимков по протоколу FTP для публикации слиянием  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Укажите **@publication**, значение **true** для **@enabled_for_internet** и соответствующие значения для следующих параметров:  
  
    -   **@ftp_address** -адрес FTP-сервера, используемого для доставки моментального снимка.  
  
    -   (Необязательно) **@ftp_port** -порт, используемый FTP-сервера.  
  
    -   (Необязательно) **@ftp_subdirectory** — подкаталог FTP-каталога по умолчанию назначена учетная запись FTP. Например, если корневой сервер FTP — \\\ftpserver\home и хотите, чтобы моментальные снимки хранились в \\\ftpserver\home\snapshots, укажите **\snapshots\ftp** для **@ftp_subdirectory** (репликация присоединяет 'ftp' к пути папки моментальных снимков при создании файлов моментальных снимков).  
  
    -   (Необязательно) **@ftp_login** -учетной записи входа, используемое при подключении к FTP-серверу.  
  
    -   (Необязательно) **@ftp_password** -пароль для ИМЕНИ входа.  
  
     Таким образом создается публикация, использующая протокол FTP. Дополнительные сведения см. в статье [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### Создание подписки по запросу на публикацию моментальных снимков или публикацию транзакций, использующую доставку моментальных снимков по протоколу FTP  
  
1.  На подписчике в базе данных подписки выполните хранимую процедуру [sp_addpullsubscription](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md). Укажите значения параметров **@publisher** и **@publication**.  
  
    -   На подписчике в базе данных подписки выполните хранимую процедуру [sp_addpullsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md). Укажите **@publisher**, **@publisher_db**, **@publication**,  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] учетные данные Windows, под которыми агент распространителя на подписчике **@job_login** и **@job_password**, а значение **true** для **@use_ftp**.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) зарегистрировать подписку по запросу. Дополнительные сведения см. в разделе [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
#### Создание подписки по запросу на публикацию слиянием, использующую доставку моментальных снимков по протоколу FTP  
  
1.  На подписчике в базе данных подписки выполните хранимую процедуру [sp_addmergepullsubscription](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md). Укажите значения параметров **@publisher** и **@publication**.  
  
2.  На подписчике в базе данных подписки выполните хранимую процедуру [sp_addmergepullsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md). Укажите **@publisher**, **@publisher_db**, **@publication**, учетные данные Windows, с которыми работает агент распространителя на подписчике **@job_login** и **@job_password**, а значение **true** для **@use_ftp**.  
  
3.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergesubscription](../../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md) зарегистрировать подписку по запросу. Дополнительные сведения см. в разделе [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
#### Изменение одной или нескольких доставок моментальных снимков по протоколу FTP для публикации моментальных снимков или публикации транзакций  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md). Выберите одно из следующих значений в параметре **@property** и укажите новое значение этого параметра в параметре **@value**:  
  
    -   **ftp_address** -адрес FTP-сервера, используемого для доставки моментального снимка.  
  
    -   **ftp_port** -порт, используемый FTP-сервера.  
  
    -   **ftp_subdirectory** — подкаталог FTP-каталога по умолчанию, используемый моментальный снимок.  
  
    -   **ftp_login** -входа, используемого для подключения к FTP-серверу.  
  
    -   **ftp_password** -пароль для ИМЕНИ входа.  
  
2.  Повторите шаг 1 для каждого изменяемого параметра FTP-соединения (необязательно).  
  
3.  (Необязательно) Чтобы отключить доставку моментальных снимков по FTP, выполните [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) на издателе в базе данных публикации. Укажите значение **enabled_for_internet** для **@property** и значение **false** для **@value**.  
  
#### Изменение настроек доставки моментальных снимков по протоколу FTP для публикации слиянием  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md). Выберите одно из следующих значений в параметре **@property** и укажите новое значение этого параметра в параметре **@value**:  
  
    -   **ftp_address** -адрес FTP-сервера, используемого для доставки моментального снимка.  
  
    -   **ftp_port** -порт, используемый FTP-сервера.  
  
    -   **ftp_subdirectory** — подкаталог FTP-каталога по умолчанию, используемый моментальный снимок.  
  
    -   **ftp_login** -входа, используемого для подключения к FTP-серверу.  
  
    -   **ftp_password** -пароль для ИМЕНИ входа.  
  
2.  Повторите шаг 1 для каждого изменяемого параметра FTP-соединения (необязательно).  
  
3.  (Необязательно) Чтобы отключить доставку моментальных снимков по FTP, выполните [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md) на издателе в базе данных публикации. Укажите значение **enabled_for_internet** для **@property** и значение **false** для **@value**.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере создается публикация слиянием, позволяющая подписчикам получить доступ к данным моментального снимка с помощью протокола FTP. Для доступа к общей папке FTP подписчик должен использовать защищенное VPN-соединение. Для передачи значений имени входа и пароля используются переменные скриптов**sqlcmd** . Дополнительные сведения см. в разделе [Использование программы sqlcmd с переменными скрипта](../../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md).  
  
 [!code-sql[HowTo#sp_createmergepub_ftp](../../../relational-databases/replication/codesnippet/tsql/deliver-a-snapshot-throu_1.sql)]  
  
 В следующем примере создается подписка на публикацию слиянием, в которой подписчик получает моментальный снимок с помощью протокола FTP. Для доступа к общей папке FTP подписчик должен использовать защищенное VPN-соединение. Для передачи значений имени входа и пароля используются переменные скриптов**sqlcmd** . Дополнительные сведения см. в разделе [Использование программы sqlcmd с переменными скрипта](../../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md).  
  
 [!code-sql[HowTo#sp_createmergepullsub_ftp](../../../relational-databases/replication/codesnippet/tsql/deliver-a-snapshot-throu_2.sql)]  
  
 [!code-sql[HowTo#sp_createmergepullsubagent_ftp](../../../relational-databases/replication/codesnippet/tsql/deliver-a-snapshot-throu_3.sql)]  
  
## См. также:  
 [Основные понятия системных хранимых процедур репликации](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Передача моментальных снимков через FTP](../../../relational-databases/replication/transfer-snapshots-through-ftp.md)   
 [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Инициализация подписки с помощью моментального снимка](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  