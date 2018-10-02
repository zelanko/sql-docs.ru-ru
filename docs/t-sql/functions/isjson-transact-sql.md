---
title: TOP (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: douglasl
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
ms.openlocfilehash: 6ef62fa601bfef0c2e99e6f1f1e40747a34e1b5a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47857332"
---
# <a name="isjson-transact-sql"></a>ISJSON (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

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
  
  
