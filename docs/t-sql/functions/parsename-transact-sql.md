---
title: "PARSENAME (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PARSENAME_TSQL
- PARSENAME
dev_langs:
- TSQL
helpviewer_keywords:
- PARSENAME function
- parsing [SQL Server], PARSENAME function
- names [SQL Server], objects
- objects [SQL Server], names
- part of object names [SQL Server]
ms.assetid: abf34f99-9ee9-460b-85b2-930ca5c4b5ae
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 63065dcee0d1f7784e7be396273785f741ef44c7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="parsename-transact-sql"></a>PARSENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Возвращает указанную часть имени объекта. Части объекта, к которым можно получить доступ: имя объекта, имя владельца, имя базы данных и имя сервера.  
  
> [!NOTE]  
>  Функция PARSENAME не показывает, существует ли на самом деле объект с данным именем. PARSENAME возвращает всего лишь указанную часть имени объекта.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
PARSENAME ( 'object_name' , object_piece )   
```  
  
## <a name="arguments"></a>Аргументы  
 "*object_name*"  
 Имя объекта, из которого будет извлекаться указанная часть. *object_name* — **sysname**. Данный параметр представляет имя объекта, которое необязательно задано полностью. Если указываются все части имени объекта, то это имя может состоять из четырех частей: имени сервера, имени базы данных, имени владельца и имени объекта.  
  
 *object_piece*  
 Часть объекта, которую необходимо вернуть. *object_piece* относится к типу **int**и может принимать следующие значения:  
  
 1 = имя объекта  
  
 2 = имя схемы  
  
 3 = имя базы данных  
  
 4 = имя сервера  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **nchar**  
  
## <a name="remarks"></a>Замечания  
 Функция PARSENAME возвращает значение NULL, если выполняется одно из условий:  
  
-   Либо *object_name* или *object_piece* имеет значение NULL.  
  
-   Синтаксическая ошибка.  
  
 Часть запрошенный объект имеет длину 0 и не является допустимым [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] идентификатор. Нулевая длина имени объекта делает недействительным полное имя объекта.  
  
## <a name="examples"></a>Примеры  
 Следующий пример демонстрирует использование `PARSENAME` для получения информации о таблице `Person` в базе данных `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
SELECT PARSENAME('AdventureWorks2012..Person', 1) AS 'Object Name';  
SELECT PARSENAME('AdventureWorks2012..Person', 2) AS 'Schema Name';  
SELECT PARSENAME('AdventureWorks2012..Person', 3) AS 'Database Name';  
SELECT PARSENAME('AdventureWorks2012..Person', 4) AS 'Server Name';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Object Name`  
  
 `------------------------------`  
  
 `Person`  
  
 `(1 row(s) affected)`  
  
 `Schema Name`  
  
 `------------------------------`  
  
 `(null)`  
  
 `(1 row(s) affected)`  
  
 `Database Name`  
  
 `------------------------------`  
  
 `AdventureWorks2012`  
  
 `(1 row(s) affected)`  
  
 `Server Name`  
  
 `------------------------------`  
  
 `(null)`  
  
 `(1 row(s) affected)`  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Следующий пример демонстрирует использование `PARSENAME` для получения информации о таблице `Person` в базе данных `AdventureWorks2012`.  
  
```  
-- Uses AdventureWorks  
  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 1) AS 'Object Name';  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 2) AS 'Schema Name';  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 3) AS 'Database Name';  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 4) AS 'Server Name';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Object Name`  
  
 `------------------------------`  
  
 `DimCustomer`  
  
 `(1 row(s) affected)`  
  
 `Schema Name`  
  
 `------------------------------`  
  
 `dbo`  
  
 `(1 row(s) affected)`  
  
 `Database Name`  
  
 `------------------------------`  
  
 `AdventureWorksPDW2012`  
  
 `(1 row(s) affected)`  
  
 `Server Name`  
  
 `------------------------------`  
  
 `(null)`  
  
 `(1 row(s) affected)`  
  
## <a name="see-also"></a>См. также:  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [Системные функции &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  


