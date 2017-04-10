---
title: "Подписка, нераспространенные команды (подписка на публикацию транзакций, SQL Server 2005 и более поздние версии) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.monitor.subscription.performance.f1"
ms.assetid: 5451561e-0ce3-4bb5-844a-88cd15b0b371
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Подписка, нераспространенные команды (подписка на публикацию транзакций, SQL Server 2005 и более поздние версии)
  На вкладке **Нераспространенные команды** отображаются сведения о количестве команд в базе данных распространителя, которые не были доставлены выбранному подписчику, и приблизительное время для доставки этих команд. Сведения о просмотре этих команд в базе данных распространителя см. в разделе [sp_replshowcmds & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql.md).  
  
## Параметры  
 **Число команд в базе данных распространителя, которые ожидают применения к этому подписчику.**  
 Количество команд в базе данных распространителя, которые не были доставлены выбранному подписчику. Команда состоит из одной инструкции языка обработки данных (DML) или одной инструкции языка определения данных (DDL) языка Transact-SQL.  
  
 **Расчетное время применения этих команд, вычисленное по результатам предыдущего выполнения.**  
 Примерное количество времени, необходимое для доставки команд на подписчик. Если это значение превышает количество времени, требуемое для создания и применения моментального снимка на подписчике, рассмотрите возможность повторной инициализации подписчика. Дополнительные сведения см. в разделе [повторно инициализировать подписки](../../relational-databases/replication/reinitialize-subscriptions.md).  
  
## См. также:  
 [Запуск монитора репликации](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Наблюдение за производительностью с помощью монитора репликации](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)   
 [Наблюдение за репликацией](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  