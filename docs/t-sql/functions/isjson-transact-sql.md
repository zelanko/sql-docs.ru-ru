---
title: TOP (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: genemi
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ISJSON
- ISJSON_TSQL
helpviewer_keywords:
- ISJSON function
- JSON, validating
ms.assetid: c836f3d3-3e17-44ae-92bf-f341918896c3
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
monikerRange: = azuresqldb-current||= azure-sqldw-latest||>= sql-server-2016||>= sql-server-linux-2017||= sqlallproducts-allversions
ms.openlocfilehash: 9b98e7250f6cea54401ba533c769ab2be0bc82cf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65577570"
---
# <a name="isjson-transact-sql"></a>ISJSON (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Проверяет, что строка содержит допустимые данные JSON.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
ISJSON ( expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Строка для проверки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает 1, если строка содержит допустимые данные JSON; в противном случае возвращает 0. Возвращает значение NULL, если *выражение* имеет значение NULL.  
  
 Не возвращает ошибок.  
  
## <a name="remarks"></a>Remarks  
 **ISJSON** не проверяет уникальность ключей на том же уровне.  
  
## <a name="examples"></a>Примеры  
  
### <a name="example-1"></a>Пример 1  
В следующем примере выполняется условный блок операторов, если значение параметра `@param` содержит допустимый код JSON.  
  
```sql  
DECLARE @param <data type>
SET @param = <value>

IF (ISJSON(@param) > 0)  
BEGIN  
     -- Do something with the valid JSON value of @param.  
END
 
```  
  
### <a name="example-2"></a>Пример 2  
В следующем примере возвращаются строки, в которых столбец `json_col` содержит допустимые данные JSON.  
  
```sql  
SELECT id, json_col
FROM tab1
WHERE ISJSON(json_col) > 0 
```  
  
## <a name="see-also"></a>См. также:  
 [Данные JSON (SQL Server)](../../relational-databases/json/json-data-sql-server.md)  
  
  
