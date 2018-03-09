---
title: "MSSQL_ENG018752 | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSSQL_ENG018752 error
ms.assetid: 405b2655-acb4-4e15-bcc6-b8f86bb22b37
caps.latest.revision: "15"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: da945958bccc9fd0380ab371b43221ca9643fd1b
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="mssqleng018752"></a>MSSQL_ENG018752
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|18752|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|К базе данных одновременно может быть подключен лишь один агент чтения журнала или процедура, относящаяся к журналу (sp_repldone, sp_replcmds и sp_replshowcmds). Если выполняется процедура, относящаяся к журналу, удалите подключение, по которому выполнялась процедура, или выполните для этого подключения процедуру sp_replflush, прежде чем запустить агент чтения журнала или выполнить другую процедуру, относящуюся к журналу.|  
  
## <a name="explanation"></a>Объяснение  
 Попытка выполнить одну из следующих процедур: **sp_repldone**, **sp_replcmds**, или **sp_replshowcmds**в рамках более одного текущего соединения. Хранимые процедуры [sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md) и [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md) используются агентом чтения журнала для обнаружения и обновления сведений о реплицированных транзакциях в опубликованной базе данных. Хранимая процедура [sp_replshowcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql.md) используется для устранения некоторых проблем, возникающих при репликации транзакций.  
  
 Данная ошибка возникает в следующих случаях:  
  
-   Если агент чтения журнала выполняется для опубликованной базы данных, а второй агент чтения журнала пытается получить доступ к той же самой базе данных, возникает ошибка для второго агента, которая записывается в журнал агента.  
  
     Если имеется несколько агентов, возможно, один из них является результатом зависшего процесса.  
  
-   Если запущен агент чтения журнала для опубликованной базы данных и пользователь выполняет процедуру **sp_repldone**, **sp_replcmds**или **sp_replshowcmds** в той же самой базе данных, возникает ошибка в приложении, в котором выполнялась хранимая процедура (например, **sqlcmd**).  
  
-   Если для опубликованной базы данных агент чтения журнала не запущен и пользователь выполняет процедуру **sp_repldone**, **sp_replcmds**или **sp_replshowcmds** , а затем не закрывает соединение, через которое процедура выполнялась, то при попытке агента чтения журнала подключиться к базе данных возникает ошибка.  
  
## <a name="user-action"></a>Действие пользователя  
 Выполнение следующих шагов может помочь устранить проблему. Если на каком-либо шаге можно запустить агент чтения журнала без ошибок, то в выполнении оставшихся шагов нет необходимости.  
  
-   Проверьте журнал агента чтения журнала. Возможно, имеются другие ошибки, вызывающие данную ошибку. Сведения о просмотре в мониторе репликации состояния агента и сведений об ошибках можно найти в статье [Просмотр сведений и выполнение задач для агентов, связанных с публикацией (монитор репликации)](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-publication-agents.md).  
  
-   Проверьте, есть ли в выходных данных процедуры [sp_who &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) идентификаторы процессов (SPIDs), подключенных к опубликованной базе данных. Закройте все соединения, для которых могла выполняться процедура **sp_repldone**, **sp_replcmds**или **sp_replshowcmds**.  
  
-   Перезапустите агент чтения журнала. Дополнительные сведения см. в статье [Запуск и остановка агента репликации (среда SQL Server Management Studio)](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
-   Перезапустите службу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (введите ее в кластер в режиме «вне сети» или «в сети») на распространителе. Если существует возможность, что запланированное задание могло выполнять процедуру **sp_repldone**, **sp_replcmds**или **sp_replshowcmds** из каких-либо других экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , перезапустите также агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для этих экземпляров. Дополнительные сведения см. в статье [Запуск, остановка или приостановка службы агента SQL Server](http://msdn.microsoft.com/library/c95a9759-dd30-4ab6-9ab0-087bb3bfb97c).  
  
-   В издателе в базе данных публикации выполните процедуру [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md), а затем перезапустите агент чтения журнала.  
  
-   Если ошибка продолжает возникать, увеличьте протоколирование агента и укажите выходной файл для журнала. В зависимости от контекста ошибки эта мера может помочь в определении шагов, которые привели к ошибке или появлению дополнительных сообщений об ошибке.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Агент чтения журнала репликации](../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
  
