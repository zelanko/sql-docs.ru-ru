---
title: Доставка моментального снимка через FTP | Документация Майкрософт
ms.custom: ''
ms.date: 11/20/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], FTP snapshots
- FTP snapshots [SQL Server replication]
- snapshot replication [SQL Server], FTP
ms.assetid: 99872c4f-40ce-4405-8fd4-44052d3bd827
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c6ec9ac5c4e868a9022a11cc153c9638cab737dc
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "71710991"
---
# <a name="deliver-a-snapshot-through-ftp"></a>Доставка моментального снимка через FTP
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описывается доставка моментального снимка по протоколу FTP в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  

По умолчанию моментальные снимки сохраняются в папках, определенных как совместно используемые папки в формате универсального соглашения об именовании (UNC). Репликация также позволяет задать общий FTP-ресурс вместо общего UNC-ресурса. Для использования FTP необходимо настроить FTP-сервер, а затем настроить публикацию и одну или несколько подписок для использования FTP. Сведения о настройке FTP-сервера см. в документации по службам IIS (Internet Information Services). При задании сведений об FTP для публикации подписки на эту публикацию будут по умолчанию использовать FTP. Протокол FTP используется только при веб-синхронизации, когда компьютер, на котором запущены службы IIS, отделен от распространителя брандмауэром. В этом случае протокол FTP может использоваться для передачи моментального снимка с распространителя и компьютера, на котором выполняются службы IIS. (Моментальный снимок всегда передается подписчику по протоколу HTTPS.)  
  
> [!IMPORTANT]  
>  Рекомендуется использовать проверку подлинности Microsoft Windows и общий UNC-ресурс вместо общего FTP-ресурса, так как пароли FTP необходимо сохранять, и они передаются с подписчика или с компьютера, на котором запущены службы IIS с использованием веб-синхронизации, на FTP-сервер без шифрования. Кроме этого, поскольку одна учетная запись управляет доступом к хранилищу моментального снимка, невозможно гарантировать, что подписчик на фильтруемую публикацию слиянием имеет доступ только к файлам моментальных снимков из своей секции данных.  
  

## <a name="limitations-and-restrictions"></a>Ограничения  
  
