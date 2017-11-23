---
title: "REPLACE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/23/2017
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
- REPLACE_TSQL
- REPLACE
dev_langs: TSQL
helpviewer_keywords:
- first string expression [SQL Server]
- replacing string expression
- third string expressions [SQL Server]
- second string expressions [SQL Server]
- REPLACE function
ms.assetid: 8a7aaaf2-62e3-46c0-8e44-fa22290dd86b
caps.latest.revision: "39"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: a50c0b7220eba654df21349e2fd3cd57b9a0d7d3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="replace-transact-sql"></a>REPLACE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Заменяет все вхождения указанного строкового значения другим строковым значением.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
REPLACE ( string_expression , string_pattern , string_replacement )  
```  
  
## <a name="arguments"></a>Аргументы  
 *String_Expression*  
 Строка, [выражение](../../t-sql/language-elements/expressions-transact-sql.md) для поиска. *String_Expression* может иметь тип символьные или двоичные данные.  
  
 *string_*шаблон  
 Подстрока для поиска. *string_pattern* может иметь тип символьные или двоичные данные. *string_pattern* не может быть пустой строкой ("«) и не должна превышать максимальное число байт, помещается на странице.  
  
 *string_*замены  
 Строка замещения. *string_replacement* может иметь тип символьные или двоичные данные.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Возвращает **nvarchar** Если один из входных аргументов имеет **nvarchar** данных типа; в противном случае ЗАМЕНИТЕ возвращает **varchar**.  
  
 Возвращает NULL, если какой-либо из аргументов имеет значение NULL.  
  
 Если *string_expression* не относится к типу **varchar(max)** или **nvarchar(max) ЗАМЕНЫ** усекает возвращаемое значение до 8000 байт. Для возврата значений, превышающих 8 000 байт *string_expression* должен быть явно приведен к типу данных большого объема.  
  
## <a name="remarks"></a>Замечания  
 REPLACE производит сравнение, основанное на параметрах сортировки входных данных. Для выполнения сравнения в указанных параметрах сортировки можно использовать [COLLATE](~/t-sql/statements/collations.md) чтобы явные параметры сортировки для входных данных.  
  
 0x0000 (**char(0)**) имеет неопределенный символ в параметрах сортировки Windows и не может включать в REPLACE.  
  
## <a name="examples"></a>Примеры  
 На следующем примере показано, как строка `cde` в строке `abcdefghi` заменяется на `xxx`.  
  
```sql  
SELECT REPLACE('abcdefghicde','cde','xxx');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
------------  
abxxxfghixxx  
(1 row(s) affected)  
```  
  
 Следующий пример иллюстрирует использование функции `COLLATE`.  
  
```sql  
SELECT REPLACE('This is a Test'  COLLATE Latin1_General_BIN,  
'Test', 'desk' );  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
------------  
This is a desk  
(1 row(s) affected)  
```  

  
## <a name="see-also"></a>См. также:  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
