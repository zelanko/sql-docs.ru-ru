---
title: "Администрирование одноранговой топологии (программирование репликации на языке Transact-SQL) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- transactional replication, peer-to-peer replication
ms.assetid: 4d0fa941-f9ea-4a14-aed9-34df593fc6f2
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 97d6ba982d1f3d4fb1eef62e30cd714455f82c67
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="administer-a-peer-to-peer-topology-replication-transact-sql-programming"></a>Администрирование одноранговой топологии (программирование репликации на языке Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Администрирование одноранговой топологии напоминает администрирование обычное топологии репликации транзакций, оно имеет некоторые специфические особенности. Главное отличие состоит в том, что при администрировании одноранговой топологии некоторые изменения требуют *замораживания*системы. Замораживание системы предполагает прекращение операций с опубликованными таблицами на всех узлах и проверку того, что каждый узел получил все изменения со всех других узлов. Дополнительные сведения см. в разделе [Замораживание топологии репликации (программирование репликации на языке Transact-SQL)](../../../relational-databases/replication/administration/quiesce-a-replication-topology-replication-transact-sql-programming.md).  
  
> [!NOTE]  
>  В одноранговой топологии распространитель не может использовать более раннюю версию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], чем подписчик по запросу.  
  
### <a name="to-add-an-article-to-an-existing-configuration"></a>Добавление статьи к существующей конфигурации  
  
1.  Заморозьте систему.  
  
2.  Остановите агент распространителя в каждом узле топологии. Дополнительные сведения см. в разделах [Основные понятия исполняемых файлов агента репликации](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) и [Запуск и остановка агента репликации (среда SQL Server Management Studio)](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
3.  При помощи инструкции CREATE TABLE добавьте новую таблицу в каждом из узлов топологии.  
  
4.  Вручную выполните массовое копирование данных во всех узлах при помощи [программы bcp](../../../tools/bcp-utility.md).  
  
5.  С помощью хранимой процедуры [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) создайте новую статью в каждом узле топологии. Дополнительные сведения см. в статье [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
    > [!NOTE]  
    >  После завершения хранимой процедуры [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) репликация автоматически добавит статью в подписки топологии.  
  
6.  Перезапустите агент распространителя в каждом из узлов топологии.  
  
### <a name="to-make-schema-changes-to-a-publication-database"></a>Внесение изменений в схему баз данных публикации  
  
1.  Заморозьте систему.  
  
2.  При помощи инструкций языка DDL внесите изменения в схему опубликованных таблиц. Дополнительные сведения о поддерживаемых изменениях схем см. в разделе [Внесение изменений в схемы баз данных публикации](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
3.  Прежде чем возобновить работу с опубликованными таблицами, вновь заморозьте систему. Это необходимо для того, чтобы изменения в схеме были приняты всеми узлами до репликации новых изменений данных.  
  
## <a name="example"></a>Пример  
 Следующий пример показывает, как нужно добавлять новую статью таблицы к существующей одноранговой топологии репликации с двумя узлами.  
  
 [!code-sql[HowTo#sp_addp2particle_createtables](../../../relational-databases/replication/codesnippet/tsql/administer-a-peer-to-pee_1.sql)]  
  
 [!code-sql[HowTo#sp_addp2particle_cmdline](../../../relational-databases/replication/codesnippet/tsql/administer-a-peer-to-pee_2.sql)]  
  
 [!code-sql[HowTo#sp_addp2particle_createarticle](../../../relational-databases/replication/codesnippet/tsql/administer-a-peer-to-pee_3.sql)]  
  
## <a name="see-also"></a>См. также:  
 [Администрирование (репликация)](../../../relational-databases/replication/administration/administration-replication.md)   
 [Резервное копирование и восстановление баз данных SQL Server](../../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Одноранговая репликация транзакций](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  
