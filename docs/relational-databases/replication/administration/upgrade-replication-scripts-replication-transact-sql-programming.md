---
title: "обновить скрипты репликации (программирование репликации на языке Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "скрипты [репликация SQL Server], обновление"
  - "обновление SQL Server, реплицируемые базы данных"
  - "обновление приложений репликации"
  - "репликация [SQL Server], написание скриптов"
  - "репликация [SQL Server], обновление"
  - "обновление реплицируемых баз данных"
ms.assetid: 0b8720bd-f339-4842-bc8f-b35a46f6d3ee
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# обновить скрипты репликации (программирование репликации на языке Transact-SQL)
  [!INCLUDE[tsql](../../../includes/tsql-md.md)] . Дополнительные сведения см. в разделе [понятия хранимых процедур репликации системы](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md).  
  
> [!IMPORTANT]  
>  Хотя обновление скриптов, выполняемых членами роли **sysadmin** , не является обязательным, рекомендуется внести в существующие скрипты изменения, описанные в настоящем разделе. Для всех агентов репликации следует указывать учетные записи, наделенные минимальным числом разрешений, как это описано в подразделе «Разрешения, необходимые для агентов» раздела [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
 Улучшения в области безопасности, повышающие управляемость разрешений за счет предоставления пользователю возможности явно задавать учетные записи [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, от которых выполняются задания агента репликации, затронут следующие хранимые процедуры в существующих скриптов.  
  
-   **sp_addpublication_snapshot**:  
  
     Теперь необходимо предоставить учетные данные Windows, как **@job_login** и **@job_password** при выполнении [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md) Чтобы создать задание, под которой выполняется агент моментальных снимков на распространителе.  
  
-   **sp_addpushsubscription_agent**:  
  
     Теперь следует выполнять [sp_addpushsubscription_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md) Чтобы явным образом добавить задание и учетные данные Windows (**@job_login** и **@job_password**) под которой запускается задание агента распространителя на распространителе. В версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] до [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]это выполнялось автоматически при создании принудительной подписки.  
  
-   **sp_addmergepushsubscription_agent**:  
  
     Теперь следует выполнять [sp_addmergepushsubscription_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md) Чтобы явным образом добавить задание и учетные данные Windows (**@job_login** и **@job_password**) под которой запускается задание агента слияния на распространителе. В версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] до [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]это выполнялось автоматически при создании принудительной подписки.  
  
-   **sp_addpullsubscription_agent**:  
  
     Теперь необходимо предоставить учетные данные Windows, как **@job_login** и **@job_password** при выполнении [sp_addpullsubscription_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md) Чтобы создать задание, под которой агент распространителя запускается на подписчике.  
  
-   **sp_addmergepullsubscription_agent**:  
  
     Теперь необходимо предоставить учетные данные Windows, как **@job_login** и **@job_password** при выполнении [sp_addmergepullsubscription_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) Чтобы создать задание, под которой выполняется агент слияния на подписчике.  
  
-   **sp_addlogreader_agent**:  
  
     Теперь следует выполнять [sp_addlogreader_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md) Чтобы вручную добавить задание и передать учетные данные Windows, под которым агент чтения журнала запускается на распространителе. В версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]это делалось автоматически при создании публикации транзакций.  
  
