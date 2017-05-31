---
title: "Заморозка топологии репликации (программирование репликации на языке Transact-SQL) | Документация Майкрософт"
ms.custom: 
ms.date: 03/03/2017
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
- administering replication, quiescing
- quiesce [SQL Server replication]
- transactional replication, backup and restore
ms.assetid: 7626d575-9994-47be-b772-5b6f1b7ef7ca
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 316668cc6facd8c2ec3692f309d2fec69342ceb2
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="quiesce-a-replication-topology-replication-transact-sql-programming"></a>заморозить топологию репликации (программирование репликации на языке Transact-SQL)
  *Замораживание* системы предполагает прекращение операций с опубликованными таблицами на всех узлах и проверку того, что каждый узел получил все изменения со всех других узлов. В этом разделе показано, как заморозить топологию репликации (что необходимо для решения ряда административных задач) и убедиться в том, что узел получил все изменения от других узлов.  
  
### <a name="to-quiesce-a-transactional-replication-topology-with-read-only-subscriptions"></a>Замораживание топологии репликации транзакций с подписками только для чтения  
  
1.  Приостановите операции со всеми опубликованными таблицами на издателе.  
  
2.  В издателе в базе данных публикации выполните процедуру [sp_posttracertoken &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql.md).  
  
3.  В базе данных публикации на издателе выполните процедуру [sp_helptracertokenhistory](../../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md).  
  
4.  Убедитесь, что каждый подписчик получил трассировочный токен.  
  
### <a name="to-quiesce-a-transactional-replication-topology-with-updatable-subscriptions"></a>Замораживание топологии репликации транзакций с обновляемыми подписками  
  
1.  Приостановите операции со всеми опубликованными таблицами на издателе и на всех подписчиках.  
  
2.  Если кто-либо из подписчиков использует подписки, обновляемые посредством очередей, выполните следующие действия.  
  
    1.  Если агент чтения очереди не работает постоянно, запустите его. Дополнительные сведения о выполнении агентов см. в статьях [Основные понятия исполняемых файлов агента репликации](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) и [Запуск и остановка агента репликации (среда SQL Server Management Studio)](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
    2.  Чтобы убедиться в том, что очередь пуста, выполните процедуру [sp_replqueuemonitor](../../../relational-databases/system-stored-procedures/sp-replqueuemonitor-transact-sql.md) на каждом подписчике.  
  
3.  В базе данных публикации на издателе выполните процедуру [sp_posttracertoken](../../../relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql.md).  
  
4.  В базе данных публикации на издателе выполните процедуру [sp_helptracertokenhistory](../../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md).  
  
5.  Убедитесь, что каждый подписчик получил трассировочный токен.  
  
### <a name="to-quiesce-a-peer-to-peer-transactional-replication-topology"></a>Замораживание одноранговой топологии репликации транзакций  
  
1.  Приостановите операции со всеми опубликованными таблицами на всех узлах.  
  
2.  Выполните процедуру [sp_requestpeerresponse](../../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) в каждой базе данных публикации в топологии.  
  
3.  Если агент чтения журнала или агент распространителя не выполняется в непрерывном режиме, запустите его. Сначала необходимо запустить агент чтения журнала, а затем агент распространителя. Дополнительные сведения о выполнении агентов см. в статьях [Основные понятия исполняемых файлов агента репликации](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) и [Запуск и остановка агента репликации (среда SQL Server Management Studio)](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
4.  Выполните процедуру [sp_helppeerresponses](../../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md) в каждой базе данных публикации в топологии. Убедитесь, что в результирующем наборе содержатся ответы от всех других узлов.  
  
### <a name="to-ensure-a-peer-to-peer-node-has-received-all-prior-changes"></a>Проверка того, что одноранговый узел получил все предыдущие изменения  
  
1.  Выполните процедуру [sp_requestpeerresponse](../../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) в каждой базе данных публикации на проверяемом узле.  
  
2.  Если агент чтения журнала или агент распространителя не выполняется в непрерывном режиме, запустите его. Сначала необходимо запустить агент чтения журнала, а затем агент распространителя. Дополнительные сведения о выполнении агентов см. в статьях [Основные понятия исполняемых файлов агента репликации](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) и [Запуск и остановка агента репликации (среда SQL Server Management Studio)](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
3.  Выполните процедуру [sp_helppeerresponses](../../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md) в каждой базе данных публикации на проверяемом узле. Убедитесь, что в результирующем наборе содержатся ответы от всех других узлов.  
  
### <a name="to-quiesce-a-merge-replication-topology"></a>Замораживание топологии репликации слиянием  
  
1.  Приостановите операции со всеми опубликованными таблицами на издателе и на всех подписчиках.  
  
2.  Выполните агент слияния для каждой подписки дважды: сначала для синхронизации всех подписок, а затем для повторной синхронизации каждой подписки. Таким образом будет гарантирована репликация изменений на все узлы. Дополнительные сведения о выполнении агентов см. в статьях [Основные понятия исполняемых файлов агента репликации](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) и [Запуск и остановка агента репликации (среда SQL Server Management Studio)](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
    > [!NOTE]  
    >  Если во время синхронизации обнаружен конфликт, то изменения, необходимые для разрешения конфликта, могут не распространиться на все узлы после того, как агент слияния будет запущен дважды.  
  
## <a name="see-also"></a>См. также:  
 [Администрирование одноранговой топологии (программирование репликации на языке Transact-SQL)](../../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Измерение задержки и проверка правильности соединений для репликации транзакций](../../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
