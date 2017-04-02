---
title: "администрировать одноранговую топологию (программирование репликации на языке Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
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
  - "репликация транзакций, одноранговая репликация"
ms.assetid: 4d0fa941-f9ea-4a14-aed9-34df593fc6f2
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# администрировать одноранговую топологию (программирование репликации на языке Transact-SQL)
  Администрирование одноранговой топологии напоминает администрирование обычное топологии репликации транзакций, оно имеет некоторые специфические особенности. Главное отличие в администрировании топологии peer-to-peer является то, что некоторые изменения требуется системе *заморожена*. Замораживание системы предполагает прекращение операций с опубликованными таблицами на всех узлах и проверку того, что каждый узел получил все изменения со всех других узлов. Дополнительные сведения см. в разделе [замораживание топологии репликации & #40; Программирование репликации Transact-SQL & #41;](../../../relational-databases/replication/administration/quiesce-a-replication-topology-replication-transact-sql-programming.md).  
  
> [!NOTE]  
>  В одноранговой топологии распространитель не может использовать более раннюю версию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], чем подписчик по запросу.  
  
### Добавление статьи к существующей конфигурации  
  
1.  Заморозьте систему.  
  
2.  Остановите агент распространителя в каждом узле топологии. Дополнительные сведения см. в разделе [Основные понятия исполняемых файлов агента репликации](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) или [Запуск и остановка агента репликации & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
3.  При помощи инструкции CREATE TABLE добавьте новую таблицу в каждом из узлов топологии.  
  
4.  Вручную выполните массовое копирование данных во всех узлах при помощи [программы bcp](../../../tools/bcp-utility.md).  
  
5.  Выполнение [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) для создания новой статьи на каждом узле в топологии. Дополнительные сведения см. в статье [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
    > [!NOTE]  
    >  После [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) будет выполнена репликация автоматически добавляет статьи подписки в топологии.  
  
6.  Перезапустите агент распространителя в каждом из узлов топологии.  
  
### Внесение изменений в схему баз данных публикации  
  
1.  Заморозьте систему.  
  
2.  При помощи инструкций языка DDL внесите изменения в схему опубликованных таблиц. Дополнительные сведения о поддерживаемых изменениях схем см. в разделе [внесение изменений схемы в базах данных публикаций](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
3.  Прежде чем возобновить работу с опубликованными таблицами, вновь заморозьте систему. Это необходимо для того, чтобы изменения в схеме были приняты всеми узлами до репликации новых изменений данных.  
  
## Пример  
 Следующий пример показывает, как нужно добавлять новую статью таблицы к существующей одноранговой топологии репликации с двумя узлами.  
  
 [!code-sql[HowTo#sp_addp2particle_createtables](../../../relational-databases/replication/codesnippet/tsql/administer-a-peer-to-pee_1.sql)]  
  
 [!code-sql[HowTo#sp_addp2particle_cmdline](../../../relational-databases/replication/codesnippet/tsql/administer-a-peer-to-pee_2.sql)]  
  
 [!code-sql[HowTo#sp_addp2particle_createarticle](../../../relational-databases/replication/codesnippet/tsql/administer-a-peer-to-pee_3.sql)]  
  
## См. также:  
 [Администрирование и #40; Репликация & #41;](../../../relational-databases/replication/administration/administration-replication.md)   
 [Резервное копирование и восстановление баз данных SQL Server](../../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Одноранговая репликация транзакций](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  