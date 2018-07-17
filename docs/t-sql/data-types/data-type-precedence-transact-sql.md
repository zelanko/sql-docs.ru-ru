---
title: Приоритет типов данных (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 7/23/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- precedence [SQL Server]
- data types [SQL Server], converting
- data types [SQL Server], precedence
- converting data types [SQL Server], precedence
- precedence [SQL Server], data types
ms.assetid: f4c804ab-ed3f-43b1-a024-c9ac6944b66b
caps.latest.revision: 21
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 14ed88abd883a06a3cc8c76c54460b552ea0bc68
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37416633"
---
# <a name="data-type-precedence-transact-sql"></a>Приоритет типов данных (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

Если оператор связывает два выражения различных типов данных, то по правилам приоритета типов данных определяется, какой тип данных имеет меньший приоритет и будет преобразован в тип данных с большим приоритетом. Если неявное преобразование не поддерживается, возвращается ошибка. Если оба операнда выражения имеют одинаковый тип данных, результат операции будет иметь тот же тип данных.
  
В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется следующий приоритет типов данных:
  
1.  определяемые пользователем типы данных (высший приоритет);  
1.  **sql_variant**  
1.  **xml**  
1.  **datetimeoffset**  
1.  **datetime2**  
1.  **datetime**  
1.  **smalldatetime**  
1.  **date**  
1. **time**  
1. **float**  
1. **real**  
1. **decimal**  
1. **money**  
1. **smallmoney**  
1. **bigint**  
1. **int**  
1. **smallint**  
1. **tinyint**  
1. **bit**  
1. **ntext**  
1. **text**  
1. **image**  
1. **timestamp**  
1. **uniqueidentifier**  
1. **nvarchar** (включая **nvarchar(max)** )  
1. **nchar**  
1. **varchar** (включая **varchar(max)** )  
1. **char**  
1. **varbinary** (включая **varbinary(max)** )  
1. **binary** (низший приоритет)  
  
## <a name="see-also"></a>См. также раздел
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  
