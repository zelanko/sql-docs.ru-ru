---
title: "настроить задание набора транзакции для издателя Oracle (программирование репликации на языке Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
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
  - "sp_publisherproperty"
  - "публикация Oracle [репликация SQL Server], настройка"
ms.assetid: beea1a5c-0053-4971-a68f-0da53063fcbb
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# настроить задание набора транзакции для издателя Oracle (программирование репликации на языке Transact-SQL)
  **Xactset** – это задание базы данных Oracle, создаваемое репликацией, которая выполняется на издателе Oracle и создает наборы транзакций, когда агент чтения журнала не подключен к издателю. Включить и настроить это задание можно программным способом с распространителя с помощью хранимых процедур репликации. Дополнительные сведения см. в разделе [Настройка производительности для издателей Oracle](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md).  
  
### Включение задания наборов транзакций  
  
1.  На издателе Oracle задайте **job_queue_processes** параметра инициализации значение достаточно, чтобы разрешить запуск задания набора транзакций. Дополнительные сведения об этом параметре см. в документации по базе данных для издателя Oracle.  
  
2.  На распространителе выполните хранимую процедуру [sp_publisherproperty & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). В параметре **@publisher**укажите имя издателя Oracle, в параметре **@propertyname** — значение **xactsetbatching**, а в параметре **@propertyvalue** — значение **enabled**.  
  
3.  На распространителе выполните хранимую процедуру [sp_publisherproperty & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Задайте имя издателя Oracle в параметре **@publisher**, значение **xactsetjobinterval** для **@propertyname**и интервал запуска задания в минутах для **@propertyvalue**.  
  
4.  На распространителе выполните хранимую процедуру [sp_publisherproperty & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). В параметре **@publisher**укажите имя издателя Oracle, в параметре **@propertyname** — значение **xactsetjob**, а в параметре **@propertyvalue** — значение **enabled**.  
  
### Настройка задания набора транзакций  
  
1.  (Необязательно) На распространителе выполните хранимую процедуру [sp_publisherproperty & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). В параметре **@publisher**укажите имя издателя Oracle. Система выдаст свойства задания **Xactset** на издателе.  
  
2.  На распространителе выполните хранимую процедуру [sp_publisherproperty & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Задайте имя издателя Oracle в параметре **@publisher**, имя свойства набора транзакций в параметре **@propertyname**и новое значение **@propertyvalue**.  
  
3.  Повторите шаг 2 для каждого устанавливаемого свойства задания набора транзакций (необязательно). Если меняется свойство **xactsetjobinterval** , необходимо перезапустить задание на издателе Oracle, чтобы новый интервал начал действовать.  
  
### Просмотр свойств задания набора транзакций  
  
1.  На распространителе выполните хранимую процедуру [sp_helpxactsetjob](../../../relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql.md). В параметре **@publisher**укажите имя издателя Oracle.  
  
### Отключение задания набора транзакций  
  
1.  На распространителе выполните хранимую процедуру [sp_publisherproperty & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). В параметре **@publisher**укажите имя издателя Oracle, в параметре **@propertyname** — значение **xactsetjob**, а в параметре **@propertyvalue** — значение **disabled**.  
  
## Пример  
 В следующем примере включается задание `Xactset` и устанавливается интервал запуска, равный трем минутам.  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../relational-databases/replication/codesnippet/tsql/configure the transactio_1.sql)]  
  
## См. также:  
 [Настройка производительности для издателей Oracle](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)   
 [Основные понятия системных хранимых процедур репликации](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  