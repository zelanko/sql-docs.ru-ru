---
title: GetLevel (ядро СУБД) | Документы Майкрософт
ms.custom: ''
ms.date: 7/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- GetLevel
- GetLevel_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GetLevel [Database Engine]
ms.assetid: 81577d7e-8ff6-4e73-b7f4-94c03d4921e7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 381a1afb5b63ae04e49636a02e890b7ac3e5e112
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51698532"
---
# <a name="getlevel-database-engine"></a>GetLevel (компонент Database Engine)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает целое число, представляющее глубину узла *this* в дереве.
  
## <a name="syntax"></a>Синтаксис  
  
```sql
-- Transact-SQL syntax  
node.GetLevel ( )   
```  
  
```sql
-- CLR syntax  
SqlInt16 GetLevel ( )   
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
**Возвращаемый тип SQL Server:smallint**
  
**Возвращаемый тип CLR:SqlInt16**
  
## <a name="remarks"></a>Remarks  
Используется, чтобы определить уровень одного или нескольких узлов или сопоставить узлы элементам определенного уровня. Корень иерархии — уровень 0.
  
Метод GetLevel очень полезен для индексов поиска преимущественно в ширину. Дополнительные сведения см. в статье [Иерархические данные (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md).
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-hierarchy-level-as-a-column"></a>A. Возвращение уровня иерархии как столбца  
В приведенном ниже примере возвращается текстовое представление **hierarchyid**, а затем уровень иерархии возвращается как столбец **EmpLevel** для всех строк в таблице.
  
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
  
## <a name="see-also"></a>См. также раздел
[Справочник по методам типа данных hierarchyid](https://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Иерархические данные (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid (Transact-SQL)](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  
