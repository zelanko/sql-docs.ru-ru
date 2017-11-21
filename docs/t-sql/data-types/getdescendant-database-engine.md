---
title: "GetDescendant (компонент Database Engine) | Документы Microsoft"
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
- GetDescendant_TSQL
- GetDescendant
dev_langs:
- TSQL
helpviewer_keywords:
- GetDescendant [Database Engine]
ms.assetid: f5f39596-033e-4243-acbc-caa188b45b03
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ced4a5518ce7d58785a1d2954c4f131b66a5ddb0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="getdescendant-database-engine"></a>GetDescendant (компонент Database Engine)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает дочерний узел данного родительского узла.
  
## <a name="syntax"></a>Синтаксис  
  
```sql
-- Transact-SQL syntax  
parent.GetDescendant ( child1 , child2 )   
```  
  
```sql
-- CLR syntax  
SqlHierarchyId GetDescendant ( SqlHierarchyId child1 , SqlHierarchyId child2 )   
```  
  
## <a name="arguments"></a>Аргументы  
*child1*  
Значение NULL или **hierarchyid** дочернего элемента текущего узла.
  
*Child2*  
Значение NULL или **hierarchyid** дочернего элемента текущего узла.
  
## <a name="return-types"></a>Типы возвращаемых значений  
**Возвращаемый тип SQL Server: hierarchyid**
  
**Возвращаемый тип CLR: SqlHierarchyId**
  
## <a name="remarks"></a>Замечания  
Возвращает один дочерний узел, который является потомком родителя.
-   Если родительская запись — NULL, метод возвращает значение NULL.  
-   Если родительская запись — не NULL, а потомки child1 и child2 — NULL, метод  возвращает одного потомка данного родителя.  
-   Если родительская запись и потомок child1 — не NULL, а потомок child2 равен NULL, метод  возвращает значение потомка родителя, который больше чем child1.  
-   Если родитель и потомок child2 — не NULL, а потомок child1 равен NULL, метод  возвращает значение потомка родителя, который меньше child2.  
-   Если родитель и дочерние узлы child1 и child2 не равны NULL, метод возвращает дочерний узел родителя, который больше child1 и меньше child2.  
-   Если child1 не равен NULL и не является дочерним узлом родителя, то возникает исключение.  
-   Если child2 не равен NULL и не является дочерним узлом родителя, то возникает исключение.  
-   Если child1 >= child2, то возникает исключение.  
  
GetDescendant является детерминированной. Таким образом Если GetDescendant вызывается с такими же входными, он всегда будет создавать такие же выходные данные. Однако точный идентификатор полученного дочернего элемента может быть различным в зависимости от связей с другими узлами, как показано в примере В.
  
## <a name="examples"></a>Примеры  
  
### <a name="a-inserting-a-row-as-the-least-descendant-node"></a>A. Вставка строки как наименьшего узла-потомка  
Новый сотрудник принят на работу, подотчетный существующему сотруднику в узле `/3/1/`. Выполните следующий код, чтобы вставить новую строку с помощью метода GetDescendant без аргументов, чтобы указать новый узел строк как `/3/1/1/`:
  
```sql
DECLARE @Manager hierarchyid;   
SET @Manager = CAST('/3/1/' AS hierarchyid);  
  
INSERT HumanResources.EmployeeDemo (OrgNode, LoginID, Title, HireDate)  
VALUES  
(@Manager.GetDescendant(NULL, NULL),  
'adventure-works\FirstNewEmployee', 'Application Intern', '3/11/07') ;  
```  
  
### <a name="b-inserting-a-row-as-a-greater-descendant-node"></a>Б. Вставка строки как наибольшего узла-потомка  
Еще один новый сотрудник принят на работу, сообщение о тому же руководителю, как показано в примере а. выполните следующий код, чтобы вставить новую строку с помощью метода GetDescendant, используя аргумент child 1 указывает, что узел новой строки последует за узлом в примере A , становится `/3/1/2/`:
  
```sql
DECLARE @Manager hierarchyid, @Child1 hierarchyid;  
  
SET @Manager = CAST('/3/1/' AS hierarchyid);  
SET @Child1 = CAST('/3/1/1/' AS hierarchyid);  
  
INSERT HumanResources.EmployeeDemo (OrgNode, LoginID, Title, HireDate)  
VALUES  
(@Manager.GetDescendant(@Child1, NULL),  
'adventure-works\SecondNewEmployee', 'Application Intern', '3/11/07') ;  
```  
  
### <a name="c-inserting-a-row-between-two-existing-nodes"></a>В. Вставка строки между двумя существующими узлами  
Третий сотрудник, подотчетный тому же руководителю, как показано в примере а. В этом примере вставляет новую строку в узел больше `FirstNewEmployee` в примере А, и меньше, чем `SecondNewEmployee` в примере б. выполните следующий код, используя метод GetDescendant. Используйте как аргумент child1, так и аргумент child2, чтобы указать, что узел новой строки будет узлом `/3/1/1.1/`:
  
```sql
DECLARE @Manager hierarchyid, @Child1 hierarchyid, @Child2 hierarchyid;  
  
SET @Manager = CAST('/3/1/' AS hierarchyid);  
SET @Child1 = CAST('/3/1/1/' AS hierarchyid);  
SET @Child2 = CAST('/3/1/2/' AS hierarchyid);  
  
INSERT HumanResources.EmployeeDemo (OrgNode, LoginID, Title, HireDate)  
VALUES  
(@Manager.GetDescendant(@Child1, @Child2),  
'adventure-works\ThirdNewEmployee', 'Application Intern', '3/11/07') ;  
  
```  
  
После завершения примеров A, B и C, в узлах, добавленных в таблицу будут одноранговыми со следующими **hierarchyid** значения:
  
`/3/1/1/`
  
`/3/1/1.1/`
  
`/3/1/2/`
  
Узел `/3/1/1.1/` больше узла `/3/1/1/`, но находится на том же уровне иерархии.
  
### <a name="d-scalar-examples"></a>Г. Скалярные примеры  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]поддерживает произвольные вставки и удаления любых **hierarchyid** узлов. С помощью GetDescendant(), можно всегда создать узел между любыми двумя **hierarchyid** узлов. Выполните следующий код, чтобы сформировать образцы узлов с использованием `GetDescendant`:
  
```sql
DECLARE @h hierarchyid = hierarchyid::GetRoot();  
DECLARE @c hierarchyid = @h.GetDescendant(NULL, NULL);  
SELECT @c.ToString();  
DECLARE @c2 hierarchyid = @h.GetDescendant(@c, NULL);  
SELECT @c2.ToString();  
SET @c2 = @h.GetDescendant(@c, @c2);  
SELECT @c2.ToString();  
SET @c = @h.GetDescendant(@c, @c2);  
SELECT @c.ToString();  
SET @c2 = @h.GetDescendant(@c, @c2);  
SELECT @c2.ToString();  
```  
  
### <a name="e-clr-example"></a>Д. Пример CLR  
В следующем фрагменте кода вызывается метод `GetDescendant()`.
  
```sql
SqlHierarchyId parent, child1, child2;  
parent = SqlHierarchyId.GetRoot();  
child1 = parent.GetDescendant(SqlHierarchyId.Null, SqlHierarchyId.Null);  
child2 = parent.GetDescendant(child1, SqlHierarchyId.Null);  
Console.Write(parent.GetDescendant(child1, child2).ToString());  
```  
  
## <a name="see-also"></a>См. также:
[Справочник по методам типа данных hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Иерархические данные (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid (Transact-SQL)](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  

