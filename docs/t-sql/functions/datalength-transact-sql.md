---
title: "DATALENGTH (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: d8887c50cb482e27bce63e08aa18b8ca54616faa
ms.contentlocale: ru-ru
ms.lasthandoff: 10/17/2017

---
# <a name="datalength-transact-sql"></a>DATALENGTH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает число байтов, использованных для представления выражения.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DATALENGTH ( expression )   
```  
  
## <a name="arguments"></a>Аргументы  
*expression*  
— [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого типа данных.
  
## <a name="return-types"></a>Возвращаемые типы
**bigint** Если *выражение* имеет **varchar(max)**, **nvarchar(max)** или **varbinary(max)** типов данных; в противном случае **int**.
  
## <a name="remarks"></a>Замечания  
DATALENGTH особенно полезна для **varchar**, **varbinary**, **текст**, **изображения**, **nvarchar**, и **ntext** типы данных, так как эти типы данных можно хранить данные переменной длины.
  
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
  
## <a name="see-also"></a>См. также:
[Функция LEN &#40; Transact-SQL &#41;](../../t-sql/functions/len-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[Системные функции &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)
  
  


