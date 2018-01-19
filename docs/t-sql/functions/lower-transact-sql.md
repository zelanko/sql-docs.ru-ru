---
title: "НИЖНЯЯ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LOWER
- LOWER_TSQL
dev_langs: TSQL
helpviewer_keywords:
- characters [SQL Server], lowercase
- LOWER function
- uppercase characters [SQL Server]
- characters [SQL Server], uppercase
- lowercase characters
- converting uppercase to lowercase characters
ms.assetid: 1783352b-6852-4658-9d94-51963c59b9bf
caps.latest.revision: "37"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: de6c63278089f6fd871fd826c6b64a2c8991f9e0
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="lower-transact-sql"></a>LOWER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает символьное выражение после преобразования символов нижнего регистра в символы верхнего регистра.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
LOWER ( character_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 — [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) символьных или двоичных данных. *character_expression* может быть константой, переменной или столбцом. *character_expression* должен иметь тип данных, который неявно преобразуется в **varchar**. В противном случае используйте [ПРИВЕДЕНИЯ](../../t-sql/functions/cast-and-convert-transact-sql.md) для явного преобразования *character_expression*.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **varchar** или **nvarchar**  
  
## <a name="examples"></a>Примеры  
 В следующем примере используются функции `LOWER` и `UPPER`, причем функция `UPPER` вложена в функцию `LOWER`, при выборе названий продуктов ценой от 11 до 20 долларов.  
  
```  
-- Uses AdventureWorks  
  
SELECT LOWER(SUBSTRING(EnglishProductName, 1, 20)) AS Lower,   
       UPPER(SUBSTRING(EnglishProductName, 1, 20)) AS Upper,   
       LOWER(UPPER(SUBSTRING(EnglishProductName, 1, 20))) As LowerUpper  
FROM dbo.DimProduct  
WHERE ListPrice between 11.00 and 20.00;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Lower                 Upper                  LowerUpper  
--------------------  ---------------------  --------------------  
minipump              MINIPUMP               minipump  
taillights – battery  TAILLIGHTS – BATTERY   taillights - battery
```  
  
## <a name="see-also"></a>См. также  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
 [ВЕРХНЯЯ &#40; Transact-SQL &#41;](../../t-sql/functions/upper-transact-sql.md)  
  
  

