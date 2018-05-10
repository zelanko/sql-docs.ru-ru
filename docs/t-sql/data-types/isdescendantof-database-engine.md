---
title: IsDescendantOf (ядро СУБД) | Документы Майкрософт
ms.custom: ''
ms.date: 7/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|data-types
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- IsDescendant_TSQL
- IsDescendant
dev_langs:
- TSQL
helpviewer_keywords:
- IsDescendantOf [Database Engine]
ms.assetid: edc80444-b697-410f-9419-0f63c9b5618d
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 679f75007cc60521f569a42a5c580f8553b61eca
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="isdescendantof-database-engine"></a>IsDescendantOf (компонент Database Engine)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает значение true, если *this* является потомком родительского элемента.
  
## <a name="syntax"></a>Синтаксис  
  
```sql
-- Transact-SQL syntax  
child. IsDescendantOf ( parent )  
```  
  
```sql
-- CLR syntax  
SqlHierarchyId IsDescendantOf (SqlHierarchyId parent )  
```  
  
## <a name="arguments"></a>Аргументы  
*parent*  
Узел **hierarchyid**, для которого следует выполнить проверку IsDescendantOf.
  
## <a name="return-types"></a>Типы возвращаемых данных  
**Возвращаемый тип SQL Server:bit**
  
**Возвращаемый тип CLR:SqlBoolean**
  
## <a name="remarks"></a>Remarks  
Возвращает значение true для всех узлов поддерева, корнем для которых является родительский элемент, и значение false для всех остальных узлов.
  
Родительский элемент считается своим собственным потомком.
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-isdescendantof-in-a-where-clause"></a>A. Использование функции IsDescendantOf в предложении WHERE  
В следующем примере возвращается имя руководителя и имена подотчетных ему сотрудников:
  
```sql
DECLARE @Manager hierarchyid  
SELECT @Manager = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\dylan0'  
  
SELECT * FROM HumanResources.EmployeeDemo  
WHERE OrgNode.IsDescendantOf(@Manager) = 1  
```  
  
### <a name="b-using-isdescendantof-to-evaluate-a-relationship"></a>Б. Использование функции IsDescendantOf для оценки связи  
В следующем фрагменте кода объявляются и заполняются три переменные. Затем оценивается иерархическая связь и возвращается один из двух печатаемых результатов на основе сравнения:
  
```sql
DECLARE @Manager hierarchyid, @Employee hierarchyid, @LoginID nvarchar(256)  
SELECT @Manager = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\terri0' ;  
  
SELECT @Employee = OrgNode, @LoginID = LoginID FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\rob0'  
  
IF @Employee.IsDescendantOf(@Manager) = 1  
   BEGIN  
    PRINT 'LoginID ' + @LoginID + ' is a subordinate of the selected Manager.'  
   END  
ELSE  
   BEGIN  
    PRINT 'LoginID ' + @LoginID + ' is not a subordinate of the selected Manager.' ;  
   END  
```  
  
### <a name="c-calling-a-common-language-runtime-method"></a>В. Вызов метода CLR  
В следующем фрагменте кода вызывается метод `IsDescendantOf()`.
  
```sql
this.IsDescendantOf(Parent)  
```  
  
## <a name="see-also"></a>См. также раздел
[Справочник по методам типа данных hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Иерархические данные (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid (Transact-SQL)](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  
