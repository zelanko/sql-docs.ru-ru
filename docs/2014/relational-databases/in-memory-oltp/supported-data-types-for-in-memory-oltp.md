---
title: Поддерживаемые типы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a7380ef0-c9d7-49e4-b6de-fad34752b9f3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: de5f805a9d722974adf7975f713436bc7b1ca4d0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63155158"
---
# <a name="supported-data-types"></a>Поддерживаемые типы данных
  Следующие типы данных **поддерживаются** для оптимизированных для памяти таблиц и хранимых процедур, скомпилированных в собственном коде.  
  
 **Числовые типы данных**  
  
|Тип данных|Дополнительные сведения|  
|---------------|--------------------------|  
|ssNoversion|[int, bigint, smallint и tinyint (Transact-SQL)](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|BIGINT|[int, bigint, smallint и tinyint (Transact-SQL)](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|smallint|[int, bigint, smallint и tinyint (Transact-SQL)](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|tinyint|[int, bigint, smallint и tinyint (Transact-SQL)](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|Decimal|[decimal и numeric (Transact-SQL)](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)|  
|NUMERIC|[decimal и numeric (Transact-SQL)](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)|  
|FLOAT|[Типы данных float и real (Transact-SQL)](/sql/t-sql/data-types/float-and-real-transact-sql)|  
|real|[Типы данных float и real (Transact-SQL)](/sql/t-sql/data-types/float-and-real-transact-sql)|  
|money|[Типы money и smallmoney (Transact-SQL)](/sql/t-sql/data-types/money-and-smallmoney-transact-sql)|  
|smallmoney|[Типы money и smallmoney (Transact-SQL)](/sql/t-sql/data-types/money-and-smallmoney-transact-sql)|  
  
 **Строковыми типами данных**  
  
|Тип данных|Дополнительные сведения|  
|---------------|--------------------------|  
|char(n)|[char и varchar (Transact-SQL)](/sql/t-sql/data-types/char-and-varchar-transact-sql)|  
|varchar(n) <sup>1</sup>|[char и varchar (Transact-SQL)](/sql/t-sql/data-types/char-and-varchar-transact-sql)|  
|nchar(n)|[nchar и nvarchar (Transact-SQL)](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
|nvarchar(n) <sup>1</sup>|[nchar и nvarchar (Transact-SQL)](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
|sysname|[nchar и nvarchar (Transact-SQL)](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
  
 <sup>1</sup> ограничение равно 8060 байт на строку в целом с учетом (n) в типах переменной длины.  
  
 Дополнительные сведения о поддерживаемых параметрах сортировки см. в разделе [Collations and Code Pages](../../database-engine/collations-and-code-pages.md).  
  
 **Типы данных даты и времени**  
  
|Тип данных|Дополнительные сведения|  
|---------------|--------------------------|  
|date|[date &#40;Transact-SQL&#41;](/sql/t-sql/data-types/date-transact-sql)|  
|time|[time (Transact-SQL)](/sql/t-sql/data-types/time-transact-sql)|  
|datetime|[datetime (Transact-SQL)](/sql/t-sql/data-types/datetime-transact-sql)|  
|datetime2|[datetime2 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime2-transact-sql)|  
|smalldatetime|[smalldatetime (Transact-SQL)](/sql/t-sql/data-types/smalldatetime-transact-sql)|  
  
 **Двоичные типы данных**  
  
|Тип данных|Дополнительные сведения|  
|---------------|--------------------------|  
|bit|[bit (Transact-SQL)](/sql/t-sql/data-types/bit-transact-sql)|  
|binary(n)|[binary и varbinary (Transact-SQL)](/sql/t-sql/data-types/binary-and-varbinary-transact-sql)|  
|varbinary(n) <sup>1</sup>|[binary и varbinary (Transact-SQL)](/sql/t-sql/data-types/binary-and-varbinary-transact-sql)|  
  
 <sup>1</sup> ограничение равно 8060 байт на строку в целом с учетом (n) в типах переменной длины.  
  
 **Другие типы данных**  
  
|Тип данных|Дополнительные сведения|  
|---------------|--------------------------|  
|UNIQUEIDENTIFIER|[uniqueidentifier (Transact-SQL)](/sql/t-sql/data-types/uniqueidentifier-transact-sql)|  
  
 **Неподдерживаемые типы данных**  
  
 Следующие типы данных не поддерживаются:  
  
||||  
|-|-|-|  
|DATETIMEOFFSET|GEOGRAPHY|GEOMETRY|  
|HIERARCHYID|Большие объекты (LOB). Например, varchar(max), nvarchar(max), varbinary(max), image, xml, text и ntext.|ROWVERSION|  
|sql_variant|Функции среды CLR|Определяемые пользователем типы|  
  
## <a name="see-also"></a>См. также  
 [Поддержка Transact-SQL для In-Memory OLTP](transact-sql-support-for-in-memory-oltp.md)   
 [Реализация LOB Columns в таблице, оптимизированной для памяти](../../database-engine/implementing-lob-columns-in-a-memory-optimized-table.md)   
 [Реализация SQL_VARIANT в таблице, оптимизированной для памяти](implementing-sql-variant-in-a-memory-optimized-table.md)  
  
  
