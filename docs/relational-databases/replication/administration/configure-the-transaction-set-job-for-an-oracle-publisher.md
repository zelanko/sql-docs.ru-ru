---
title: Установка задания настройки транзакции (издатель Oracle)
description: Узнайте, как настроить задание настройки транзакций для публикации издателя Oracle на подписчике SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
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
ms.openlocfilehash: 8f25f3d9c9a69d3a8f87e8a4eb1886f31092940f
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "75322061"
---
# <a name="configure-the-transaction-set-job-for-an-oracle-publisher"></a>Настройка задания для набора транзакции в издателе Oracle
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **Xactset** – это задание базы данных Oracle, создаваемое репликацией, которая выполняется на издателе Oracle и создает наборы транзакций, когда агент чтения журнала не подключен к издателю. Включить и настроить это задание можно программным способом с распространителя с помощью хранимых процедур репликации. Дополнительные сведения см. в статье [Настройка производительности для издателей Oracle](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md).  
  
### <a name="to-enable-the-transaction-set-job"></a>Включение задания наборов транзакций  
  
1.  На издателе Oracle задайте достаточно большое значение параметра инициализации **job_queue_processes** , чтобы могло выполняться задание «Xactset». Дополнительные сведения об этом параметре см. в документации по базе данных для издателя Oracle.  
  
2.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). В параметре **\@publisher** укажите имя издателя Oracle, в параметре **\@propertyname** — значение **xactsetbatching**, а в параметре **\@propertyvalue** — значение **enabled**.  
  
3.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Задайте имя издателя Oracle в параметре **\@publisher**, значение **xactsetjobinterval** для **\@propertyname** и интервал запуска задания в минутах для **\@propertyvalue**.  
  
4.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). В параметре **\@publisher** укажите имя издателя Oracle, в параметре **\@propertyname** — значение **xactsetjob**, а в параметре **\@propertyvalue** — значение **enabled**.  
  
### <a name="to-configure-the-transaction-set-job"></a>Настройка задания набора транзакций  
  
1.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md) (необязательно). В параметре **\@publisher** укажите имя издателя Oracle. Система выдаст свойства задания **Xactset** на издателе.  
  
2.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Задайте имя издателя Oracle в параметре **\@publisher**, имя свойства задания Xactset в параметре **\@propertyname** и новое значение в **\@propertyvalue**.  
  
3.  Повторите шаг 2 для каждого устанавливаемого свойства задания набора транзакций (необязательно). Если меняется свойство **xactsetjobinterval** , необходимо перезапустить задание на издателе Oracle, чтобы новый интервал начал действовать.  
  
### <a name="to-view-properties-of-the-transaction-set-job"></a>Просмотр свойств задания набора транзакций  
  
1.  На распространителе выполните процедуру [sp_helpxactsetjob](../../../relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql.md). В параметре **\@publisher** укажите имя издателя Oracle.  
  
### <a name="to-disable-the-transaction-set-job"></a>Отключение задания набора транзакций  
  
1.  На распространителе выполните хранимую процедуру [sp_publisherproperty (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). В параметре **\@publisher** укажите имя издателя Oracle, в параметре **\@propertyname** — значение **xactsetjob**, а в параметре **\@propertyvalue** — значение **disabled**.  
  
## <a name="example"></a>Пример  
 В следующем примере включается задание `Xactset` и устанавливается интервал запуска, равный трем минутам.  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../relational-databases/replication/codesnippet/tsql/configure-the-transactio_1.sql)]  
  
## <a name="see-also"></a>См. также:  
 [Настройка производительности для издателей Oracle](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)   
 [Replication System Stored Procedures Concepts](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  
