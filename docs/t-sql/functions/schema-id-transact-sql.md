---
title: "SCHEMA_ID (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SCHEMA_ID
- SCHEMA_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- identification numbers [SQL Server], schemas
- schemas [SQL Server], IDs
- SCHEMA_ID function
- IDs [SQL Server], schemas
- default schema IDs
ms.assetid: c8e34df5-3eea-459f-ae40-050909ce9fda
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 6034b43145cf81c23359149b07f3b6caaffcc352
ms.contentlocale: ru-ru
ms.lasthandoff: 10/17/2017

---
# <a name="schemaid-transact-sql"></a>SCHEMA_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает идентификатор схемы, связанный с именем схемы.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SCHEMA_ID ( [ schema_name ] )   
```  
  
## <a name="arguments"></a>Аргументы  
  
|Термин|Определение|  
|----------|----------------|  
|*schema_name*|Имя схемы. *schema_name* — **sysname**. Если *schema_name* не задан, SCHEMA_ID возвращает идентификатор схемы по умолчанию вызывающего объекта.|  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **int**  
  
 Будет возвращено значение NULL, если *schema_name* не является допустимой схемой.  
  
## <a name="remarks"></a>Замечания  
 SCHEMA_ID возвращает идентификаторы системных и пользовательских схем. Функцию SCHEMA_ID можно вызывать в списке выбора, в предложении WHERE и в любом месте, где разрешается выражение.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-default-schema-id-of-a-caller"></a>A. Возвращение идентификатора схемы по умолчанию вызывающего объекта  
  
```  
SELECT SCHEMA_ID();  
```  
  
### <a name="b-returning-the-schema-id-of-a-named-schema"></a>Б. Возвращение идентификатора именованной схемы  
  
```  
SELECT SCHEMA_ID('dbo');  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции метаданных &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [Schema_name &#40; Transact-SQL &#41;](../../t-sql/functions/schema-name-transact-sql.md)   
 [sys.schemas &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md)  
  
  


