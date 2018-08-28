---
title: ASCII (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ASCII_TSQL
- ASCII
dev_langs:
- TSQL
helpviewer_keywords:
- ASCII function
- characters [SQL Server], ASCII
- code [SQL Server], ASCII
- leftmost character of expression
ms.assetid: 45c2044a-0593-4805-8bae-0fad4bde2e6b
caps.latest.revision: 37
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4add8a1a63572e6e86d659c29ea29d172545b9e0
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43076179"
---
# <a name="ascii-transact-sql"></a>ASCII (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает код ASCII первого символа указанного символьного выражения.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
ASCII ( character_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
*character_expression*  
[Выражение ](../../t-sql/language-elements/expressions-transact-sql.md) типа **char** или **varchar**.
  
## <a name="return-types"></a>Типы возвращаемых данных
 **int**  
  
## <a name="remarks"></a>Remarks
ASCII — это аббревиатура от **A**merican **S**tandard **C**ode for **I**nformation **I**nterchange (американский стандартный код для обмена информацией). Это стандарт кодировки символов для современных компьютеров. Список символов ASCII см. в разделе **Печатаемые символы** спецификации [ASCII](https://www.wikipedia.org/wiki/ASCII).

## <a name="examples"></a>Примеры  
В этом примере принимается кодировка ASCII и возвращается значение `ASCII` для 6 символов.
  
```sql
SELECT ASCII('A') AS A, ASCII('B') AS B,   
ASCII('a') AS a, ASCII('b') AS b,  
ASCII(1) AS [1], ASCII(2) AS [2];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
A           B           a           b           1           2  
----------- ----------- ----------- ----------- ----------- -----------  
65          66          97          98          49          50  
```  
  
## <a name="see-also"></a>См. также раздел
 [CHAR (Transact-SQL)](../../t-sql/functions/char-transact-sql.md)  
 [NCHAR (Transact-SQL)](../../t-sql/functions/nchar-transact-sql.md)  
 [UNICODE (Transact-SQL)](../../t-sql/functions/unicode-transact-sql.md)  
 [Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)
  
  


