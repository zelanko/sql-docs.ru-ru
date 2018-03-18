---
title: "DATALENGTH (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 07/29/2017
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
- DATALENGTH_TSQL
- DATALENGTH
dev_langs:
- TSQL
helpviewer_keywords:
- number of bytes representing expression
- data types [SQL Server], length
- DATALENGTH function
- expressions [SQL Server], length
- lengths [SQL Server], data
ms.assetid: 00f377f1-cc3e-4eac-be47-b3e3f80267c9
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 9d9b60d82ad4a711ed7cf67a015491b6ebafa264
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="datalength-transact-sql"></a>DATALENGTH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает число байтов, использованных для представления выражения.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DATALENGTH ( expression )   
```  
  
## <a name="arguments"></a>Аргументы  
*expression*  
[Выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого типа данных.
  
## <a name="return-types"></a>Типы возвращаемых данных
**bigint**, если *expression* имеет тип данных **varchar(max)**, **nvarchar(max)** или **varbinary(max)**; в противном случае **int**.
  
## <a name="remarks"></a>Remarks  
Функция DATALENGTH особенно полезна при работе с данными типов **varchar**, **varbinary**, **text**, **image**, **nvarchar** и **ntext**, потому что они могут хранить данные переменной длины.
  
Функция DATALENGTH возвращает NULL, если аргументом является NULL.
  
> [!NOTE]  
>  Уровни совместимости могут повлиять на возвращаемые значения. Дополнительные сведения об уровнях совместимости см. в разделе [Уровень совместимости ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="examples"></a>Примеры  
В следующем примере находится длина столбца `Name` в таблице `Product`.
  
```sql
-- Uses AdventureWorks  
  
SELECT length = DATALENGTH(EnglishProductName), EnglishProductName  
FROM dbo.DimProduct  
ORDER BY EnglishProductName;  
GO  
```  
  
## <a name="see-also"></a>См. также раздел
[LEN (Transact-SQL)](../../t-sql/functions/len-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-for-transact-sql.md)
  
  

