---
title: "DROP EXTERNAL TABLE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 02a6a236-0756-4570-abfa-6f677a7df042
caps.latest.revision: "12"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e29508550528b1f98318bec26676707c72f0b5fc
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="drop-external-table-transact-sql"></a>DROP EXTERNAL TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Удаляет из внешней таблицы PolyBase. Это не приводит к удалению внешних данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DROP EXTERNAL TABLE [ database_name . [schema_name ] . | schema_name . ] table_name   
[;]  
```  
  

## <a name="arguments"></a>Аргументы  
 [ *database_name* . [*schema_name*] . | *schema_name* . ] *table_name*  
 Имя внешней таблицы для удаления одной - трех частей. При необходимости может включать имя таблицы, схемы или базы данных и схемы.  
  
## <a name="permissions"></a>Разрешения  
  
-   Требуется **ALTER** разрешения на схему, которой принадлежит таблица.  
  
## <a name="general-remarks"></a>Общие замечания  
 При удалении внешней таблицы удаляются все метаданные, относящиеся к таблице. Он не удаляет внешних данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-basic-syntax"></a>A. С помощью базовый синтаксис  
  
```  
DROP EXTERNAL TABLE SalesPerson;  
DROP EXTERNAL TABLE dbo.SalesPerson;  
DROP EXTERNAL TABLE EasternDivision.dbo.SalesPerson;  
```  
  
### <a name="b-dropping-an-external-table-from-the-current-database"></a>Б. Удаление внешней таблицы из текущей базы данных  
 В следующем примере удаляется `ProductVendor1` таблицы, данные, индексы и все зависимые представления из текущей базы данных.  
  
```  
DROP EXTERNAL TABLE ProductVendor1;  
```  
  
### <a name="c-dropping-a-table-from-another-database"></a>В. Удаление таблицы из другой базы данных  
 Следующий пример удаляет таблицу `SalesPerson` из базы данных `EasternDivision`.  
  
```  
DROP EXTERNAL TABLE EasternDivision.dbo.SalesPerson;  
```  
  
## <a name="see-also"></a>См. также  
 [CREATE EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/create-external-table-transact-sql.md)  
  
  

