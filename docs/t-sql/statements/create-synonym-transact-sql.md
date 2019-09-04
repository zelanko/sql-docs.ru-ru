---
title: CREATE SYNONYM (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 04/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CREATE_SYNONYM_TSQL
- SYNONYM_TSQL
- SYNONYM
- CREATE SYNONYM
dev_langs:
- TSQL
helpviewer_keywords:
- alternate names [SQL Server]
- names [SQL Server], synonyms
- CREATE SYNONYM statement
- synonyms [SQL Server], creating
ms.assetid: 41313809-e970-449c-bc35-85da2ef96e48
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 78dd9533a33d3b28f4fffcb2bb0ff4cd6604713f
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70155816"
---
# <a name="create-synonym-transact-sql"></a>CREATE SYNONYM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Создание нового синонима.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- SQL Server Syntax  
  
CREATE SYNONYM [ schema_name_1. ] synonym_name FOR <object>  
  
<object> :: =  
{  
    [ server_name.[ database_name ] . [ schema_name_2 ]. object_name   
  | database_name . [ schema_name_2 ].| schema_name_2. ] object_name  
}  
```  
  
```  
-- Azure SQL Database Syntax  
  
CREATE SYNONYM [ schema_name_1. ] synonym_name FOR < object >  
  
< object > :: =  
{  
    [database_name. [ schema_name_2 ].| schema_name_2. ] object_name  
}  
```  
  
## <a name="arguments"></a>Аргументы  
 *schema_name_1*  
 Указывает схему, в которой создается новый синоним. Если *schema* не указана, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует применяемую по умолчанию схему текущего пользователя.  
  
 *synonym_name*  
 Имя нового синонима.  
  
 *server_name*  
 **Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Имя сервера, на котором расположен базовый объект.  
  
 *database_name*  
 Имя базы данных, в которой расположен базовый объект. Если не задано *database_name*, используется имя текущей базы данных.  
  
 *schema_name_2*  
 Имя схемы базового объекта. Если не задан аргумент *schema_name*, используется схема по умолчанию текущего пользователя.  
  
 *object_name*  
 Имя базового объекта, на который ссылается синоним.  
  
 База данных SQL Azure поддерживает формат трехкомпонентного имени имя_базы_данных.[имя_схемы].имя_объекта, если имя_базы_данных — это текущая база данных или tempdb, а имя_объекта начинается с символа #.  
  
## <a name="remarks"></a>Remarks  
 Базовый объект может не существовать в момент создания синонима. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверяется наличие базового объекта во время выполнения.  
  
 Синонимы могут создаваться для следующих типов объектов:  
  
|||  
|-|-|  
|Хранимая процедура сборки (среда CLR)|Функция сборки с табличным значением(среда CLR)|  
|Скалярная функция сборки (среда CLR)|Агрегатные функции сборки (среда CLR)|  
|Процедура фильтра репликации|Расширенная хранимая процедура|  
|Скалярная функция SQL|функция SQL с табличным значением|  
|Встроенная функция SQL с табличным значением|Хранимая процедура SQL|  
|Представление|Таблица<sup>1</sup> (пользовательская)|  
  
 <sup>1 включает локальные и глобальные временные таблицы</sup>  
  
 Имена, состоящие из четырех элементов, для базовых объектов-функций не поддерживаются.  
  
 Синонимы можно создавать, удалять и ссылаться на них в динамическом SQL.  
  
## <a name="permissions"></a>Разрешения  
 Для создания синонима в заданной схеме пользователь должен иметь разрешение CREATE SYNONYM и, либо владеть схемой, либо иметь разрешение ALTER SCHEMA.  
  
 Разрешение на выполнение CREATE SYNONYM можно предоставлять.  
  
> [!NOTE]  
>  Чтобы успешно скомпилировать инструкцию CREATE SYNONYM, необязательно иметь разрешение на базовый объект, потому что проверка всех разрешений на базовые объекты откладывается до времени выполнения.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-synonym-for-a-local-object"></a>A. Создание синонима для локального объекта  
 В следующем примере сначала создается синоним для базового объекта `Product` в базе данных `AdventureWorks2012`, а затем выполняется запрос к этому синониму.  
  
```  
-- Create a synonym for the Product table in AdventureWorks2012.  
CREATE SYNONYM MyProduct  
FOR AdventureWorks2012.Production.Product;  
GO  
  
-- Query the Product table by using the synonym.  
SELECT ProductID, Name   
FROM MyProduct  
WHERE ProductID < 5;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ----------------------- 
 ProductID   Name 
 ----------- -------------------------- 
 1           Adjustable Race 
 2           Bearing Ball 
 3           BB Ball Bearing 
 4           Headset Ball Bearings 

 (4 row(s) affected)
``` 
  
### <a name="b-creating-a-synonym-to-remote-object"></a>Б. Создание синонима для удаленного объекта  
 В следующем примере базовый объект, `Contact`, находится на удаленном сервере с именем `Server_Remote`.  
  
**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
EXEC sp_addlinkedserver Server_Remote;  
GO  
USE tempdb;  
GO  
CREATE SYNONYM MyEmployee FOR Server_Remote.AdventureWorks2012.HumanResources.Employee;  
GO  
```  
  
### <a name="c-creating-a-synonym-for-a-user-defined-function"></a>В. Создание синонима для определяемой пользователем функции  
 В следующем примере создается функция с именем `dbo.OrderDozen`, которая увеличивает объем заказа до целого числа дюжин. Затем в примере создается синоним `dbo.CorrectOrder` для функции `dbo.OrderDozen`.  
  
```  
-- Creating the dbo.OrderDozen function  
CREATE FUNCTION dbo.OrderDozen (@OrderAmt int)  
RETURNS int  
WITH EXECUTE AS CALLER  
AS  
BEGIN  
IF @OrderAmt % 12 <> 0  
BEGIN  
    SET @OrderAmt +=  12 - (@OrderAmt % 12)  
END  
RETURN(@OrderAmt);  
END;  
GO  
  
-- Using the dbo.OrderDozen function  
DECLARE @Amt int;  
SET @Amt = 15;  
SELECT @Amt AS OriginalOrder, dbo.OrderDozen(@Amt) AS ModifiedOrder;  
  
-- Create a synonym dbo.CorrectOrder for the dbo.OrderDozen function.  
CREATE SYNONYM dbo.CorrectOrder  
FOR dbo.OrderDozen;  
GO  
  
-- Using the dbo.CorrectOrder synonym.  
DECLARE @Amt int;  
SET @Amt = 15;  
SELECT @Amt AS OriginalOrder, dbo.CorrectOrder(@Amt) AS ModifiedOrder;  
```  
  
## <a name="see-also"></a>См. также:  
 [DROP SYNONYM (Transact-SQL)](../../t-sql/statements/drop-synonym-transact-sql.md)   
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
