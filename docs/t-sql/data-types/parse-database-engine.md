---
title: "Parse (компонент Database Engine) | Документы Microsoft"
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 027940c7575f3c7901cd8668879064ff375d9986
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="parse-database-engine"></a>Parse (компонент Database Engine)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

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
  
  

