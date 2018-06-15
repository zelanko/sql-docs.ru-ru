---
title: ATN2 (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ATN2
- ATN2_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- arctangent
- tangent
- ATN2 function
ms.assetid: 014b291e-7cd7-4c39-b20d-5db3a9f0505d
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 68e1712c19872155a962b2ad4960a65fe29d6cb3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33050931"
---
# <a name="atn2-transact-sql"></a>ATN2 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает угол в радианах между положительным направлением оси X и лучом, проведенным из начала координат в точку (y, x), где x и y — значения двух указанных выражений с плавающей запятой.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
ATN2 ( float_expression , float_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
*float_expression*  
[Выражение](../../t-sql/language-elements/expressions-transact-sql.md) типа данных **float**.
  
## <a name="return-types"></a>Типы возвращаемых данных
**float**
  
## <a name="examples"></a>Примеры  
В следующем примере `ATN2` рассчитывается для указанных компонентов `x` и `y`.
  
```sql
DECLARE @x float = 35.175643, @y float = 129.44;  
SELECT 'The ATN2 of the angle is: ' + CONVERT(varchar, ATN2(@y, @x));  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
The ATN2 of the angle is: 1.30545                         
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также раздел
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Типы данных float и real (Transact-SQL)](../../t-sql/data-types/float-and-real-transact-sql.md)  
[Математические функции (Transact-SQL)](../../t-sql/functions/mathematical-functions-transact-sql.md)
  
  

