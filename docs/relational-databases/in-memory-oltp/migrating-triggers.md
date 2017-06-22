---
title: "Перенос триггеров | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad5385c5-5a50-40ca-a319-97d5606b8511
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3a9c1baf562c88910708c20682d48a118c81da25
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="migrating-triggers"></a>Перенос триггеров
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  В этой статье описаны триггеры DDL, а также оптимизированные для памяти таблицы.  
  
 Триггеры DML поддерживаются в таблицах, оптимизированных для памяти, но только с событием-триггером FOR | AFTER. Пример см. в разделе [Реализация инструкции UPDATE с предложением FROM или вложенными запросами](../../relational-databases/in-memory-oltp/implementing-update-with-from-or-subqueries.md). 
  
 Триггеры LOGON и триггеры, определенные для вызова событий LOGON. Триггеры LOGON не оказывают влияния на оптимизированные для памяти таблицы.  
  
## <a name="ddl-triggers"></a>Триггеры DDL  
 Триггеры DDL — это триггеры, которые срабатывают при выполнении на сервере, на котором они определены, инструкции CREATE, ALTER, DROP, GRANT, DENY, REVOKE или UPDATE STATISTICS для базы данных.  
  
 Нельзя создать оптимизированные для памяти таблицы, если в базе данных или на сервере определен один или несколько триггеров DDL для события CREATE_TABLE или любой группы событий, которая содержит это событие. Нельзя удалить оптимизированную для памяти таблицу, если в базе данных или на сервере определен один или несколько триггеров DDL для события DROP_TABLE или любой группы событий, которая содержит это событие.  
  
 При наличии одного или нескольких триггеров DDL для событий CREATE_PROCEDURE и DROP_PROCEDURE или любой группы событий, в которую входят эти события, нельзя создавать скомпилированные в собственном коде хранимые процедуры.  
  
## <a name="see-also"></a>См. также:  
 [Миграция в In-Memory OLTP](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  
