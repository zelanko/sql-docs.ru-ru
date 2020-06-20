---
title: Реализация IDENTITY в оптимизированной для памяти таблице | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0a704a3-3a31-4c2c-b967-addacda62ef8
author: rothja
ms.author: jroth
ms.openlocfilehash: 793890018d0d7e57e4102d03a9120feb9803b816
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050134"
---
# <a name="implementing-identity-in-a-memory-optimized-table"></a>Реализация IDENTITY в таблице, оптимизированной для памяти
  IDENTITY(1, 1) поддерживается для таблицы, оптимизированной для памяти. Однако столбцы идентификаторов с определением IDENTITY(x, y), где x != 1 или y != 1 для таблиц, оптимизированных для памяти, не поддерживаются. Для обхода этой проблемы значения IDENTITY используют объект SEQUENCE ([Sequence Numbers](../sequence-numbers/sequence-numbers.md)).  
  
 Вначале удалите свойство IDENTITY из таблицы, которая преобразуется в OLTP в памяти. Затем определите новый объект SEQUENCE для столбца таблицы. Объекты SEQUENCE как столбцы идентификаторов зависят от возможности создания для столбцов значений DEFAULT, которые используют синтаксис NEXT VALUE FOR для получения нового значения идентификатора. Поскольку значения DEFAULT не поддерживаются в OLTP в памяти, необходимо передать вновь созданное значение SEQUENCE в инструкцию INSERT или в скомпилированную хранимую процедуру, которая выполняет вставку. Следующий пример демонстрирует этот подход.  
  
```sql  
-- Create a new In-Memory OLTP table to simulate IDENTITY insert  
-- Here the column C1 was the identity column in the original table  
--  
create table T1  
(  
  
[c1] integer not null primary key T1_c1 nonclustered,  
[c2] varchar(32) not null,  
[c3] datetime not null  
  
) with (memory_optimized = on)  
go  
  
-- This is a sequence provider that will give us values for column [c1]  
--  
create sequence usq_SequenceForT1 as integer start with 2 increment by 1  
go  
  
--   insert a sample row using the sequence  
--   note that a new value needs to be retrieved form   
--   the sequence object for every insert  
--  
declare @c1 integer = next value for [dbo].[usq_SequenceForT1]  
insert into T1 values (@c1, 'test', getdate())  
```  
  
 После выполнения нескольких вставок можно увидеть монотонно возрастающие значения в столбце [c1]. Этот результирующий набор создан с помощью просмотра таблицы и хэш-индекса без `ORDER BY`, поэтому строки не упорядочены.  
  
## <a name="see-also"></a>См. также:  
 [Миграция в In-Memory OLTP](migrating-to-in-memory-oltp.md)  
  
  
