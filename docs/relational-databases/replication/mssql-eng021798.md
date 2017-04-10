---
title: "MSSQL_ENG021798 | Microsoft Docs"
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
  - "MSSQL_ENG021798, ошибка"
ms.assetid: 596f5092-75ab-4a19-8582-588687c7b089
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# MSSQL_ENG021798
    
## Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21798|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Перед продолжением необходимо добавить задание агента '%s' с помощью '%s'. См. документацию по "%s".»|  
  
## Объяснение  
 Чтобы создать публикацию, необходимо быть членом **sysadmin** фиксированной серверной роли на издателе или членом **db_owner** фиксированной роли базы данных в базе данных публикации. Если вы являетесь членом **db_owner** роли, эта ошибка возникает в том случае, если:  
  
-   Выполняются скрипты из [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Модель безопасности в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]изменилась, поэтому эти скрипты необходимо обновить.  
  
-   Хранимая процедура **sp_addpublication** выполняется перед выполнением [sp_addlogreader_agent & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md). Это относится ко всем публикациям транзакций.  
  
-   Хранимая процедура **sp_addpublication** выполняется перед выполнением [sp_addqreader_agent & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md). Это относится к публикациям транзакций, которые включены для очереди обновляемых подписок (значение TRUE для **@allow_queued_tran** параметр **sp_addpublication**).  
  
 Хранимые процедуры **sp_addlogreader_agent** и **sp_addqreader_agent** каждый создать задание агента и позволяют задавать [!INCLUDE[msCoName](../../includes/msconame-md.md)] учетной записи Windows, под которой запускается агент. Для пользователей в **sysadmin** роли, задания агентов создаются неявно при **sp_addlogreader_agent** и **sp_addqreader_agent** не выполняются; агенты запускаются в контексте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетная запись службы агента на распространителе. Хотя **sp_addlogreader_agent** и **sp_addqreader_agent** не являются обязательными для пользователей в **sysadmin** роли, это безопасности рекомендуется задать отдельную учетную запись для агентов. Дополнительные сведения см. в статье [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## Действие пользователя  
 Убедитесь в том, что процедуры выполняются в правильном порядке. Дополнительные сведения см. в статье [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md). При наличии скриптов репликации, оставшихся от предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], обновите их, включив хранимые процедуры и параметры, необходимые для [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий. Дополнительные сведения см. в разделе [скрипты обновления репликации & #40; Программирование репликации Transact-SQL & #41;](../../relational-databases/replication/administration/upgrade-replication-scripts-replication-transact-sql-programming.md).  
  
## См. также:  
 [Ошибки и события ссылку & #40; Репликация & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  