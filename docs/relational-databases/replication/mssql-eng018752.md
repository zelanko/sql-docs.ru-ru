---
title: "MSSQL_ENG018752 | Microsoft Docs"
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
  - "MSSQL_ENG018752, ошибка"
ms.assetid: 405b2655-acb4-4e15-bcc6-b8f86bb22b37
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MSSQL_ENG018752
    
## Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|18752|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|К базе данных одновременно может быть подключен лишь один агент чтения журнала или процедура, относящаяся к журналу (sp_repldone, sp_replcmds и sp_replshowcmds). Если выполняется процедура, относящаяся к журналу, удалите подключение, по которому выполнялась процедура, или выполните для этого подключения процедуру sp_replflush, прежде чем запустить агент чтения журнала или выполнить другую процедуру, относящуюся к журналу.|  
  
## Объяснение  
 Более одного текущего соединения пытаются выполнить одно из следующих: **sp_repldone**, **sp_replcmds**, или **sp_replshowcmds**. Хранимые процедуры [sp_repldone & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md) и [sp_replcmds & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md) хранимые процедуры используются агентом чтения журнала для обнаружения и обновления сведений о реплицированных транзакциях в опубликованной базе данных. Хранимая процедура [sp_replshowcmds & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql.md) используется для устранения некоторых типов проблем с репликацией транзакций.  
  
 Данная ошибка возникает в следующих случаях:  
  
-   Если агент чтения журнала выполняется для опубликованной базы данных, а второй агент чтения журнала пытается получить доступ к той же самой базе данных, возникает ошибка для второго агента, которая записывается в журнал агента.  
  
     Если имеется несколько агентов, возможно, один из них является результатом зависшего процесса.  
  
-   Если запущен агент чтения журнала для опубликованной базы данных и пользователь выполняет **sp_repldone**, **sp_replcmds**, или **sp_replshowcmds** к той же базе данных, возникает ошибка в приложении, в котором выполнялась хранимая процедура (например, **sqlcmd**).  
  
-   Если агент чтения журнала не выполняется для опубликованной базы данных и пользователь выполняет **sp_repldone**, **sp_replcmds**, или **sp_replshowcmds** и затем не закрывает соединение, через которое процедура выполнялась, ошибка возникает, когда агент чтения журнала пытается подключиться к базе данных.  
  
## Действие пользователя  
 Выполнение следующих шагов может помочь устранить проблему. Если на каком-либо шаге можно запустить агент чтения журнала без ошибок, то в выполнении оставшихся шагов нет необходимости.  
  
-   Проверьте журнал агента чтения журнала. Возможно, имеются другие ошибки, вызывающие данную ошибку. Сведения о просмотре в мониторе репликации состояния агента и ошибок сведения см. в разделе [Просмотр сведений и выполнение задач для агентов снимков & #40; Монитор репликации & #41;](../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md).  
  
-   Проверьте выходные данные [sp_who & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) идентификационные номера определенного процесса (SPID), которые подключены к опубликованной базе данных. Закройте все подключения, которые может быть вызвано **sp_repldone**, **sp_replcmds**, или **sp_replshowcmds**.  
  
-   Перезапустите агент чтения журнала. Дополнительные сведения см. в разделе [Запуск и остановка агента репликации & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
-   Перезапустите службу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (введите ее в кластер в режиме «вне сети» или «в сети») на распространителе. Если есть вероятность, что запланированное задание могло выполнять **sp_repldone**, **sp_replcmds**, или **sp_replshowcmds** от любого другого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра, перезапустите [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агент для этих экземпляров. Дополнительные сведения см. в разделе [Запуск, остановка или приостановка службы агента SQL Server](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md).  
  
-   Выполнение [sp_replflush & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md) на издателе в базе данных публикации, а затем перезапустите агент чтения журнала.  
  
-   Если ошибка продолжает возникать, увеличьте протоколирование агента и укажите выходной файл для журнала. В зависимости от контекста ошибки эта мера может помочь в определении шагов, которые привели к ошибке или появлению дополнительных сообщений об ошибке.  
  
## См. также:  
 [Ошибки и события ссылку & #40; Репликация & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Агент чтения журнала репликации](../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
  