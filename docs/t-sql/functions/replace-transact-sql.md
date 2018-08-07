---
title: REPLACE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- REPLACE_TSQL
- REPLACE
dev_langs:
- TSQL
helpviewer_keywords:
- first string expression [SQL Server]
- replacing string expression
- third string expressions [SQL Server]
- second string expressions [SQL Server]
- REPLACE function
ms.assetid: 8a7aaaf2-62e3-46c0-8e44-fa22290dd86b
caps.latest.revision: 39
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 3796514d8397b87db38f13951d0ad9432775db0c
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2018
ms.locfileid: "39456618"
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
 *string_expression*  
 Строковое [выражение](../../t-sql/language-elements/expressions-transact-sql.md), в котором выполняется поиск. *string_expression* может быть символьного или двоичного типа данных.  
  
 *string_* pattern  
 Подстрока для поиска. *string_pattern* может быть символьного или двоичного типа данных. *string_pattern* не может быть пустой строкой ('') и не может превышать максимальное число байтов, которое может уместиться на странице.  
  
 *string_* replacement  
 Строка замещения. Аргумент *string_replacement* может содержать символьные или двоичные данные.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Возвращает значение типа **nvarchar**, если один из входных аргументов имеет тип данных **nvarchar**; в противном случае возвращает значение типа **varchar**.  
  
 Возвращает NULL, если какой-либо из аргументов имеет значение NULL.  
  
 Если *string_expression* не относится к типу **varchar(max)** или **nvarchar(max)**, функция REPLACE усекает возвращаемое значение до 8000 байт. Для возврата значений, превышающих 8000 байт, аргумент *string_expression* должен быть явно приведен к типу данных с большими значениями.  
  
## <a name="remarks"></a>Remarks  
 REPLACE производит сравнение, основанное на параметрах сортировки входных данных. Для выполнения сравнения в указанных параметрах сортировки можно воспользоваться функцией [COLLATE](~/t-sql/statements/collations.md), чтобы явно указать параметры сортировки для входных данных.  
  
 Символ 0x0000 (**char(0)**) не определен в параметрах сортировки Windows, и его нельзя включать в REPLACE.  
  
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
 [CONCAT (Transact-SQL)](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS (Transact-SQL)](../../t-sql/functions/concat-ws-transact-sql.md)  
 [FORMATMESSAGE (Transact-SQL)](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME (Transact-SQL)](../../t-sql/functions/quotename-transact-sql.md)  
 [REVERSE (Transact-SQL)](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG (Transact-SQL)](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE (Transact-SQL)](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF (Transact-SQL)](../../t-sql/functions/stuff-transact-sql.md)  
 [TRANSLATE (Transact-SQL)](../../t-sql/functions/translate-transact-sql.md)  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)  
  
