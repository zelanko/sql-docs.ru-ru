---
description: GetLevel (компонент Database Engine)
title: GetLevel (ядро СУБД) | Документы Майкрософт
ms.custom: ''
ms.date: 07/22/2017
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
ms.openlocfilehash: f0aa604a88902dc8bfba522556f11b267fa1e184
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "92037167"
---
# <a name="getlevel-database-engine"></a>GetLevel (компонент Database Engine)

[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Возвращает целое число, представляющее глубину узла *this* в дереве.
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
-- Transact-SQL syntax  
node.GetLevel ( )   
```  
  
```syntaxsql
-- CLR syntax  
SqlInt16 GetLevel ( )   
```  

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Типы возвращаемых данных  
**Возвращаемый тип SQL Server:smallint**
  
**Возвращаемый тип CLR:SqlInt16**
  
## <a name="remarks"></a>Примечания  
Используется, чтобы определить уровень одного или нескольких узлов или сопоставить узлы элементам определенного уровня. Корень иерархии — уровень 0.
  
Метод GetLevel полезен для индексов поиска в ширину. Дополнительные сведения см. в статье [Иерархические данные (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md).
  
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
[Справочник по методам типа данных hierarchyid](./hierarchyid-data-type-method-reference.md)  
[Иерархические данные (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid (Transact-SQL)](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
