---
description: GetRoot (компонент Database Engine)
title: GetRoot (ядро СУБД) | Документы Майкрософт
ms.custom: ''
ms.date: 07/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- GetRoot
- GetRoot_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GetRoot [Database Engine]
ms.assetid: 240b70f1-eeda-44ab-b4bb-9e4af80fa7c0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5db6206cd555705ec5b167dc023f585293f45bf8
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91111236"
---
# <a name="getroot-database-engine"></a>GetRoot (компонент Database Engine)

[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Возвращает корневой элемент дерева иерархии. GetRoot() — статический метод.
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
-- Transact-SQL syntax  
hierarchyid::GetRoot ( )   
```  
  
```syntaxsql
-- CLR syntax  
static SqlHierarchyId GetRoot ( )   
```  

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Типы возвращаемых данных  
**Возвращаемый тип SQL Server:hierarchyid**
  
**Возвращаемый тип CLR:SqlHierarchyId**
  
## <a name="remarks"></a>Примечания  
Используется для определения корневого узла в иерархическом дереве.
  
## <a name="examples"></a>Примеры  
  
### <a name="a-transact-sql-example"></a>A. Пример (Transact-SQL)  
В следующем примере возвращается корневой узел иерархического дерева.
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode = hierarchyid::GetRoot()  
```  
  
### <a name="b-clr-example"></a>Б. Пример CLR  
В следующем фрагменте кода вызывается метод GetRoot():
  
```sql
SqlHierarchyId.GetRoot()  
```  
  
## <a name="see-also"></a>См. также раздел
[Справочник по методам типа данных hierarchyid](https://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Иерархические данные (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid (Transact-SQL)](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  