-   Агент моментальных снимков должен иметь разрешения на запись в указанный каталог, а агент распространителя или агент слияния должен иметь разрешения на чтение из этого каталога. При использовании подписок по запросу следует указать в качестве пути, соответствующего соглашению об универсальном назначении имен (UNC), общий каталог, например \\\ftpserver\home\snapshots. Дополнительные сведения см. в статье [Организация безопасности папки моментальных снимков](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
## <a name="prerequisites"></a>предварительные требования  
  
-   Для передачи файлов моментальных снимков с использованием протокола FTP (File Transfer Protocol) необходимо настроить FTP-сервер. Дополнительные сведения см. в документации служб IIS [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
 В целях повышения безопасности рекомендуется реализовать частную виртуальную сеть (VPN) при доставке моментальных снимков по протоколу FTP через Интернет. Дополнительные сведения см. в статье [Публикация данных через Интернет с помощью виртуальных частных сетей](../../../relational-databases/replication/publish-data-over-the-internet-using-vpn.md).  
  
 Для обеспечения безопасности рекомендуется запретить анонимный вход на FTP-сервер. Агент моментальных снимков должен иметь разрешения на запись в указанный каталог, а агент распространителя или агент слияния должен иметь разрешения на чтение из этого каталога. При использовании подписок по запросу следует указать в качестве пути, соответствующего соглашению об универсальном назначении имен (UNC), общий каталог, например \\\ftpserver\home\snapshots. Дополнительные сведения см. в статье [Организация безопасности папки моментальных снимков](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
 По возможности запрашивайте у пользователей учетные данные в среде выполнения приложения. Если учетные данные хранятся в файле скрипта, необходимо защитить этот файл.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 После настройки FTP-сервера укажите каталог и сведения безопасности для этого сервера в диалоговом окне **Свойства публикации — \<публикация>** . Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-ftp-information"></a>Указание сведений FTP  
  
1.  В диалоговом окне **Свойства публикации — \<публикация>** установите флажок **Разрешить подписчикам загружать файлы моментальных снимков по протоколу FTP** на одной из следующих страниц:  
  
    -   Страница **Моментальный снимок FTP** для публикаций моментальных снимков, публикаций транзакций и публикаций слиянием с издателей, использующих версии, предшествующие [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
    -   Страница **Моментальный снимок FTP и Интернет** для публикаций слиянием с издателей, использующих [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более позднюю версию.  
  
2.  Укажите значения для свойств **Имя FTP-сервера**, **Номер порта**, **Путь из корневой папки FTP**, **Имя входа**и **Пароль**.  
  
     Например, если корневой каталог FTP-сервера является \\\ftpserver\home и нужно, чтобы моментальные снимки хранились в \\\ftpserver\home\snapshots, укажите значение \snapshots\ftp для свойства **Путь из корневой папки FTP** (репликация присоединяет ftp к пути папки моментальных снимков при создании файлов моментальных снимков).  
  
3.  Укажите, что агент моментальных снимков должен записывать файлы моментальных снимков в каталог, указанный на шаге 2. Например, чтобы агент моментальных снимков записывал файлы моментальных снимков в \\\ftpserver\home\snapshots\ftp, следует указать путь \\\ftpserver\home\snapshots в одном из двух мест:  
  
    -   Расположение моментальных снимков по умолчанию для распространителя, связанного с этой публикацией.    
    -   Альтернативное расположение папки моментальных снимков для данной публикации. Если моментальный снимок сжимается, необходимо альтернативное расположение папки.  

Дополнительные сведения об изменении свойств расположения папки моментальных снимков см. в разделе [Параметры моментальных снимков](../snapshot-options.md).
  

4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 Можно установить параметр, который сделает доступными файлы моментальных снимков на сервере, а настройки FTP можно изменить программно с помощью хранимых процедур репликации. Эта процедура зависит от типа публикации. Доставка моментальных снимков по протоколу FTP используется только с подписками по запросу.  
  
#### <a name="to-enable-ftp-snapshot-delivery-for-a-snapshot-or-transactional-publication"></a>Включение доставки моментальных снимков по протоколу FTP для публикации моментальных снимков или публикации транзакций  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addpublication](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md). Укажите параметр `@publication`, значение **true** в параметре `@enabled_for_internet` и соответствующие значения для следующих параметров:  
  
    -   `@ftp_address` — адрес FTP-сервера, который используется для доставки моментального снимка;  
  
    -   `@ftp_port` — порт FTP-сервера (необязательно).  
  
    -   `@ftp_subdirectory` — вложенный каталог в каталоге FTP по умолчанию, назначенном для имени входа на FTP-сервер (необязательно). Например, если корневой каталог FTP-сервера — \\\ftpserver\home и нужно, чтобы моментальные снимки хранились в каталоге \\\ftpserver\home\snapshot, укажите значение **\snapshots\ftp** в параметре `@ftp_subdirectory` (репликация присоединяет "ftp" к пути папки моментальных снимков при создании файлов моментальных снимков).  
  
    -   `@ftp_login` — учетная запись входа, используемая для соединения с FTP-сервером (необязательно).  
  
    -   `@ftp_password` — пароль для имени входа FTP (необязательно).  
  
     Таким образом создается публикация, использующая протокол FTP. Дополнительные сведения см. в разделе [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### <a name="to-enable-ftp-snapshot-delivery-for-a-merge-publication"></a>Включение доставки моментальных снимков по протоколу FTP для публикации слиянием  
  
1.  На издателе в базе данных публикации выполните процедуру [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Укажите параметр `@publication`, значение **true** в параметре `@enabled_for_internet` и соответствующие значения для следующих параметров:  
  
    -   `@ftp_address` — адрес FTP-сервера, который используется для доставки моментального снимка;  
  
    -   `@ftp_port` — порт FTP-сервера (необязательно).  
  
    -   `@ftp_subdirectory` — вложенный каталог в каталоге FTP по умолчанию, назначенном для имени входа на FTP-сервер (необязательно). Например, если корневой каталог FTP-сервера — \\\ftpserver\home и нужно, чтобы моментальные снимки хранились в каталоге \\\ftpserver\home\snapshot, укажите значение **\snapshots\ftp** в параметре `@ftp_subdirectory` (репликация присоединяет "ftp" к пути папки моментальных снимков при создании файлов моментальных снимков).  
  
    -   `@ftp_login` — учетная запись входа, используемая для соединения с FTP-сервером (необязательно).  
  
    -   `@ftp_password` — пароль для имени входа FTP (необязательно).  
  
     Таким образом создается публикация, использующая протокол FTP. Дополнительные сведения см. в разделе [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### <a name="to-create-a-pull-subscription-to-a-snapshot-or-transactional-publication-that-uses-ftp-snapshot-delivery"></a>Создание подписки по запросу на публикацию моментальных снимков или публикацию транзакций, использующую доставку моментальных снимков по протоколу FTP  
  
1.  На подписчике в базе данных подписки выполните хранимую процедуру [sp_addpullsubscription](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md). Укажите параметры `@publisher` и `@publication`.  
  
    -   На подписчике в базе данных подписки выполните хранимую процедуру [sp_addpullsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md). Укажите параметры `@publisher`, `@publisher_db`, `@publication`, учетные данные [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, с которыми выполняется агент распространения в подписчике, в параметрах `@job_login` и `@job_password`, а также значение **true** в параметре `@use_ftp`.  
  
2.  Чтобы зарегистрировать подписку по запросу, выполните на издателе в базе данных публикации хранимую процедуру [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) . Дополнительные сведения см. в статье [Создание подписки по запросу](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
#### <a name="to-create-a-pull-subscription-to-a-merge-publication-that-uses-ftp-snapshot-delivery"></a>Создание подписки по запросу на публикацию слиянием, использующую доставку моментальных снимков по протоколу FTP  
  
1.  В базе данных подписки на издателе выполните процедуру [sp_addmergepushsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md). Укажите параметры `@publisher` и `@publication`.  
  
2.  На подписчике в базе данных подписки выполните хранимую процедуру [sp_addmergepullsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md). Укажите параметры `@publisher`, `@publisher_db`, `@publication`, учетные данные Windows, с которыми выполняется агент распространения в подписчике, в параметрах `@job_login` и `@job_password`, а также значение `true` в параметре `@use_ftp`.  
  
3.  Чтобы зарегистрировать подписку по запросу, выполните на издателе в базе данных публикации хранимую процедуру [sp_addmergesubscription](../../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md) . Дополнительные сведения см. в статье [Создание подписки по запросу](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
#### <a name="to-change-one-or-more-ftp-snapshot-delivery-settings-for-a-snapshot-or-transactional-publication"></a>Изменение одной или нескольких доставок моментальных снимков по протоколу FTP для публикации моментальных снимков или публикации транзакций  
  
1.  На издателе в базе данных публикации выполните процедуру [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md). Укажите одно из следующих значений в параметре `@property` и новое значение этого параметра в параметре `@value`:  
  
    -   `ftp_address ` — адрес FTP-сервера, который используется для доставки моментального снимка;  
  
    -   `ftp_port` — порт FTP-сервера;  
  
    -   `ftp_subdirectory` — подкаталог FTP-каталога по умолчанию, в котором хранится моментальный снимок;  
  
    -   `ftp_login` — имя входа для подключения к FTP-серверу;  
  
    -   `ftp_password` — пароль для имени входа.  
  
2.  Повторите шаг 1 для каждого изменяемого параметра FTP-соединения (необязательно).  
  
3.  Чтобы отключить доставку моментальных снимков по протоколу FTP, выполните на издателе в базе данных публикации хранимую процедуру [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) (необязательно). Укажите значение `enabled_for_internet` в параметре `@property` и значение `false` в параметре `@value`.  
  
#### <a name="to-change-ftp-snapshot-delivery-settings-for-a-merge-publication"></a>Изменение настроек доставки моментальных снимков по протоколу FTP для публикации слиянием  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md). Укажите одно из следующих значений в параметре `@property` и новое значение этого параметра в параметре `@value`:  
  
    -   `ftp_address` — адрес FTP-сервера, который используется для доставки моментального снимка;  
  
    -   `ftp_port` — порт FTP-сервера;  
  
    -   `ftp_subdirectory` — подкаталог FTP-каталога по умолчанию, в котором хранится моментальный снимок;  
  
    -   `ftp_login` — имя входа для подключения к FTP-серверу;  
  
    -   `ftp_password` — пароль для имени входа.  
  
2.  Повторите шаг 1 для каждого изменяемого параметра FTP-соединения (необязательно).  
  
3.  Чтобы отключить доставку моментальных снимков по протоколу FTP, выполните на издателе в базе данных публикации хранимую процедуру [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md) (необязательно). Укажите значение `enabled_for_internet` в параметре `@property` и значение `false` в параметре `@value`.  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере создается публикация слиянием, позволяющая подписчикам получить доступ к данным моментального снимка с помощью протокола FTP. Для доступа к общей папке FTP подписчик должен использовать защищенное VPN-соединение. Для передачи значений имени входа и пароля используются переменные скриптов**sqlcmd** . Дополнительные сведения см. в статье [Использование программы sqlcmd с переменными скрипта](../../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md).  
  
 [!code-sql[HowTo#sp_createmergepub_ftp](../../../relational-databases/replication/codesnippet/tsql/deliver-a-snapshot-throu_1.sql)]  
  
 В следующем примере создается подписка на публикацию слиянием, в которой подписчик получает моментальный снимок с помощью протокола FTP. Для доступа к общей папке FTP подписчик должен использовать защищенное VPN-соединение. Для передачи значений имени входа и пароля используются переменные скриптов**sqlcmd** . Дополнительные сведения см. в статье [Использование программы sqlcmd с переменными скрипта](../../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md).  
  
 [!code-sql[HowTo#sp_createmergepullsub_ftp](../../../relational-databases/replication/codesnippet/tsql/deliver-a-snapshot-throu_2.sql)]  
  
 [!code-sql[HowTo#sp_createmergepullsubagent_ftp](../../../relational-databases/replication/codesnippet/tsql/deliver-a-snapshot-throu_3.sql)]  
  
## <a name="see-also"></a>См. также:  
 [Replication System Stored Procedures Concepts](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Инициализация подписки с помощью моментального снимка](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
