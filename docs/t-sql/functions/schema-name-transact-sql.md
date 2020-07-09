---
title: SCHEMA_NAME (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
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
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0b852897e21bdcaaf11ff61240ab84e692dfe326
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86003652"
---
# <a name="schema_name-transact-sql"></a>SCHEMA_NAME (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Возвращает имя схемы, связанное с идентификатором схемы.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SCHEMA_NAME ( [ schema_id ] )  
```  
  
## <a name="arguments"></a>Аргументы  
  
|Термин|Определение|  
|----------|----------------|  
|*schema_id*|Идентификатор схемы. Аргумент *schema_id* имеет тип **int**. Если аргумент *schema_id* не определен, SCHEMA_NAME возвратит имя схемы по умолчанию вызывающей стороны.|  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **sysname**  
  
 Возвращает значение NULL, когда аргумент *schema_id* не является допустимым идентификатором.  
  
## <a name="remarks"></a>Remarks  
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
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)   
 [SCHEMA_ID (Transact-SQL)](../../t-sql/functions/schema-id-transact-sql.md)   
 [sys.schemas (Transact-SQL)](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Функции метаданных (Transact-SQL)](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [WHERE (Transact-SQL)](../../t-sql/queries/where-transact-sql.md)  
  
  

