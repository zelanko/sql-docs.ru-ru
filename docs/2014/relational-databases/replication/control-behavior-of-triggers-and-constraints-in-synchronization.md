---
title: Управлять поведением триггеров и ограничений во время синхронизации (Программирование репликации Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- identities [SQL Server replication]
- constraints [SQL Server], replication
- triggers [SQL Server], replication
- triggers [SQL Server replication]
- constraints [SQL Server replication]
- NOT FOR REPLICATION option
- NFR option
ms.assetid: 7c4e0f0e-cadc-4c99-98f4-69799b9b356b
caps.latest.revision: 35
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: e287beff3addbea618e825ef3b0664d9d005e7ed
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099541"
---
# <a name="control-the-behavior-of-triggers-and-constraints-during-synchronization-replication-transact-sql-programming"></a>управлять поведением триггеров и ограничений во время синхронизации (программирование репликации на языке Transact-SQL)
  Во время синхронизации агенты репликации выполняют инструкции [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql), [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) и [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) для реплицируемых таблиц, что может вызвать срабатывание триггеров DML для этих таблиц. В некоторых случаях может понадобиться предотвратить срабатывание этих триггеров или применение ограничений во время синхронизации. Эти действия зависят от того, как были созданы триггер или ограничение.  
  
### <a name="to-prevent-triggers-from-executing-during-synchronization"></a>Предотвращение срабатывания триггеров во время синхронизации  
  
1.  При создании нового триггера укажите параметр NOT FOR REPLICATION в инструкции [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).  
  
2.  Для существующего триггера укажите параметр NOT FOR REPLICATION в инструкции [ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql).  
  
### <a name="to-prevent-constraints-from-being-enforced-during-synchronization"></a>Предотвращение применения ограничений во время синхронизации  
  
1.  При создании нового ограничения CHECK или FOREIGN KEY укажите параметр CHECK NOT FOR REPLICATION в ограничении, определяемом инструкцией [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).  
  
## <a name="see-also"></a>См. также  
 [Создание таблиц (ядро СУБД)](../tables/create-tables-database-engine.md)  
  
  
