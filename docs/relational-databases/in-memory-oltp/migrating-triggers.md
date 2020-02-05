---
title: Перенос триггеров | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: ad5385c5-5a50-40ca-a319-97d5606b8511
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4629b9f18cdf0b97b5a79cff0696973cb60f7c36
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68050152"
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
  
  
