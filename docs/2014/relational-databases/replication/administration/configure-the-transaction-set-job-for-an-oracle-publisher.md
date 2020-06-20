---
title: Настройка задания набора транзакций для издателя Oracle (программирование репликации на языке Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_publisherproperty
- Oracle publishing [SQL Server replication], configuring
ms.assetid: beea1a5c-0053-4971-a68f-0da53063fcbb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 43a25ce755a505f0efd7c25243b8969a962ea701
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065977"
---
# <a name="configure-the-transaction-set-job-for-an-oracle-publisher-replication-transact-sql-programming"></a>настроить задание набора транзакции для издателя Oracle (программирование репликации на языке Transact-SQL)
  **Xactset** – это задание базы данных Oracle, создаваемое репликацией, которая выполняется на издателе Oracle и создает наборы транзакций, когда агент чтения журнала не подключен к издателю. Включить и настроить это задание можно программным способом с распространителя с помощью хранимых процедур репликации. Дополнительные сведения см. в статье [Настройка производительности для издателей Oracle](../non-sql/performance-tuning-for-oracle-publishers.md).  
  
### <a name="to-enable-the-transaction-set-job"></a>Включение задания наборов транзакций  
  
1.  На издателе Oracle задайте достаточно большое значение параметра инициализации **job_queue_processes** , чтобы могло выполняться задание «Xactset». Дополнительные сведения об этом параметре см. в документации по базе данных для издателя Oracle.  
  
2.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Укажите имя издателя Oracle для ** \@ издателя**, значение `xactsetbatching` для ** \@ PropertyName**и значение `enabled` для параметра ** \@ propertyvalue**.  
  
3.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Укажите имя издателя Oracle для ** \@ издателя**, значение `xactsetjobinterval` для ** \@ PropertyName**и интервал задания в минутах для ** \@ propertyvalue**.  
  
4.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Укажите имя издателя Oracle для ** \@ издателя**, значение `xactsetjob` для ** \@ PropertyName**и значение `enabled` для параметра ** \@ propertyvalue**.  
  
### <a name="to-configure-the-transaction-set-job"></a>Настройка задания набора транзакций  
  
1.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) (необязательно). Укажите имя издателя Oracle для ** \@ издателя**. Система выдаст свойства задания **Xactset** на издателе.  
  
2.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Укажите имя издателя Oracle для ** \@ издателя**, имя свойства задания набора транзакций, устанавливаемое для ** \@ PropertyName**, и новый параметр для ** \@ propertyvalue**.  
  
3.  Повторите шаг 2 для каждого устанавливаемого свойства задания набора транзакций (необязательно). При изменении `xactsetjobinterval` свойства необходимо перезапустить задание на издателе Oracle, чтобы новый интервал вступил в силу.  
  
### <a name="to-view-properties-of-the-transaction-set-job"></a>Просмотр свойств задания набора транзакций  
  
1.  На распространителе выполните процедуру [sp_helpxactsetjob](/sql/relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql). Укажите имя издателя Oracle для ** \@ издателя**.  
  
### <a name="to-disable-the-transaction-set-job"></a>Отключение задания набора транзакций  
  
1.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Укажите имя издателя Oracle для ** \@ издателя**, значение `xactsetjob` для ** \@ PropertyName**и значение `disabled` для параметра ** \@ propertyvalue**.  
  
## <a name="example"></a>Пример  
 В следующем примере включается задание `Xactset` и устанавливается интервал запуска, равный трем минутам.  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../snippets/tsql/SQL15/replication/howto/tsql/enablexactsetjob.sql#sp_enable_xactsetjob)]  
  
## <a name="see-also"></a>См. также:  
 [Настройка производительности для издателей Oracle](../non-sql/performance-tuning-for-oracle-publishers.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
