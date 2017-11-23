---
title: "PARSENAME (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PARSENAME_TSQL
- PARSENAME
dev_langs: TSQL
helpviewer_keywords:
- PARSENAME function
- parsing [SQL Server], PARSENAME function
- names [SQL Server], objects
- objects [SQL Server], names
- part of object names [SQL Server]
ms.assetid: abf34f99-9ee9-460b-85b2-930ca5c4b5ae
caps.latest.revision: "38"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 25ef79b303580c63355df0de6e29898fa67809c1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="parsename-transact-sql"></a>PARSENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Возвращает указанную часть имени объекта. Части объекта, к которым можно получить доступ: имя объекта, имя владельца, имя базы данных и имя сервера.  
  
> [!NOTE]  
>  Функция PARSENAME не показывает, существует ли на самом деле объект с данным именем. PARSENAME возвращает всего лишь указанную часть имени объекта.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [Системные функции &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  

