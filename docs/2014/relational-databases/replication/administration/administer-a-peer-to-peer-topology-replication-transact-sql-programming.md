---
title: Администрирование одноранговой топологии (программирование репликации на языке Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- transactional replication, peer-to-peer replication
ms.assetid: 4d0fa941-f9ea-4a14-aed9-34df593fc6f2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0254902ce6e2b67b29cbdf2d9a4544036a0d747b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52773386"
---
# <a name="administer-a-peer-to-peer-topology-replication-transact-sql-programming"></a>Администрирование одноранговой топологии (программирование репликации на языке Transact-SQL)
  Администрирование одноранговой топологии напоминает администрирование обычное топологии репликации транзакций, оно имеет некоторые специфические особенности. Главное отличие состоит в том, что при администрировании одноранговой топологии некоторые изменения требуют *замораживания*системы. Замораживание системы предполагает прекращение операций с опубликованными таблицами на всех узлах и проверку того, что каждый узел получил все изменения со всех других узлов. Дополнительные сведения см. в разделе [Замораживание топологии репликации (программирование репликации на языке Transact-SQL)](quiesce-a-replication-topology-replication-transact-sql-programming.md).  
  
> [!NOTE]  
>  В одноранговой топологии распространитель не может использовать более раннюю версию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], чем подписчик по запросу.  
  
### <a name="to-add-an-article-to-an-existing-configuration"></a>Добавление статьи к существующей конфигурации  
  
1.  Заморозьте систему.  
  
2.  Остановите агент распространителя в каждом узле топологии. Дополнительные сведения см. в разделах [Основные понятия исполняемых файлов агента репликации](../concepts/replication-agent-executables-concepts.md) и [Запуск и остановка агента репликации (среда SQL Server Management Studio)](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
3.  При помощи инструкции CREATE TABLE добавьте новую таблицу в каждом из узлов топологии.  
  
4.  Вручную выполните массовое копирование данных во всех узлах при помощи [программы bcp](../../../tools/bcp-utility.md).  
  
5.  С помощью хранимой процедуры [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) создайте новую статью в каждом узле топологии. Дополнительные сведения см. в статье [определить статью](../publish/define-an-article.md).  
  
    > [!NOTE]  
    >  После завершения хранимой процедуры [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) репликация автоматически добавит статью в подписки топологии.  
  
6.  Перезапустите агент распространителя в каждом из узлов топологии.  
  
### <a name="to-make-schema-changes-to-a-publication-database"></a>Внесение изменений в схему баз данных публикации  
  
1.  Заморозьте систему.  
  
2.  При помощи инструкций языка DDL внесите изменения в схему опубликованных таблиц. Дополнительные сведения о поддерживаемых изменениях схем см. в разделе [Внесение изменений в схемы баз данных публикации](../publish/make-schema-changes-on-publication-databases.md).  
  
3.  Прежде чем возобновить работу с опубликованными таблицами, вновь заморозьте систему. Это необходимо для того, чтобы изменения в схеме были приняты всеми узлами до репликации новых изменений данных.  
  
## <a name="example"></a>Пример  
 Следующий пример показывает, как нужно добавлять новую статью таблицы к существующей одноранговой топологии репликации с двумя узлами.  
  
 [!code-sql[HowTo#sp_addp2particle_createtables](../../../snippets/tsql/SQL15/replication/howto/tsql/addp2particle.sql#sp_addp2particle_createtables)]  
  
 [!code-sql[HowTo#sp_addp2particle_cmdline](../../../snippets/tsql/SQL15/replication/howto/tsql/addp2particle.sql#sp_addp2particle_cmdline)]  
  
 [!code-sql[HowTo#sp_addp2particle_createarticle](../../../snippets/tsql/SQL15/replication/howto/tsql/addp2particle.sql#sp_addp2particle_createarticle)]  
  
## <a name="see-also"></a>См. также  
 [Администрирование (репликация)](administration-replication.md)   
 [Резервное копирование и восстановление баз данных SQL Server](../../backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Одноранговая репликация транзакций](../transactional/peer-to-peer-transactional-replication.md)  
  
  
