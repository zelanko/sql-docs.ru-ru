---
title: PARSENAME (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/02/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
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
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 915cf95799a80a0d8841206f4b23b04fba5fec5f
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "87112371"
---
# <a name="parsename-transact-sql"></a>PARSENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Возвращает указанную часть имени объекта. Части объекта, к которым можно получить доступ: имя объекта, имя схемы, имя базы данных и имя сервера. 
  
> [!NOTE]  
>  Функция PARSENAME не показывает, существует ли на самом деле объект с данным именем. PARSENAME возвращает всего лишь указанную часть имени объекта.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql 
PARSENAME ('object_name' , object_piece )
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы

*«object_name»* — параметр, содержащий имя объекта, из которого будет извлекаться указанный элемент объекта. Данный параметр представляет имя объекта, которое необязательно задано полностью. Если указываются все части имени объекта, то это имя может состоять из четырех частей: имени сервера, имени базы данных, имени схемы и имени объекта.  Каждая часть строки «object_name» имеет тип *sysname* что эквивалентно типу nvarchar (128) или 256 байтам. Если какая-либо часть строки превышает 256 байт, PARSENAME вернет значение NULL для этой части, так как оно не является допустимым значением sysname.
  
*object_piece*  
Часть объекта, которую необходимо вернуть. Аргумент *object_piece* имеет тип **int** и может принимать следующие значения:  
    1 = имя объекта  
    2 = имя схемы  
    3 = имя базы данных  
    4 = имя сервера  
  
## <a name="return-type"></a>Тип возвращаемых данных

 **sysname**
  
## <a name="remarks"></a>Remarks

 Функция PARSENAME возвращает значение NULL, если выполняется одно из условий:  
  
-   Либо аргумент *object_name*, либо аргумент *object_piece* имеет значение NULL.  
  
-   Синтаксическая ошибка.  
  
 Длина запрошенной части имени равна 0 и не является допустимым идентификатором [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Нулевая длина имени объекта делает недействительным полное имя объекта.  
  
## <a name="examples"></a>Примеры

 Следующий пример демонстрирует использование `PARSENAME` для получения информации о таблице `Person` в базе данных `AdventureWorks2012`.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 1) AS 'Object Name';  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 2) AS 'Schema Name';  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 3) AS 'Database Name';  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 4) AS 'Server Name';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
```
Object Name
------------------------------
DimCustomer

(1 row(s) affected)

Schema Name
------------------------------
dbo

(1 row(s) affected)

Database Name
------------------------------
AdventureWorksPDW2012

(1 row(s) affected)

Server Name
------------------------------
(null)

(1 row(s) affected)
```
  
## <a name="see-also"></a>См. также:

- [QUOTENAME (Transact-SQL)](../../t-sql/functions/quotename-transact-sql.md)  
- [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
- [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
- [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-category-transact-sql.md)  
  
  

