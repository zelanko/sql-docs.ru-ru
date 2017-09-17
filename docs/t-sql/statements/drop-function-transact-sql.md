---
title: "ФУНКЦИЯ СБРОСА (Transact-SQL) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/28/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_FUNCTION_TSQL
- DROP FUNCTION
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined functions [SQL Server], removing
- removing user-defined functions
- DROP FUNCTION statement
- dropping user-defined functions
- deleting user-defined functions
ms.assetid: ee5ad283-9e44-4109-902f-0ce12669ee11
caps.latest.revision: 49
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3b85cb68749cdcf88d62d9d8fbf136a37e845519
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="drop-function-transact-sql"></a>DROP FUNCTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-_md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Удаляет из текущей базы данных одну или несколько пользовательских функций. Определяемые пользователем функции создаются с помощью [CREATE FUNCTION](../../t-sql/statements/create-function-transact-sql.md) и изменяются с помощью [ALTER FUNCTION](../../t-sql/statements/alter-function-transact-sql.md).  
  
 Функция СБРОСА поддерживает скомпилированных в собственном коде скалярные определяемые пользователем функции. Дополнительные сведения см. в разделе [скалярные определяемые пользователем функции для In-Memory OLTP](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
 -- SQL Server, Azure SQL Database 

DROP FUNCTION [ IF EXISTS ] { [ schema_name. ] function_name } [ ,...n ]   
[;]
```

```  
 -- Azure SQL Data Warehouse, Parallel Data Warehouse 

DROP FUNCTION [ schema_name. ] function_name
[;] 
```  
   
  
## <a name="arguments"></a>Аргументы  
 *ЕСЛИ СУЩЕСТВУЕТ*    
 Условно удаляет функции только в том случае, если он уже существует. Доступно для [!INCLUDE[ssnoversion_md](../../includes/ssnoversion_md.md)] 2016 и в [!INCLUDE[sssds_md](../../includes/sssds_md.md)].
  
 *schema_name*  
 Имя схемы, к которой принадлежит определяемая пользователем функция.  
  
 *имя функции*  
 Имя удаляемой пользовательской функции или функций. Указание имени схемы является необязательным. Невозможно указать имя сервера и имя базы данных.  
  
## <a name="remarks"></a>Замечания  
 При выполнении инструкции DROP FUNCTION произойдет сбой, если в базе данных существуют функции или представления языка [!INCLUDE[tsql](../../includes/tsql-md.md)], созданные с ключевым словом SCHEMABINDING и содержащие ссылки на удаляемую функцию, или если база данных содержит вычисляемые столбцы, ограничения CHECK или DEFAULT, которые ссылаются на эту функцию.  
  
 При выполнении инструкции DROP FUNCTION произойдет сбой, если имеются вычисляемые столбцы, которые содержат ссылки на удаляемую функцию и которые были проиндексированы.  
  
## <a name="permissions"></a>Permissions  
 Для вызова инструкции DROP FUNCTION у пользователя должно быть как минимум разрешение ALTER на схему, которой принадлежит функция, или разрешение CONTROL на функцию.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-dropping-a-function"></a>A. Удаление функции  
 В следующем примере удаляется `fn_SalesByStore` определяемой пользователем функции из `Sales` схемы в [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] образца базы данных. Для создания этой функции, см. пример Б в [CREATE FUNCTION &#40; Transact-SQL &#41; ](../../t-sql/statements/create-function-transact-sql.md).  
  
```  
DROP FUNCTION Sales.fn_SalesByStore;  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER FUNCTION (Transact-SQL)](../../t-sql/statements/alter-function-transact-sql.md)   
 [CREATE FUNCTION (Transact-SQL)](../../t-sql/statements/create-function-transact-sql.md)   
 [Object_id &#40; Transact-SQL &#41;](../../t-sql/functions/object-id-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.parameters &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)  
  
  

