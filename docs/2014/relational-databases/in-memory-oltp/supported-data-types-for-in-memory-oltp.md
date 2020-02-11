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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63155158"
---
# <a name="supported-data-types"></a>Поддерживаемые типы данных
  Следующие типы данных **поддерживаются** для оптимизированных для памяти таблиц и хранимых процедур, скомпилированных в собственном коде.  
  
 **Числовые типы данных**  
  
|Тип данных|Дополнительные сведения|  
|---------------|--------------------------|  
|INT|[int, bigint, smallint и tinyint &#40;Transact-SQL&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|bigint|[int, bigint, smallint и tinyint &#40;Transact-SQL&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|smallint|[int, bigint, smallint и tinyint &#40;Transact-SQL&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|tinyint;|[int, bigint, smallint и tinyint &#40;Transact-SQL&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|Decimal|[десятичные и числовые &#40;&#41;Transact-SQL](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)|  
|NUMERIC|[десятичные и числовые &#40;&#41;Transact-SQL](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)|  
|FLOAT|[&#41;с плавающей запятой и реальным &#40;Transact-SQL](/sql/t-sql/data-types/float-and-real-transact-sql)|  
|real;|[&#41;с плавающей запятой и реальным &#40;Transact-SQL](/sql/t-sql/data-types/float-and-real-transact-sql)|  
|money|[средства Money и smallmoney &#40;Transact-SQL&#41;](/sql/t-sql/data-types/money-and-smallmoney-transact-sql)|  
|smallmoney|[средства Money и smallmoney &#40;Transact-SQL&#41;](/sql/t-sql/data-types/money-and-smallmoney-transact-sql)|  
  
 **Строковые типы данных**  
  
|Тип данных|Дополнительные сведения|  
|---------------|--------------------------|  
|char(n)|[char и varchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/char-and-varchar-transact-sql)|  
|varchar (n) <sup>1</sup>|[char и varchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/char-and-varchar-transact-sql)|  
|nchar(n)|[nchar и nvarchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
|nvarchar (n) <sup>1</sup>|[nchar и nvarchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
|sysname|[nchar и nvarchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
  
 <sup>1</sup> ограничение составляет 8060 байт на строку, считая (n) в типах переменной длины.  
  
 Дополнительные сведения о поддерживаемых параметрах сортировки см. в разделе [Collations and Code Pages](../../database-engine/collations-and-code-pages.md).  
  
 **Типы данных даты и времени**  
  
|Тип данных|Дополнительные сведения|  
|---------------|--------------------------|  
|Дата|[Дата &#40;&#41;Transact-SQL](/sql/t-sql/data-types/date-transact-sql)|  
|time|[время &#40;&#41;Transact-SQL](/sql/t-sql/data-types/time-transact-sql)|  
|DATETIME|[DateTime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql)|  
|datetime2|[datetime2 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime2-transact-sql)|  
|smalldatetime|[smalldatetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/smalldatetime-transact-sql)|  
  
 **Двоичные типы данных**  
  
|Тип данных|Дополнительные сведения|  
|---------------|--------------------------|  
|bit|[разрядный &#40;&#41;Transact-SQL](/sql/t-sql/data-types/bit-transact-sql)|  
|binary(n)|[двоичные и varbinary &#40;Transact-SQL&#41;](/sql/t-sql/data-types/binary-and-varbinary-transact-sql)|  
|varbinary (n) <sup>1</sup>|[двоичные и varbinary &#40;Transact-SQL&#41;](/sql/t-sql/data-types/binary-and-varbinary-transact-sql)|  
  
 <sup>1</sup> ограничение составляет 8060 байт на строку, считая (n) в типах переменной длины.  
  
 **Другие типы данных**  
  
|Тип данных|Дополнительные сведения|  
|---------------|--------------------------|  
|UNIQUEIDENTIFIER|[&#40;uniqueidentifier&#41;Transact-SQL](/sql/t-sql/data-types/uniqueidentifier-transact-sql)|  
  
 **Неподдерживаемые типы данных**  
  
 Следующие типы данных не поддерживаются:  
  
||||  
|-|-|-|  
|DATETIMEOFFSET|GEOGRAPHY|GEOMETRY|  
|HIERARCHYID|Большие объекты (LOB). Например, varchar(max), nvarchar(max), varbinary(max), image, xml, text и ntext.|ROWVERSION|  
|sql_variant|Функции среды CLR|Определяемые пользователем типы|  
  
## <a name="see-also"></a>См. также:  
 [Поддержка Transact-SQL для выполняющейся в памяти OLTP](transact-sql-support-for-in-memory-oltp.md)   
 [Реализация столбцов LOB в таблице, оптимизированной для памяти](../../database-engine/implementing-lob-columns-in-a-memory-optimized-table.md)   
 [Реализация SQL_VARIANT в таблице, оптимизированной для памяти](implementing-sql-variant-in-a-memory-optimized-table.md)  
  
  
