---
title: "Schema_name (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SCHEMA_NAME
- SCHEMA_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SCHEMA_NAME function
- schemas [SQL Server], names
ms.assetid: 20071b77-2b6e-4ce7-a8e3-fa71480baf73
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: bbc8d08ff59f85544fe3f11712c6780431bc76d7
ms.contentlocale: ru-ru
ms.lasthandoff: 10/17/2017

---
# <a name="schemaname-transact-sql"></a>SCHEMA_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает имя схемы, связанное с идентификатором схемы.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SCHEMA_NAME ( [ schema_id ] )  
```  
  
## <a name="arguments"></a>Аргументы  
  
|Термин|Определение|  
|----------|----------------|  
|*SCHEMA_ID*|Идентификатор схемы. *SCHEMA_ID* — **int**. Если *schema_id* — не определен, SCHEMA_NAME возвратит имя принимаемой по умолчанию схемы вызывающей стороны.|  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **sysname**  
  
 Возвращает значение NULL, если *schema_id* не является допустимым идентификатором.  
  
## <a name="remarks"></a>Замечания  
 SCHEMA_NAME возвращает имена системных схем и пользовательских схем. SCHEMA_NAME можно вызывать в списке выбора, в предложении WHERE и в любом месте, где разрешается выражение.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-name-of-the-default-schema-of-the-caller"></a>A. Возвращение имени принимаемой по умолчанию схемы вызывающей стороны  
  
```  
SELECT SCHEMA_NAME();  
```  
  
### <a name="b-returning-the-name-of-a-schema-by-using-an-id"></a>Б. Возвращение имени схемы с помощью идентификатора  
  
```  
SELECT SCHEMA_NAME(1);  
```  
  
## <a name="see-also"></a>См. также:  
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [SCHEMA_ID &#40; Transact-SQL &#41;](../../t-sql/functions/schema-id-transact-sql.md)   
 [sys.schemas &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Функции метаданных &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [ГДЕ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  


