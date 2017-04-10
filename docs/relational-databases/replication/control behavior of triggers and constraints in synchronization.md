---
title: "управлять поведением триггеров и ограничений во время синхронизации (программирование репликации на языке Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/29/2017"
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
  - "идентификаторы [репликация SQL Server]"
  - "ограничения [SQL Server], репликация"
  - "триггеры [SQL Server], репликация"
  - "триггеры [репликация SQL Server]"
  - "ограничения [репликация SQL Server]"
  - "NOT FOR REPLICATION, параметр"
  - "NFR, параметр"
ms.assetid: 7c4e0f0e-cadc-4c99-98f4-69799b9b356b
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# управлять поведением триггеров и ограничений во время синхронизации (программирование репликации на языке Transact-SQL)
  Во время синхронизации агенты репликации выполняют [Вставить & #40; Transact-SQL & #41;](../../t-sql/statements/insert-transact-sql.md), [обновления & #40; Transact-SQL & #41;](../../t-sql/queries/update-transact-sql.md), и [Удалить & #40; Transact-SQL & #41;](../../t-sql/statements/delete-transact-sql.md) инструкции в реплицированных таблицах, что может привести к данными триггеры языка DML в этих таблицах для выполнения. В некоторых случаях может понадобиться предотвратить срабатывание этих триггеров или применение ограничений во время синхронизации. Эти действия зависят от того, как были созданы триггер или ограничение.  
  
### Предотвращение срабатывания триггеров во время синхронизации  
  
1.  При создании нового триггера укажите параметр NOT FOR REPLICATION [CREATE TRIGGER & #40; Transact-SQL & #41;](../../t-sql/statements/create-trigger-transact-sql.md).  
  
2.  Для существующего триггера укажите параметр NOT FOR REPLICATION инструкции [ALTER TRIGGER & #40; Transact-SQL & #41;](../../t-sql/statements/alter-trigger-transact-sql.md).  
  
### Предотвращение применения ограничений во время синхронизации  
  
1.  При создании нового ограничения CHECK или FOREIGN KEY, укажите параметр CHECK NOT FOR REPLICATION в определении ограничения [CREATE TABLE & #40; Transact-SQL & #41;](../../t-sql/statements/create-table-transact-sql.md).  
  
## См. также:  
 [Создание таблицы #40; компонент Database Engine & #41;](../../relational-databases/tables/create-tables-database-engine.md)  
  
  