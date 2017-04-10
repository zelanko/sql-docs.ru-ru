---
title: "MSSQL_ENG021797 | Microsoft Docs"
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
  - "MSSQL_ENG021797, ошибка"
ms.assetid: 54d83a1e-43fd-449c-a2b2-fdda2609a534
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# MSSQL_ENG021797
    
## Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21797|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|"%s" должно быть допустимым именем входа Windows, представленным в следующем виде: "КОМПЬЮТЕР\имя_входа" или "ДОМЕН\имя_входа". См. документацию по "%s".»|  
  
## Объяснение  
 Эта ошибка возникает в следующих хранимых процедур репликации, если значение, указанное для **@job_login** параметр имеет значение null или не является допустимым. Эта ошибка может возникнуть, если член **db_owner** фиксированной роли базы данных запускает сценарии из предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Модель безопасности в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]изменилась, поэтому эти скрипты необходимо обновить.  
  
-   [sp_addlogreader_agent & #40; Transact-SQL и #41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)  
  
-   [sp_addqreader_agent & #40; Transact-SQL и #41;](../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md)  
  
-   [sp_addpublication_snapshot & #40; Transact-SQL и #41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)  
  
-   [sp_addpushsubscription_agent & #40; Transact-SQL и #41;](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md)  
  
-   [sp_addpullsubscription_agent & #40; Transact-SQL и #41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)  
  
-   [sp_addmergepushsubscription_agent & #40; Transact-SQL и #41;](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md)  
  
-   [sp_addmergepullsubscription_agent & #40; Transact-SQL и #41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)  
  
 Эти хранимые процедуры могут выполняться членом **sysadmin** предопределенной роли сервера на соответствующем сервере или членом **db_owner** фиксированной роли базы данных в соответствующей базе данных. Каждая из этих хранимых процедур создает задание для агента и позволяет задать учетную запись [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, под которой запускается агент. Для пользователей в **sysadmin** роли, задания агентов создаются неявно даже, если не указана учетная запись Windows (если учетная запись указана, она должна быть допустимой); агенты запускаются в контексте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетная запись службы агента на соответствующем сервере. Несмотря на то, что учетная запись не требуется, в целях безопасности рекомендуется задать отдельную учетную запись для каждого агента. Дополнительные сведения см. в статье [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## Действие пользователя  
 Убедитесь, укажите допустимые учетную запись Windows для **@job_login** каждой процедуры. При наличии скриптов репликации из предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]обновите эти скрипты для включения хранимых процедур и параметров, требуемых [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Дополнительные сведения см. в разделе [скрипты обновления репликации & #40; Программирование репликации Transact-SQL & #41;](../../relational-databases/replication/administration/upgrade-replication-scripts-replication-transact-sql-programming.md).  
  
## См. также:  
 [Ошибки и события ссылку & #40; Репликация & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  