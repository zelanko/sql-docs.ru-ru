---
title: GetAncestor (ядро СУБД) | Документы Майкрософт
ms.custom: ''
ms.date: 7/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- GetAncestor_TSQL
- GetAncestor
dev_langs:
- TSQL
helpviewer_keywords:
- GetAncestor [Database Engine]
ms.assetid: b96a986f-d5e4-4034-8013-de7974594ee9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 085dac6c67b6039c30268daae26c5cac5f5d4f01
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47830532"
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
  
  
