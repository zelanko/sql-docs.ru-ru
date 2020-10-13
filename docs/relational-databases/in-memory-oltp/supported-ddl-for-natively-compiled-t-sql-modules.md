---
title: Поддерживаемые конструкции DDL для модулей T-SQL, скомпилированных в собственном коде | Документация Майкрософт
description: Сведения о поддерживаемых конструкциях DDL для модулей T-SQL, скомпилированных в машинный код, в частности хранимых процедурах, определяемых пользователем скалярных функциях, встроенных функциях, возвращающих табличные значения и триггерах.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6b21f47e-bceb-4054-8b3c-9d39bb9583c0
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9e7dc391e0f199ab6ab8855599506bb01365333a
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91868478"
---
# <a name="supported-ddl-for-natively-compiled-t-sql-modules"></a>Поддерживаемые конструкции DDL для модулей, скомпилированных в собственном коде T-SQL
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  В этой статье перечислены поддерживаемые конструкции DDL для модулей, скомпилированных в собственном коде T-SQL, в частности хранимые процедуры, определяемые пользователем скалярные функции, встроенные возвращающие табличное значение функции и триггеры.  
  
 Сведения о возможностях и контактной зоне T-SQL, которые можно использовать в составе модулей, скомпилированных в собственном коде T-SQL, см. в статье [Поддерживаемые функции для модулей, скомпилированных в собственном коде T-SQL](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md).  
  
 Дополнительные сведения о неподдерживаемых конструкциях см. в разделе [Конструкции языка Transact-SQL, не поддерживаемые в In-Memory OLTP](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
 Поддерживаются следующие конструкции:  
  
-   [CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md)  
  
-   [DROP PROCEDURE (Transact-SQL)](../../t-sql/statements/drop-procedure-transact-sql.md)  
  
-   [ALTER PROCEDURE (Transact-SQL)](../../t-sql/statements/alter-procedure-transact-sql.md)  
  
-   Инструкции [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md) и INSERT SELECT  
  
-   SCHEMABINDING и BEGIN ATOMIC (требуется для хранимых процедур, скомпилированных в собственном коде)  
  
     Дополнительные сведения см. в статье [Скомпилированные в собственном коде хранимые процедуры](../../relational-databases/in-memory-oltp/creating-natively-compiled-stored-procedures.md).  
  
-   NATIVE_COMPILATION  
  
     Дополнительные сведения см. в статье [Собственная компиляция таблиц и хранимых процедур](../../relational-databases/in-memory-oltp/native-compilation-of-tables-and-stored-procedures.md).  
  
-   Параметры и переменные могут быть объявлены как NOT NULL (доступно только для модулей, скомпилированных в собственном коде: скомпилированные в собственном коде хранимые процедуры и скомпилированные в собственном коде скалярные функции, определяемые пользователем).  
  
-   Возвращающие табличные значения параметры  
  
     Дополнительные сведения см. в статье [Использование возвращающих табличные значения параметров (компонент Database Engine)](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).  
  
-   EXECUTE AS OWNER, SELF, CALLER и пользователь.  
  
-   Разрешения GRANT и DENY для таблиц и процедур.  
  
     Дополнительные сведения см. в статьях [Разрешения объекта GRANT (Transact-SQL)](../../t-sql/statements/grant-object-permissions-transact-sql.md) и [Разрешения объекта DENY (Transact-SQL)](../../t-sql/statements/deny-object-permissions-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [Скомпилированные в собственном коде хранимые процедуры](./a-guide-to-query-processing-for-memory-optimized-tables.md)  
  