-   **sp_addqreader_agent**:  
  
     Теперь следует выполнять [sp_addqreader_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md) Чтобы вручную добавить задание и передать учетные данные Windows, под которыми агент чтения очереди работает на распространителе. В версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]это производилось автоматически при создании публикации транзакций, поддерживающей обновление посредством очередей.  
  
 В модели безопасности, представленные в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], агенты репликации всегда устанавливают соединение с локальным экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с проверкой подлинности Windows, используя учетные данные, предоставленные в **@job_name** и **@job_password**. Сведения о требованиях к учетным записям Windows, которые предназначены для выполнения заданий агента репликации, см. в разделе [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если учетные данные сохраняются в файле скрипта, то должна быть обеспечена защита этого файла.  
  
### Обновление скриптов настройки репликации моментальными снимками и публикацией транзакций  
  
1.  В существующем скрипте перед [sp_addpublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), выполнение [sp_addlogreader_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md) на издателе в базе данных публикации. Укажите учетные данные Windows, под которыми агент чтения журнала для **@job_name** и **@job_password**. Если агент будет использовать [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] проверки подлинности при подключении к издателю, необходимо также указать значение **0** для **@publisher_security_mode** и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сведения об имени входа **@publisher_login** и **@publisher_password**. Таким образом будет сформировано задание агента чтения журнала для базы данных публикации.  
  
    > [!NOTE]  
    >  Этот шаг предназначен только для публикаций транзакций и не обязателен для публикаций моментальных снимков.  
  
2.  (Необязательно) Прежде чем [sp_addpublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), выполнение [sp_addqreader_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md) на распространителе в базе данных распространителя. Укажите учетные данные Windows, под которыми агент чтения очереди для **@job_name** и **@job_password**. В результате этого будет сформировано задание агента чтения очереди для распространителя.  
  
    > [!NOTE]  
    >  Этот шаг обязателен только для публикаций транзакций, которые поддерживают подписчиков, обновляемых посредством очередей.  
  
3.  (Необязательно) Выполнение обновления [sp_addpublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md) Чтобы задать все значения по умолчанию для параметров, реализующих новые функции репликации.  
  
4.  После [sp_addpublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), выполнение [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md) на издателе в базе данных публикации. Укажите **@publication** учетные данные Windows, с которыми работает агент моментальных снимков и **@job_name** и **@job_password**. Если агент будет использовать [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] проверки подлинности при подключении к издателю, необходимо также указать значение **0** для **@publisher_security_mode** и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сведения об имени входа **@publisher_login** и **@publisher_password**. Будет создано задание агента моментальных снимков для публикации.  
  
5.  (Необязательно) Выполнение обновления [sp_addarticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) Чтобы задать все значения по умолчанию для параметров, реализующих новые функции репликации.  
  
### Обновление скриптов, которые добавляют подписки к публикациям моментальных снимков или публикациям транзакций  
  
1.  После вызова хранимой процедуры, которая создает подписку, обязательно выполните хранимую процедуру, формирующую задание агента распространителя для синхронизации подписки. Используемая хранимая процедура зависит от типа подписки.  
  
    -   Для подписки по запросу обновите выполнения [sp_addpullsubscription_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md) Чтобы предоставить учетные данные Windows, с которыми агент распространителя запускается на подписчике для **@job_name** и **@job_password**. Это необходимо сделать после выполнения [sp_addpullsubscription](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md). Дополнительные сведения см. в разделе [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
    -   Для принудительной подписки, выполните [sp_addpushsubscription_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md) на издателе. Укажите **@subscriber**, **@subscriber_db**, **@publication**, учетные данные Windows, под которыми агент распространителя запускается на распространителе для **@job_name** и **@job_password**, а также расписание для этого задания агента. Дополнительные сведения см. в статье [Specify Synchronization Schedules](../../../relational-databases/replication/specify-synchronization-schedules.md). Это необходимо сделать после выполнения [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Дополнительные сведения см. в статье [Create a Push Subscription](../../../relational-databases/replication/create-a-push-subscription.md).  
  
### Обновление скриптов настройки публикации слиянием  
  
1.  (Необязательно) В существующем скрипте обновите выполнения [sp_addmergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) Чтобы задать все значения по умолчанию для параметров, реализующих новые функции репликации.  
  
2.  После [sp_addmergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md), выполнение [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md) на издателе в базе данных публикации. Укажите **@publication** учетные данные Windows, с которыми работает агент моментальных снимков и **@job_name** и **@job_password**. Если агент будет использовать [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] проверки подлинности при подключении к издателю, необходимо также указать значение **0** для **@publisher_security_mode** и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сведения об имени входа **@publisher_login** и **@publisher_password**. Будет создано задание агента моментальных снимков для публикации.  
  
3.  (Необязательно) Выполнение обновления [sp_addmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Чтобы задать все значения по умолчанию для параметров, реализующих новые функции репликации.  
  
### Обновление скриптов, добавляющих подписки к публикации слиянием  
  
1.  После вызова хранимой процедуры, которая создает подписку, обязательно выполните хранимую процедуру, формирующую задание агента слияния для синхронизации подписки. Используемая хранимая процедура зависит от типа подписки.  
  
    -   Для подписки по запросу обновите выполнения [sp_addmergepullsubscription_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) Чтобы предоставить учетные данные Windows, при которых выполняется агент слияния на подписчике для **@job_name** и **@job_password**. Это необходимо сделать после выполнения [sp_addmergepullsubscription](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md). Дополнительные сведения см. в разделе [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
    -   Для принудительной подписки, выполните [sp_addmergepushsubscription_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md) на издателе. Укажите **@subscriber**, **@subscriber_db**, **@publication**, учетные данные Windows, с которыми работает агент слияния на распространителе **@job_name** и **@job_password**, а также расписание для этого задания агента. Дополнительные сведения см. в статье [Specify Synchronization Schedules](../../../relational-databases/replication/specify-synchronization-schedules.md). Это необходимо сделать после выполнения [sp_addmergesubscription](../../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md). Дополнительные сведения см. в статье [Create a Push Subscription](../../../relational-databases/replication/create-a-push-subscription.md).  
  
## Пример  
 Ниже приведен пример скрипта [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] , который создает публикацию транзакций для таблицы Product. Эта публикация поддерживает немедленное обновление с переключением на обновление отработки отказа. Значения по умолчанию были удалены для удобства чтения.  
  
 [!code-sql[HowTo#sp_createtranpub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_1.sql)]  
  
## Пример  
 Ниже приведено обновление предыдущего примера скрипта, который создает публикацию транзакций для запуска в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях. Эта публикация поддерживает немедленное обновление с переключением на обновление отработки отказа. Значения по умолчанию для новых параметров были объявлены явно.  
  
> [!NOTE]  
>  Учетные данные Windows предоставляются во время выполнения с помощью **sqlcmd** переменные сценария.  
  
 [!code-sql[HowTo#sp_createtranpub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_2.sql)]  
  
## Пример  
 Ниже приведен пример скрипта [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] , который создает публикацию слиянием для таблицы Customers. Значения по умолчанию были удалены для удобства чтения.  
  
 [!code-sql[HowTo#sp_createmergepub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_3.sql)]  
  
## Пример  
 Ниже приведен предыдущий пример скрипта для создания публикации слиянием, обновленный для запуска в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях. Значения по умолчанию для новых параметров были объявлены явно.  
  
> [!NOTE]  
>  Учетные данные Windows предоставляются во время выполнения с помощью **sqlcmd** переменные сценария.  
  
 [!code-sql[HowTo#sp_createmergepub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_4.sql)]  
  
## Пример  
 Ниже приведен пример скрипта [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] , который создает принудительную подписку для публикации транзакций. Значения по умолчанию были удалены для удобства чтения.  
  
 [!code-sql[HowTo#sp_createtranpushsub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_5.sql)]  
  
## Пример  
 Ниже приведен предыдущий пример скрипта для создания принудительной подписки для публикации транзакций, обновленный для запуска в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях. Значения по умолчанию для новых параметров были объявлены явно.  
  
> [!NOTE]  
>  Учетные данные Windows предоставляются во время выполнения с помощью **sqlcmd** переменные сценария.  
  
 [!code-sql[HowTo#sp_createtranpushsub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_6.sql)]  
  
## Пример  
 Ниже приведен пример скрипта [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] , который создает принудительную подписку для публикации слиянием. Значения по умолчанию были удалены для удобства чтения.  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_7.sql)]  
  
## Пример  
 Ниже приведен предыдущий пример скрипта, создающий принудительную подписку для публикации слиянием, обновленный для запуска в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях. Значения по умолчанию для новых параметров были объявлены явно.  
  
> [!NOTE]  
>  Учетные данные Windows предоставляются во время выполнения с помощью **sqlcmd** переменные сценария.  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_8.sql)]  
  
## Пример  
 Ниже приведен пример скрипта [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] , который создает подписку по запросу для публикации транзакций. Значения по умолчанию были удалены для удобства чтения.  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_7.sql)]  
  
## Пример  
 Ниже приведен предыдущий пример скрипта для создания подписки по запросу для публикации транзакций, обновленный для запуска в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях. Значения по умолчанию для новых параметров были объявлены явно.  
  
> [!NOTE]  
>  Учетные данные Windows предоставляются во время выполнения с помощью **sqlcmd** переменные сценария.  
  
 [!code-sql[HowTo#sp_createtranpullsub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_9.sql)]  
  
## Пример  
 Ниже приведен пример скрипта [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] , который создает подписку по запросу для публикации слиянием. Значения по умолчанию были удалены для удобства чтения.  
  
 [!code-sql[HowTo#sp_createmergepullsub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_10.sql)]  
  
## Пример  
 Ниже приведен предыдущий пример скрипта, создающий подписку по запросу для публикации слиянием, обновленный для запуска в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях. Значения по умолчанию для новых параметров были объявлены явно.  
  
> [!NOTE]  
>  Учетные данные Windows предоставляются во время выполнения с помощью **sqlcmd** переменные сценария.  
  
 [!code-sql[HowTo#sp_createmergepullsub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_11.sql)]  
  
## См. также:  
 [Создание публикации](../../../relational-databases/replication/publish/create-a-publication.md)   
 [Создание принудительной подписки](../../../relational-databases/replication/create-a-push-subscription.md)   
 [Создание подписки по запросу](../../../relational-databases/replication/create-a-pull-subscription.md)   
 [Просмотр и изменение параметров безопасности репликации](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [MSSQL_ENG021797](../../../relational-databases/replication/mssql-eng021797.md)   
 [MSSQL_ENG021798](../../../relational-databases/replication/mssql-eng021798.md)   
 [Основные понятия системных хранимых процедур репликации](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Обновление реплицируемых баз данных](../../../database-engine/install-windows/upgrade-replicated-databases.md)  
  
  