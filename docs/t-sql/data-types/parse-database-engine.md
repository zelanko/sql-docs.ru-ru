---
title: "Parse (компонент Database Engine) | Документы Microsoft"
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Parse
- Parse_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Parse [Database Engine]
ms.assetid: b37e28b6-6e2e-470a-945b-ce5252da743a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e80c29d1a13e0b77792ec6d3533d4d80cf355b40
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="parse-database-engine"></a>Parse (компонент Database Engine)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Метод Parse преобразует каноническое представление строки **hierarchyid** для **hierarchyid** значение. Синтаксический анализ вызывается неявно при преобразовании из строкового типа в **hierarchyid** происходит. Действие противоположно из [ToString](../../t-sql/data-types/tostring-database-engine.md). Parse() является статическим методом.
  
## <a name="syntax"></a>Синтаксис  
  
```sql
-- Transact-SQL syntax  
hierarchyid::Parse ( input )  
-- This is functionally equivalent to the following syntax   
-- which implicitly calls Parse():  
CAST ( input AS hierarchyid )  
```  
  
```sql
-- CLR syntax  
static SqlHierarchyId Parse ( SqlString input )   
```  
  
## <a name="arguments"></a>Аргументы  
*входные данные*  
[!INCLUDE[tsql](../../includes/tsql-md.md)]: значение типа данных символа, которые было конвертировано.
  
Среда CLR: Строковое значение, которое оценивается.
  
## <a name="return-types"></a>Типы возвращаемых значений  
**Возвращаемый тип SQL Server: hierarchyid**
  
**Возвращаемый тип CLR: SqlHierarchyId**
  
## <a name="remarks"></a>Замечания  
Если синтаксический анализ получает значение, которое не является допустимым строковым представлением **hierarchyid**, возникает исключение. Например если **char** типы данных содержат конечные пробелы, возникает исключение.
  
## <a name="examples"></a>Примеры  
  
### <a name="a-converting-transact-sql-values-without-a-table"></a>A. Преобразование значений Transact-SQL без таблицы  
Следующий пример кода использует `ToString` для преобразования **hierarchyid** значения в строку и `Parse` преобразовать строковое значение для **hierarchyid**.
  
```sql
DECLARE @StringValue AS nvarchar(4000), @hierarchyidValue AS hierarchyid  
SET @StringValue = '/1/1/3/'  
SET @hierarchyidValue = 0x5ADE  
  
SELECT hierarchyid::Parse(@StringValue) AS hierarchyidRepresentation,  
@hierarchyidValue.ToString() AS StringRepresentation ;
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
hierarchyidRepresentation    StringRepresentation
-------------------------    -----------------------
0x5ADE                       /1/1/3/
```
  
### <a name="b-clr-example"></a>Б. Пример CLR  
В следующем фрагменте кода вызывается метод Parse():
  
```sql
string input = “/1/2/”;  
SqlHierarchyId.Parse(input);  
```  
  
## <a name="see-also"></a>См. также:
[Справочник по методам типа данных hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Иерархические данные (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid (Transact-SQL)](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  
