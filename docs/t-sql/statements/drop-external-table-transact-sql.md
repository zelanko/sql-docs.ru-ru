---
description: DROP EXTERNAL TABLE (Transact-SQL)
title: DROP EXTERNAL TABLE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 02a6a236-0756-4570-abfa-6f677a7df042
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 75ad3c1c1de4d12a1efa2267c63a2f22e5f2cb2e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88415630"
---
# <a name="drop-external-table-transact-sql"></a>DROP EXTERNAL TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Удаляет из базы данных внешнюю таблицу PolyBase, но не удаляет внешние данные.  
  
 ![Значок ссылки на статью](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на статью") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
DROP EXTERNAL TABLE { database_name.schema_name.table_name | schema_name.table_name | table_name }
[;]  
```  
  

## <a name="arguments"></a>Аргументы  
 `[ database_name . [schema_name] . | schema_name . ] table_name`  
 Состоящее из не более трех частей имя внешней таблицы для удаления. При необходимости имя таблицы может включать схему или базу данных и схему.  
  
## <a name="permissions"></a>Разрешения  
  
-   Требуется разрешение **ALTER** на схему, которой принадлежит таблица.  
  
## <a name="general-remarks"></a>Общие замечания  
 При удалении внешней таблицы удаляются все метаданные, относящиеся к таблице. Это не приводит к удалению внешних данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-basic-syntax"></a>A. Использование основного синтаксиса  
  
```sql  
DROP EXTERNAL TABLE SalesPerson;  
DROP EXTERNAL TABLE dbo.SalesPerson;  
DROP EXTERNAL TABLE EasternDivision.dbo.SalesPerson;  
```  
  
### <a name="b-dropping-an-external-table-from-the-current-database"></a>Б. Удаление внешней таблицы из текущей базы данных  
 В следующем примере из текущей базы данных удаляется таблица `ProductVendor1`, ее данные, индексы и зависимые представления.  
  
```sql  
DROP EXTERNAL TABLE ProductVendor1;  
```  
  
### <a name="c-dropping-a-table-from-another-database"></a>В. Удаление таблицы из другой базы данных  
 Следующий пример удаляет таблицу `SalesPerson` из базы данных `EasternDivision`.  
  
```sql  
DROP EXTERNAL TABLE EasternDivision.dbo.SalesPerson;  
```  
  
## <a name="see-also"></a>См. также  
 [CREATE EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/create-external-table-transact-sql.md)  
  
