---
title: "Перенос триггеров | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad5385c5-5a50-40ca-a319-97d5606b8511
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a2f151fa00c2e92ef1509ea2c6d7d93e8c8d2c69
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="migrating-triggers"></a>Перенос триггеров
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  В этой статье описаны триггеры DDL, а также оптимизированные для памяти таблицы.  
  
 Триггеры DML поддерживаются в таблицах, оптимизированных для памяти, но только с событием-триггером FOR | AFTER. Пример см. в разделе [Реализация инструкции UPDATE с предложением FROM или вложенными запросами](../../relational-databases/in-memory-oltp/implementing-update-with-from-or-subqueries.md). 
  
 Триггеры LOGON и триггеры, определенные для вызова событий LOGON. Триггеры LOGON не оказывают влияния на оптимизированные для памяти таблицы.  
  
## <a name="ddl-triggers"></a>Триггеры DDL  
 Триггеры DDL — это триггеры, которые срабатывают при выполнении на сервере, на котором они определены, инструкции CREATE, ALTER, DROP, GRANT, DENY, REVOKE или UPDATE STATISTICS для базы данных.  
  
 Нельзя создать оптимизированные для памяти таблицы, если в базе данных или на сервере определен один или несколько триггеров DDL для события CREATE_TABLE или любой группы событий, которая содержит это событие. Нельзя удалить оптимизированную для памяти таблицу, если в базе данных или на сервере определен один или несколько триггеров DDL для события DROP_TABLE или любой группы событий, которая содержит это событие.  
  
 При наличии одного или нескольких триггеров DDL для событий CREATE_PROCEDURE и DROP_PROCEDURE или любой группы событий, в которую входят эти события, нельзя создавать скомпилированные в собственном коде хранимые процедуры.  
  
## <a name="see-also"></a>См. также:  
 [Миграция в In-Memory OLTP](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  
