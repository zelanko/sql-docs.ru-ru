---
title: "GetAncestor (ядро СУБД) | Документы Майкрософт"
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
- GetAncestor_TSQL
- GetAncestor
dev_langs:
- TSQL
helpviewer_keywords:
- GetAncestor [Database Engine]
ms.assetid: b96a986f-d5e4-4034-8013-de7974594ee9
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b232238dccf5c22918a8805cdc9cd876dfef5723
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="getancestor-database-engine"></a>GetAncestor (компонент Database Engine)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает идентификатор **hierarchyid**, представляющий *n*-й предок *this*.
  
## <a name="syntax"></a>Синтаксис  
  
```sql
-- Transact-SQL syntax  
child.GetAncestor ( n )   
```  
  
```sql
-- CLR syntax  
SqlHierarchyId GetAncestor ( int n )  
```  
  
## <a name="arguments"></a>Аргументы  
*n*  
Значение типа **int**, представляющее число уровней для перемещения вверх по иерархии.
  
## <a name="return-types"></a>Типы возвращаемых данных
**Возвращаемый тип SQL Server:hierarchyid**
  
**Возвращаемый тип CLR:SqlHierarchyId**
  
## <a name="remarks"></a>Remarks  
Используется, чтобы проверить, является ли текущий узел предком для каждого из узлов в выходных данных на указанном уровне.
  
Если передается число больше значения [GetLevel()](../../t-sql/data-types/getlevel-database-engine.md), возвращается значение NULL.
  
При передаче отрицательного числа возникает исключение.
  
## <a name="examples"></a>Примеры  
  
### <a name="a-finding-the-child-nodes-of-a-parent"></a>A. Нахождение дочерних узлов родительского узла  
Функция `GetAncestor(1)` возвращает имена сотрудников, для которых элемент `david0` является непосредственным предком (родительским элементом). В следующем примере используется функция `GetAncestor(1)`.
  
```sql
DECLARE @CurrentEmployee hierarchyid  
SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\david0'  
  
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetAncestor(1) = @CurrentEmployee ;  
```  
  
### <a name="b-returning-the-grandchildren-of-a-parent"></a>Б. Возвращение внучатых узлов родительского узла  
Функция `GetAncestor(2)` возвращает имена сотрудников, расположенные двумя уровнями ниже текущего узла в иерархии. Эти элементы являются внучатыми для текущего узла. В следующем примере используется функция `GetAncestor(2)`.
  
```sql
DECLARE @CurrentEmployee hierarchyid  
SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\ken0'  
  
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetAncestor(2) = @CurrentEmployee ;  
```  
  
### <a name="c-returning-the-current-row"></a>В. Возвращение текущей строки  
Чтобы вернуть текущий узел с помощью функции `GetAncestor(0)`, выполните приведенный ниже код.
  
```sql
DECLARE @CurrentEmployee hierarchyid  
SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\david0'  
  
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetAncestor(0) = @CurrentEmployee ;  
```  
  
### <a name="d-returning-a-hierarchy-level-if-a-table-is-not-present"></a>Г. Возвращение уровня иерархии в случае отсутствия таблицы  
Функция `GetAncestor` возвращает выбранный уровень в иерархии даже в случае отсутствия таблицы. Например, следующим фрагментом кода назначается текущий сотрудник и возвращается идентификатор `hierarchyid` предка текущего сотрудника без обращения к таблице.
  
```sql
DECLARE @CurrentEmployee hierarchyid ;  
DECLARE @TargetEmployee hierarchyid ;  
SELECT @CurrentEmployee = '/2/3/1.2/5/3/' ;  
SELECT @TargetEmployee = @CurrentEmployee.GetAncestor(2) ;  
SELECT @TargetEmployee.ToString(), @TargetEmployee ;  
```  
  
### <a name="e-calling-a-common-language-runtime-method"></a>Д. Вызов метода CLR  
В следующем фрагменте кода вызывается метод `GetAncestor()`.
  
```sql
this.GetAncestor(1)  
```  
  
## <a name="see-also"></a>См. также раздел
[IsDescendantOf (ядро СУБД)](../../t-sql/data-types/isdescendantof-database-engine.md)  
[Справочник по методам типа данных hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Иерархические данные (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid (Transact-SQL)](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  
