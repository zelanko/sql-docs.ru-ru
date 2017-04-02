---
title: "Поддерживаемые типы данных для выполняющейся в памяти OLTP | Microsoft Docs"
ms.custom: ""
ms.date: "05/27/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a7380ef0-c9d7-49e4-b6de-fad34752b9f3
caps.latest.revision: 26
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 26
---
# Поддерживаемые типы данных для выполняющейся в памяти OLTP
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  В этой статье перечислены типы данных, которые не поддерживаются для компонентов выполняющейся в памяти OLTP:  
  
-   Таблицы, оптимизированные для памяти  
  
-   Скомпилированные в собственном коде хранимые процедуры  
  
## Неподдерживаемые типы данных  
 Следующие типы данных не поддерживаются:  
  
||||  
|-|-|-|  
|[datetimeoffset (Transact-SQL)](../../t-sql/data-types/datetimeoffset-transact-sql.md)|[geography (Transact-SQL)](../Topic/geography%20\(Transact-SQL\).md)|[geometry (Transact-SQL)](../Topic/geometry%20\(Transact-SQL\).md)|  
|[hierarchyid (Transact-SQL)](../Topic/hierarchyid%20\(Transact-SQL\).md)|[rowversion (Transact-SQL)](../../t-sql/data-types/rowversion-transact-sql.md)|[xml (Transact-SQL)](../../t-sql/xml/xml-transact-sql.md)|  
|[sql_variant (Transact-SQL)](../../t-sql/data-types/sql-variant-transact-sql.md)|Определяемые пользователем типы|.|  
  
## Важные поддерживаемые типы данных  
 Большинство типов данных поддерживаются компонентами выполняющейся в памяти OLTP. Обратите внимание на следующие компоненты:  
  
|Строковые и двоичные типы|Дополнительные сведения|  
|-----------------------------|--------------------------|  
|binary и varbinary*|[binary и varbinary (Transact-SQL)](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|  
|char и varchar*|[char и varchar (Transact-SQL)](../../t-sql/data-types/char-and-varchar-transact-sql.md)|  
|nchar и nvarchar*|[nchar и nvarchar (Transact-SQL)](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)|  
  
Для предшествующих строковых и двоичных типов данных, начиная с SQL Server 2016:  
  
- Отдельная оптимизированная для памяти таблица может также содержать несколько столбцов типа long, например `nvarchar(4000)`, даже если их совокупная длина превысит размер физической строки 8060 байт.  
  
- Оптимизированная для памяти таблица может содержать строковые и двоичные столбцы с максимальной длиной таких типов данных, например `varchar(max)`.  


### Определение LOB-столбцов и других столбцов вне строки

Следующая инструкция Transact-SQL SELECT возвращает все столбцы вне строки для таблиц, оптимизированных для памяти. Обратите внимание на следующее.

- Все ключевые столбцы индекса сохранены в строке.
  - Теперь ключи неуникальных индексов могут включать столбцы со значениями NULL в таблицах, оптимизированных для памяти.
  - Индексы могут быть объявлены как UNIQUE для таблицы, оптимизированной для памяти.
- Все столбцы LOB хранятся вне строки.
- max_lengthax_length со значением -1 означает столбец большого объекта (LOB).


```tsql
SELECT
        OBJECT_NAME(m.object_id) as [table],
        c.name                   as [column],
        c.max_length
    FROM
             sys.memory_optimized_tables_internal_attributes AS m
        JOIN sys.columns                                     AS c
                ON  m.object_id = c.object_id
                AND m.minor_id  = c.column_id
    WHERE
        m.type = 5;
```


#### Поддержка скомпилированных в собственном коде модулей для LOB


Встроенная строковая функция, используемая в скомпилированных в собственном коде модулях, например в процедуре, скомпилированной в собственном коде, может принимать строковый тип LOB. Например в процедуре, скомпилированной в собственном коде, функция LTrim может ввести параметр типа nvarchar(max) или varbinary(max).

Эти типы LOB могут быть возвращаемым типом определяемой пользователем скалярной функции (UDF).


### Прочие типы данных


|Другие типы|Дополнительные сведения|  
|-----------------|--------------------------|  
|табличные типы|[Переменные оптимизированной для памяти таблицы](../Topic/Memory-Optimized%20Table%20Variables.md)|  
  
## См. также:  
 [Поддержка Transact-SQL для In-Memory OLTP](../../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)   
 [Реализация LOB Columns в таблице, оптимизированной для памяти](http://msdn.microsoft.com/ru-ru/bd8df0a5-12b9-4f4c-887c-2fb78dd79f4e)   
 [Реализация SQL_VARIANT в таблице, оптимизированной для памяти](../../relational-databases/in-memory-oltp/implementing-sql-variant-in-a-memory-optimized-table.md)  
  
  