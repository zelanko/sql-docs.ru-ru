---
title: Настройка задания для набора транзакции в издателе Oracle | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- sp_publisherproperty
- Oracle publishing [SQL Server replication], configuring
ms.assetid: beea1a5c-0053-4971-a68f-0da53063fcbb
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1a412288ca94808ee71d07d8038271adffcc4ac2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="configure-the-transaction-set-job-for-an-oracle-publisher"></a>Настройка задания для набора транзакции в издателе Oracle
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **Xactset** – это задание базы данных Oracle, создаваемое репликацией, которая выполняется на издателе Oracle и создает наборы транзакций, когда агент чтения журнала не подключен к издателю. Включить и настроить это задание можно программным способом с распространителя с помощью хранимых процедур репликации. Дополнительные сведения см. в статье [Настройка производительности для издателей Oracle](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md).  
  
### <a name="to-enable-the-transaction-set-job"></a>Включение задания наборов транзакций  
  
1.  На издателе Oracle задайте достаточно большое значение параметра инициализации **job_queue_processes** , чтобы могло выполняться задание «Xactset». Дополнительные сведения об этом параметре см. в документации по базе данных для издателя Oracle.  
  
2.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). В параметре **@publisher**укажите имя издателя Oracle, в параметре **@propertyname** @propertyname **@propertyname**, а в параметре **@propertyvalue** @propertyname **@propertyvalue**.  
  
3.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). В параметре **@publisher**укажите имя издателя Oracle, в параметре **xactsetjobinterval** @propertyname **@propertyname**и интервал запуска задания в минутах для **@propertyvalue**.  
  
4.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). В параметре **@publisher**укажите имя издателя Oracle, в параметре **@propertyname** @propertyname **@propertyname**, а в параметре **@propertyvalue** @propertyname **@propertyvalue**.  
  
### <a name="to-configure-the-transaction-set-job"></a>Настройка задания набора транзакций  
  
1.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md) (необязательно). В параметре **@publisher**. Система выдаст свойства задания **Xactset** на издателе.  
  
2.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). В параметре **@publisher**, имя свойства набора транзакций в параметре **@propertyname**и новое значение **@propertyvalue**.  
  
3.  Повторите шаг 2 для каждого устанавливаемого свойства задания набора транзакций (необязательно). Если меняется свойство **xactsetjobinterval** , необходимо перезапустить задание на издателе Oracle, чтобы новый интервал начал действовать.  
  
### <a name="to-view-properties-of-the-transaction-set-job"></a>Просмотр свойств задания набора транзакций  
  
1.  На распространителе выполните процедуру [sp_helpxactsetjob](../../../relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql.md). В параметре **@publisher**.  
  
### <a name="to-disable-the-transaction-set-job"></a>Отключение задания набора транзакций  
  
1.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). В параметре **@publisher**укажите имя издателя Oracle, в параметре **@propertyname** @propertyname **@propertyname**, а в параметре **@propertyvalue** @propertyname **@propertyvalue**.  
  
## <a name="example"></a>Пример  
 В следующем примере включается задание `Xactset` и устанавливается интервал запуска, равный трем минутам.  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../relational-databases/replication/codesnippet/tsql/configure-the-transactio_1.sql)]  
  
## <a name="see-also"></a>См. также:  
 [Настройка производительности для издателей Oracle](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)   
 [Replication System Stored Procedures Concepts](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  
