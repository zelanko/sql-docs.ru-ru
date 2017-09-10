---
title: "GetLevel (компонент Database Engine) | Документы Microsoft"
ms.custom: 
ms.date: 07/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GetLevel
- GetLevel_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GetLevel [Database Engine]
ms.assetid: 81577d7e-8ff6-4e73-b7f4-94c03d4921e7
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aac401d8fbe9546404f44f5fa2455f9e9c5dfe9d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="getlevel-database-engine"></a>GetLevel (компонент Database Engine)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает целое число, представляющее глубину узла *это* в дереве.
  
## <a name="syntax"></a>Синтаксис  
  
```sql
-- Transact-SQL syntax  
node.GetLevel ( )   
```  
  
```sql
-- CLR syntax  
SqlInt16 GetLevel ( )   
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
**Возвращаемый тип SQL Server: smallint**
  
**Возвращаемый тип CLR: SqlInt16**
  
## <a name="remarks"></a>Замечания  
Используется, чтобы определить уровень одного или нескольких узлов или сопоставить узлы элементам определенного уровня. Корень иерархии — уровень 0.
  
GetLevel очень полезен для индексов поиска преимущественно. Дополнительные сведения см. в разделе [иерархических данных &#40; SQL Server &#41; ](../../relational-databases/hierarchical-data-sql-server.md).
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-hierarchy-level-as-a-column"></a>A. Возвращение уровня иерархии как столбца  
В следующем примере возвращается текстовое представление **hierarchyid**, а затем уровень иерархии как **EmpLevel** столбец для всех строк в таблице:
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode,   
OrgNode.GetLevel() AS EmpLevel, *  
FROM HumanResources.EmployeeDemo;  
```  
  
### <a name="b-returning-all-members-of-a-hierarchy-level"></a>Б. Возвращение всех элементов уровня иерархии  
В следующем примере возвращаются все строки в таблице на уровне иерархии 2.
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode,   
OrgNode.GetLevel() AS EmpLevel, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetLevel() = 2;  
```  
  
### <a name="c-returning-the-root-of-the-hierarchy"></a>В. Возвращение корневого элемента иерархии  
В следующем примере возвращается корневой уровень иерархии.
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode,   
OrgNode.GetLevel() AS EmpLevel, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetLevel() = 0;  
```  
  
### <a name="d-clr-example"></a>Г. Пример CLR  
В следующем фрагменте кода вызывается метод GetLevel():
  
```sql
this.GetLevel()  
```  
  
## <a name="see-also"></a>См. также:
[Справочник по методам типа данных hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Иерархические данные (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid (Transact-SQL)](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  

