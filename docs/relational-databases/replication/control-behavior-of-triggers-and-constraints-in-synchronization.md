---
title: Управление поведением триггеров и ограничений при синхронизации | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
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
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a77f0405c9e5df1e1e49f426f065df4c7c1619c5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67903074"
---
# <a name="control-behavior-of-triggers-and-constraints-in-synchronization"></a>Управление поведением триггеров и ограничений при синхронизации
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Во время синхронизации агенты репликации выполняют инструкции [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md), [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md) и [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md) для реплицируемых таблиц, что может вызвать срабатывание триггеров DML для этих таблиц. В некоторых случаях может понадобиться предотвратить срабатывание этих триггеров или применение ограничений во время синхронизации. Эти действия зависят от того, как были созданы триггер или ограничение.  
  
### <a name="to-prevent-triggers-from-executing-during-synchronization"></a>Предотвращение срабатывания триггеров во время синхронизации  
  
1.  При создании нового триггера укажите параметр NOT FOR REPLICATION в инструкции [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md).  
  
2.  Для существующего триггера укажите параметр NOT FOR REPLICATION в инструкции [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md).  
  
### <a name="to-prevent-constraints-from-being-enforced-during-synchronization"></a>Предотвращение применения ограничений во время синхронизации  
  
1.  При создании нового ограничения CHECK или FOREIGN KEY укажите параметр CHECK NOT FOR REPLICATION в ограничении, определяемом инструкцией [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [Создание таблиц (ядро СУБД)](../../relational-databases/tables/create-tables-database-engine.md)  
  
  
