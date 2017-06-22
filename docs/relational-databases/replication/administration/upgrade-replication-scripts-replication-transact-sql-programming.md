---
title: "Обновление скриптов репликации (программирование репликации на языке Transact-SQL) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- scripts [SQL Server replication], upgrading
- upgrading SQL Server, replicated databases
- upgrading replication applications
- replication [SQL Server], scripting
- replication [SQL Server], upgrading
- upgrading replicated databases
ms.assetid: 0b8720bd-f339-4842-bc8f-b35a46f6d3ee
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5ef24ad75fa3a8d6e2e181d436dd878a133135b6
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="upgrade-replication-scripts-replication-transact-sql-programming"></a>обновить скрипты репликации (программирование репликации на языке Transact-SQL)
  Настройка топологии репликации программным способом возможна при помощи файлов скриптов на языке[!INCLUDE[tsql](../../../includes/tsql-md.md)] . Дополнительные сведения см. в статье [Основные понятия системных хранимых процедур репликации](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md).  
  
> [!IMPORTANT]  
>  Хотя обновление скриптов, выполняемых членами роли **sysadmin** , не является обязательным, рекомендуется внести в существующие скрипты изменения, описанные в настоящем разделе. Для всех агентов репликации следует указывать учетные записи, наделенные минимальным числом разрешений, как это описано в подразделе «Разрешения, необходимые для агентов» раздела [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
 Улучшения в области безопасности, повышающие управляемость разрешений за счет предоставления пользователю возможности явно задавать учетные записи [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, от которых выполняются задания агента репликации, затронут следующие хранимые процедуры в существующих скриптов.  
  
-   **sp_addpublication_snapshot**:  
  
     Теперь при вызове хранимой процедуры [sp_addpublication_snapshot (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md) для формирования задания пользователь должен в параметрах **@job_login** и **@job_password** передать учетные данные Windows, с которыми будет запускаться агент моментальных снимков на распространителе.  
  
-   **sp_addpushsubscription_agent**:  
  
     Теперь пользователь должен выполнять хранимую процедуру [sp_addpushsubscription_agent (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md), чтобы явным образом добавить задание и передать учетные данные Windows(в параметрах **@job_login** и **@job_password**), с которыми задание агента распространителя будет выполняться на распространителе. В версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] до [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]это выполнялось автоматически при создании принудительной подписки.  
  
-   **sp_addmergepushsubscription_agent**:  
  
     Теперь пользователь должен выполнить процедуру [sp_addpushsubscription_agent (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md), чтобы явным образом добавить задание и передать учетные данные Windows (в параметрах **@job_login** и **@job_password**), с использованием которых задание агента слияния будет выполняться на распространителе. В версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] до [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]это выполнялось автоматически при создании принудительной подписки.  
  
-   **sp_addpullsubscription_agent**:  
  
     Теперь при вызове хранимой процедуры [sp_addpullsubscription_agent (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md) для формирования задания пользователь должен в параметрах **@job_login** и **@job_password** передать учетные данные Windows, с которыми будет запускаться агент распространителя на подписчике.  
  
-   **sp_addmergepullsubscription_agent**:  
  
     Теперь при вызове хранимой процедуры [sp_addmergepullsubscription_agent (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) для формирования задания пользователь должен в параметрах **@job_login** и **@job_password** передать учетные данные Windows, с которыми будет запускаться агент слияния на подписчике.  
  
-   **sp_addlogreader_agent**:  
  
     Теперь пользователь должен вызвать хранимую процедуру [sp_addlogreader_agent (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md), чтобы вручную добавить задание и передать учетные данные Windows, с использованием которых агент чтения журнала будет выполняться на распространителе. В версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]это делалось автоматически при создании публикации транзакций.  
  
-   **sp_addqreader_agent**:  
  
     Теперь пользователь должен вызвать хранимую процедуру [sp_addlogreader_agent (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md), чтобы вручную добавить задание и передать учетные данные Windows, с использованием которых агент чтения очереди будет выполняться на распространителе. В версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]это производилось автоматически при создании публикации транзакций, поддерживающей обновление посредством очередей.  
  
 В модели безопасности, которая реализована в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], агенты репликации всегда устанавливают соединение с локальным экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с использованием проверки подлинности Windows. При этом они пользуются учетными данными, переданными в параметрах **@job_name** @job_login **@job_password**. Сведения о требованиях к учетным записям Windows, которые предназначены для выполнения заданий агента репликации, см. в разделе [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если учетные данные сохраняются в файле скрипта, то должна быть обеспечена защита этого файла.  
  
### <a name="to-upgrade-scripts-that-configure-a-snapshot-or-transactional-publication"></a>Обновление скриптов настройки репликации моментальными снимками и публикацией транзакций  
  
1.  В существующем скрипте перед [sp_addpublication (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md) выполните хранимую процедуру [sp_addlogreader_agent (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md) в издателе в базе данных публикации. Укажите в параметрах **@job_name** @job_login **@job_password**. Если агент при соединении с издателем будет использовать проверку подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , то необходимо также присвоить значение **0** параметру **@publisher_security_mode** и передать сведения об имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в качестве значений параметров **@publisher_login** @job_login **@publisher_password**. Таким образом будет сформировано задание агента чтения журнала для базы данных публикации.  
  
    > [!NOTE]  
    >  Этот шаг предназначен только для публикаций транзакций и не обязателен для публикаций моментальных снимков.  
  
2.  (Необязательно.) Перед [sp_addpublication (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md) выполните [sp_addlogreader_agent (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md) в издателе в базе данных публикации. Укажите в параметрах **@job_name** @job_login **@job_password**. В результате этого будет сформировано задание агента чтения очереди для распространителя.  
  
    > [!NOTE]  
    >  Этот шаг обязателен только для публикаций транзакций, которые поддерживают подписчиков, обновляемых посредством очередей.  
  
3.  Чтобы установить для параметров, реализующих новые функции репликации, значения отличные от принятых по умолчанию, обновите код вызова процедуры [sp_addpublication (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md) (необязательно).  
  
4.  После [sp_addpublication (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md) выполните [sp_addpublication_snapshot (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md) в издателе в базе данных публикации. Укажите параметр **@publication** и учетные данные Windows, с которыми будет выполняться агент моментальных снимков, в параметрах **@job_name** @job_login **@job_password**. Если агент при соединении с издателем будет использовать проверку подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , то необходимо также присвоить значение **0** параметру **@publisher_security_mode** и передать сведения об имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в качестве значений параметров **@publisher_login** @job_login **@publisher_password**. Будет создано задание агента моментальных снимков для публикации.  
  
5.  Чтобы установить для параметров, реализующих новые функции репликации, значения, отличные от принятых по умолчанию, обновите код вызова процедуры [sp_addarticle (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) (необязательно).  
  
### <a name="to-upgrade-scripts-that-add-subscriptions-to-a-snapshot-or-transactional-publication"></a>Обновление скриптов, которые добавляют подписки к публикациям моментальных снимков или публикациям транзакций  
  
1.  После вызова хранимой процедуры, которая создает подписку, обязательно выполните хранимую процедуру, формирующую задание агента распространителя для синхронизации подписки. Используемая хранимая процедура зависит от типа подписки.  
  
    -   Для подписки по запросу обновите вызов процедуры [sp_addpullsubscription_agent (Transact-SQL) ](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md), указав в параметрах **@job_name** и **@job_password** учетные данные Windows, с использованием которых агент распространителя будет запускаться на подписчике. Это необходимо сделать после вызова хранимой процедуры [sp_addpullsubscription](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md). Дополнительные сведения см. в разделе [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
    -   Для принудительной подписки выполните процедуру [sp_addpushsubscription_agent (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md) на издателе. Укажите параметр **@subscriber**, **@subscriber_db**, **@publication**, учетные данные Windows, от которых агент распространителя будет запускаться на распространителе, в параметрах **@job_name** @job_login **@job_password**, а также расписание для этого задания. Дополнительные сведения см. в статье [Specify Synchronization Schedules](../../../relational-databases/replication/specify-synchronization-schedules.md). Это необходимо сделать после вызова процедуры [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Дополнительные сведения см. в статье [Create a Push Subscription](../../../relational-databases/replication/create-a-push-subscription.md).  
  
### <a name="to-upgrade-scripts-that-configure-a-merge-publication"></a>Обновление скриптов настройки публикации слиянием  
  
1.  В существующем скрипте обновите вызов процедуры [sp_addmergepublication (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md), указав для новых параметров, реализующих новые функции репликации, значения, отличные от заданных по умолчанию (необязательно).  
  
2.  После [sp_addmergepublication (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) выполните [sp_addpublication_snapshot (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md) в издателе в базе данных публикации. Укажите параметр **@publication** и учетные данные Windows, с которыми будет выполняться агент моментальных снимков, в параметрах **@job_name** @job_login **@job_password**. Если агент при соединении с издателем будет использовать проверку подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , то необходимо также присвоить значение **0** параметру **@publisher_security_mode** и передать сведения об имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в качестве значений параметров **@publisher_login** @job_login **@publisher_password**. Будет создано задание агента моментальных снимков для публикации.  
  
3.  (Необязательно.) Чтобы установить для параметров, реализующих новые функции репликации, значения, отличные от принятых по умолчанию, обновите код вызова процедуры [sp_addmergearticle (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).  
  
### <a name="to-upgrade-scripts-that-add-subscriptions-to-a-merge-publication"></a>Обновление скриптов, добавляющих подписки к публикации слиянием  
  
1.  После вызова хранимой процедуры, которая создает подписку, обязательно выполните хранимую процедуру, формирующую задание агента слияния для синхронизации подписки. Используемая хранимая процедура зависит от типа подписки.  
  
    -   Для подписки по запросу обновите вызов процедуры [sp_addmergepullsubscription_agent (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md), указав в параметрах **@job_name** и **@job_password** учетные данные Windows, с использованием которых агент слияния будет запускаться на подписчике. Это необходимо сделать после вызова процедуры [sp_addmergepullsubscription](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md). Дополнительные сведения см. в разделе [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
    -   Для принудительной подписки, выполните процедуру [sp_addmergepushsubscription_agent (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md) на издателе. Укажите параметр **@subscriber**, **@subscriber_db**, **@publication**, в параметрах **@job_name** @job_login **@job_password**, а также расписание для этого задания. Дополнительные сведения см. в статье [Specify Synchronization Schedules](../../../relational-databases/replication/specify-synchronization-schedules.md). Это необходимо сделать после вызова хранимой процедуры [sp_addmergesubscription](../../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md). Дополнительные сведения см. в статье [Create a Push Subscription](../../../relational-databases/replication/create-a-push-subscription.md).  
  
## <a name="example"></a>Пример  
 Ниже приведен пример скрипта [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] , который создает публикацию транзакций для таблицы Product. Эта публикация поддерживает немедленное обновление с переключением на обновление отработки отказа. Значения по умолчанию были удалены для удобства чтения.  
  
 [!code-sql[HowTo#sp_createtranpub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_1.sql)]  
  
## <a name="example"></a>Пример  
 Ниже приведено обновление предыдущего примера скрипта, который создает публикацию транзакций для запуска в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях. Эта публикация поддерживает немедленное обновление с переключением на обновление отработки отказа. Значения по умолчанию для новых параметров были объявлены явно.  
  
> [!NOTE]  
>  Учетные данные Windows предоставляются во время выполнения с помощью переменных сценария **sqlcmd** .  
  
 [!code-sql[HowTo#sp_createtranpub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_2.sql)]  
  
## <a name="example"></a>Пример  
 Ниже приведен пример скрипта [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] , который создает публикацию слиянием для таблицы Customers. Значения по умолчанию были удалены для удобства чтения.  
  
 [!code-sql[HowTo#sp_createmergepub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_3.sql)]  
  
## <a name="example"></a>Пример  
 Ниже приведен предыдущий пример скрипта для создания публикации слиянием, обновленный для запуска в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях. Значения по умолчанию для новых параметров были объявлены явно.  
  
> [!NOTE]  
>  Учетные данные Windows предоставляются во время выполнения с помощью переменных сценария **sqlcmd** .  
  
 [!code-sql[HowTo#sp_createmergepub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_4.sql)]  
  
## <a name="example"></a>Пример  
 Ниже приведен пример скрипта [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] , который создает принудительную подписку для публикации транзакций. Значения по умолчанию были удалены для удобства чтения.  
  
 [!code-sql[HowTo#sp_createtranpushsub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_5.sql)]  
  
## <a name="example"></a>Пример  
 Ниже приведен предыдущий пример скрипта для создания принудительной подписки для публикации транзакций, обновленный для запуска в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях. Значения по умолчанию для новых параметров были объявлены явно.  
  
> [!NOTE]  
>  Учетные данные Windows предоставляются во время выполнения с помощью переменных сценария **sqlcmd** .  
  
 [!code-sql[HowTo#sp_createtranpushsub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_6.sql)]  
  
## <a name="example"></a>Пример  
 Ниже приведен пример скрипта [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] , который создает принудительную подписку для публикации слиянием. Значения по умолчанию были удалены для удобства чтения.  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_7.sql)]  
  
## <a name="example"></a>Пример  
 Ниже приведен предыдущий пример скрипта, создающий принудительную подписку для публикации слиянием, обновленный для запуска в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях. Значения по умолчанию для новых параметров были объявлены явно.  
  
> [!NOTE]  
>  Учетные данные Windows предоставляются во время выполнения с помощью переменных сценария **sqlcmd** .  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_8.sql)]  
  
## <a name="example"></a>Пример  
 Ниже приведен пример скрипта [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] , который создает подписку по запросу для публикации транзакций. Значения по умолчанию были удалены для удобства чтения.  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_7.sql)]  
  
## <a name="example"></a>Пример  
 Ниже приведен предыдущий пример скрипта для создания подписки по запросу для публикации транзакций, обновленный для запуска в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях. Значения по умолчанию для новых параметров были объявлены явно.  
  
> [!NOTE]  
>  Учетные данные Windows предоставляются во время выполнения с помощью переменных сценария **sqlcmd** .  
  
 [!code-sql[HowTo#sp_createtranpullsub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_9.sql)]  
  
## <a name="example"></a>Пример  
 Ниже приведен пример скрипта [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] , который создает подписку по запросу для публикации слиянием. Значения по умолчанию были удалены для удобства чтения.  
  
 [!code-sql[HowTo#sp_createmergepullsub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_10.sql)]  
  
## <a name="example"></a>Пример  
 Ниже приведен предыдущий пример скрипта, создающий подписку по запросу для публикации слиянием, обновленный для запуска в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях. Значения по умолчанию для новых параметров были объявлены явно.  
  
> [!NOTE]  
>  Учетные данные Windows предоставляются во время выполнения с помощью переменных сценария **sqlcmd** .  
  
 [!code-sql[HowTo#sp_createmergepullsub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_11.sql)]  
  
## <a name="see-also"></a>См. также:  
 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)   
 [Create a Push Subscription](../../../relational-databases/replication/create-a-push-subscription.md)   
 [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md)   
 [Просмотр и изменение параметров безопасности репликации](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [MSSQL_ENG021797](../../../relational-databases/replication/mssql-eng021797.md)   
 [MSSQL_ENG021798](../../../relational-databases/replication/mssql-eng021798.md)   
 [Replication System Stored Procedures Concepts](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Обновление реплицируемых баз данных](../../../database-engine/install-windows/upgrade-replicated-databases.md)  
  
  
