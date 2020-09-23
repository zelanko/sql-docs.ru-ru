---
description: Parse (компонент Database Engine)
title: Parse (ядро СУБД) | Документы Майкрософт
ms.custom: ''
ms.date: 07/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Parse
- Parse_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Parse [Database Engine]
ms.assetid: b37e28b6-6e2e-470a-945b-ce5252da743a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0a9650958d90712f659d4adade529049ad4a4775
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91115035"
---
# <a name="parse-database-engine"></a>Parse (компонент Database Engine)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

Метод Parse преобразует каноническое представление строки **hierarchyid** в значение **hierarchyid**. Метод Parse вызывается неявно при преобразовании из строкового типа в **hierarchyid**. Действие противоположно [ToString](../../t-sql/data-types/tostring-database-engine.md). Parse() — это статический метод.
  
## <a name="syntax"></a>Синтаксис  
  
```sql
-- Transact-SQL syntax  
hierarchyid::Parse ( input )  
-- This is functionally equivalent to the following syntax   
-- which implicitly calls Parse():  
CAST ( input AS hierarchyid )  
```  
  
```csharp
-- CLR syntax  
static SqlHierarchyId Parse ( SqlString input )   
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
*input*  
[!INCLUDE[tsql](../../includes/tsql-md.md)]: значение типа данных символа, которые было конвертировано.
  
CLR: оцениваемое значение типа String.
  
## <a name="return-types"></a>Типы возвращаемых данных  
**Возвращаемый тип SQL Server:hierarchyid**
  
**Возвращаемый тип CLR:SqlHierarchyId**
  
## <a name="remarks"></a>Примечания  
Если метод Parse получает значение, которое не является допустимым строковым представлением **hierarchyid**, возникает исключение. Например, если типы данных **char** содержат конечные пробелы, возникает исключение.
  
## <a name="examples"></a>Примеры  
  
### <a name="a-converting-transact-sql-values-without-a-table"></a>A. Преобразование значений Transact-SQL без таблицы  
В приведенном ниже примере кода метод `ToString` преобразует значение **hierarchyid** в строку, а метод `Parse` преобразует строковое значение в **hierarchyid**.
  
```sql
DECLARE @StringValue AS NVARCHAR(4000), @hierarchyidValue AS hierarchyid  
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
  
```csharp
string input = "/1/2/";  
SqlHierarchyId.Parse(input);  
```  
  
## <a name="see-also"></a>См. также раздел
[Справочник по методам типа данных hierarchyid](https://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Иерархические данные (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid (Transact-SQL)](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  
