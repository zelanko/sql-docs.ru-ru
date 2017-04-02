---
title: "заморозить топологию репликации (программирование репликации на языке Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
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
  - "управление репликацией, замораживание"
  - "замораживание [репликация SQL Server]"
  - "репликация транзакций, резервное копирование и восстановление"
ms.assetid: 7626d575-9994-47be-b772-5b6f1b7ef7ca
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# заморозить топологию репликации (программирование репликации на языке Transact-SQL)
  *Замораживание* системы предполагает прекращение операций с опубликованными таблицами на всех узлах и проверку того, что каждый узел получил все изменения со всех других узлов. В этом разделе показано, как заморозить топологию репликации (что необходимо для решения ряда административных задач) и убедиться в том, что узел получил все изменения от других узлов.  
  
### Замораживание топологии репликации транзакций с подписками только для чтения  
  
1.  Приостановите операции со всеми опубликованными таблицами на издателе.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_posttracertoken & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql.md).  
  
3.  На издателе в базе данных публикации выполните хранимую процедуру [sp_helptracertokenhistory](../../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md).  
  
4.  Убедитесь, что каждый подписчик получил трассировочный токен.  
  
### Замораживание топологии репликации транзакций с обновляемыми подписками  
  
1.  Приостановите операции со всеми опубликованными таблицами на издателе и на всех подписчиках.  
  
2.  Если кто-либо из подписчиков использует подписки, обновляемые посредством очередей, выполните следующие действия.  
  
    1.  Если агент чтения очереди не работает постоянно, запустите его. Дополнительные сведения о запуске агентов см. в разделе [Основные понятия исполняемых файлов агента репликации](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) или [Запуск и остановка агента репликации & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
    2.  Чтобы проверить, что очередь пуста, выполните [sp_replqueuemonitor](../../../relational-databases/system-stored-procedures/sp-replqueuemonitor-transact-sql.md) на каждом подписчике.  
  
3.  На издателе в базе данных публикации выполните хранимую процедуру [sp_posttracertoken](../../../relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql.md).  
  
4.  На издателе в базе данных публикации выполните хранимую процедуру [sp_helptracertokenhistory](../../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md).  
  
5.  Убедитесь, что каждый подписчик получил трассировочный токен.  
  
### Замораживание одноранговой топологии репликации транзакций  
  
1.  Приостановите операции со всеми опубликованными таблицами на всех узлах.  
  
2.  Выполнение [sp_requestpeerresponse](../../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) в каждой базе данных публикации в топологии.  
  
3.  Если агент чтения журнала или агент распространителя не выполняется в непрерывном режиме, запустите его. Сначала необходимо запустить агент чтения журнала, а затем агент распространителя. Дополнительные сведения о запуске агентов см. в разделе [Основные понятия исполняемых файлов агента репликации](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) или [Запуск и остановка агента репликации & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
4.  Выполнение [sp_helppeerresponses](../../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md) в каждой базе данных публикации в топологии. Убедитесь, что в результирующем наборе содержатся ответы от всех других узлов.  
  
### Проверка того, что одноранговый узел получил все предыдущие изменения  
  
1.  Выполнение [sp_requestpeerresponse](../../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) в базе данных публикации на узле, который вы проверяете.  
  
2.  Если агент чтения журнала или агент распространителя не выполняется в непрерывном режиме, запустите его. Сначала необходимо запустить агент чтения журнала, а затем агент распространителя. Дополнительные сведения о запуске агентов см. в разделе [Основные понятия исполняемых файлов агента репликации](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) или [Запуск и остановка агента репликации & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
3.  Выполнение [sp_helppeerresponses](../../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md) в базе данных публикации на узле, который вы проверяете. Убедитесь, что в результирующем наборе содержатся ответы от всех других узлов.  
  
### Замораживание топологии репликации слиянием  
  
1.  Приостановите операции со всеми опубликованными таблицами на издателе и на всех подписчиках.  
  
2.  Выполните агент слияния для каждой подписки дважды: сначала для синхронизации всех подписок, а затем для повторной синхронизации каждой подписки. Таким образом будет гарантирована репликация изменений на все узлы. Дополнительные сведения о запуске агентов см. в разделе [Основные понятия исполняемых файлов агента репликации](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) или [Запуск и остановка агента репликации & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
    > [!NOTE]  
    >  Если во время синхронизации обнаружен конфликт, то изменения, необходимые для разрешения конфликта, могут не распространиться на все узлы после того, как агент слияния будет запущен дважды.  
  
## См. также:  
 [Администрирование топологии Peer-to-Peer & #40; Программирование репликации Transact-SQL и #41;](../../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Измерение задержки и проверка правильности соединений для репликации транзакций](../../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  