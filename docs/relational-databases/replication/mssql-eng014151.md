---
title: "MSSQL_ENG014151 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG014151, ошибка"
ms.assetid: 54b45e70-46b3-4c7a-a5bf-06f6dd028ceb
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# MSSQL_ENG014151
    
## Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|14151|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Репликация-%s: ошибка агента %s. %s|  
  
## Объяснение  
 Эта ошибка возникает в случае сбоя любого агента репликации. Текст в конце сообщения зависит от контекста сбоя.  
  
## Действие пользователя  
 Эта ошибка может возникать в нескольких ситуациях; в зависимости от сложившихся обстоятельств используйте следующие подходы:  
  
-   Перезапустите агент, сбой которого произошел, и посмотрите, будет ли он теперь работать без сбоев. Дополнительные сведения см. в разделе [Запуск и остановка агента репликации & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) и [Основные понятия исполняемых файлов агента репликации](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
-   Проверьте журнал агента и журнал заданий на наличие других ошибок, возникших приблизительно в то же время. Сведения о просмотре состояния агента и подробных сведений об ошибке в мониторе репликации см. в следующих разделах:  
  
    -   Агент моментальных снимков, агента чтения журнала и агента чтения очереди см. в разделе [Просмотр сведений и выполнение задач для агентов снимков & #40; Монитор репликации & #41;](../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md).  
  
    -   Агент распространителя и агент слияния см. в разделе [Просмотр сведений и выполнение задач для агентов, связанных с подпиской и #40; Монитор репликации & #41;](../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
-   Проверьте функционирование базовых соединений между компьютерами, к которым обращается агент, а затем подключитесь к каждому из этих компьютеров, используя программу, такую как [sqlcmd Utility](../../tools/sqlcmd-utility.md). При подключении используйте ту же учетную запись, под которой агент устанавливает соединения. Дополнительные сведения о правах доступа, необходимых учетной записи каждого агента, см. в разделе [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
-   Если ошибка возникает при создании или применении моментального снимка, проверьте файлы в каталоге моментальных снимков на наличие ошибок.  
  
-   Если ошибка продолжает возникать, увеличьте протоколирование агента и укажите выходной файл для журнала. В зависимости от контекста ошибки эта мера может помочь в определении шагов, которые привели к ошибке или появлению дополнительных сообщений об ошибке.  
  
## См. также:  
 [Администрирование агента репликации](../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Ошибки и события ссылку & #40; Репликация & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Агент распространения репликации](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Агент чтения журнала репликации](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Агент слияния репликации](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Агент чтения очереди репликации](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Агент моментальных снимков репликации](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  