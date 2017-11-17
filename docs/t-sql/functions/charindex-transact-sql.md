---
title: "Функция CHARINDEX (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
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
- CHARINDEX
- CHARINDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- expressions [SQL Server], pattern searching
- CHARINDEX function
- pattern searching [SQL Server]
- starting point of expression in character string
ms.assetid: 78c10341-8373-4b30-b404-3db20e1a3ac4
caps.latest.revision: 52
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 80c1228faeaaa4012afc0fd27992a2f5cf389f6e
ms.openlocfilehash: 5467f9d98562fac8262e537887d03c1d68b25d88
ms.contentlocale: ru-ru
ms.lasthandoff: 10/12/2017

---
# <a name="charindex-transact-sql"></a>CHARINDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Ищет в выражении другое выражение и возвращает его начальную позицию, если оно найдено.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
CHARINDEX ( expressionToFind , expressionToSearch [ , start_location ] )   
```  
  
## <a name="arguments"></a>Аргументы  
*expressionToFind*  
Символом [выражение](../../t-sql/language-elements/expressions-transact-sql.md) , содержащее последовательность искомых. *expressionToFind* не должна превышать 8000 символов.
  
*выражения expressionToSearch*  
Символьное выражение, в котором производится поиск.
  
*start_location*  
— **Целое** или **bigint** выражение, с которой начинается поиск. Если *start_location* не указан, имеет отрицательное значение или равен 0, то поиск начинается в начале *выражения expressionToSearch*.
  
## <a name="return-types"></a>Возвращаемые типы
**bigint** Если *выражения expressionToSearch* имеет **varchar(max)**, **nvarchar(max)**, или **varbinary(max)** данных типы; в противном случае **int**.
  
## <a name="remarks"></a>Замечания  
Если параметр *expressionToFind* или *выражения expressionToSearch* имеет тип данных Юникода (**nvarchar** или **nchar**), а другой — нет, другие преобразуется в тип данных Юникода. Функция CHARINDEX не может использоваться с **текст**, **ntext**, и **изображение** типов данных.
  
Если параметр *expressionToFind* или *выражения expressionToSearch* имеет значение NULL, функция CHARINDEX возвращает NULL.
  
Если *expressionToFind* не найдено в *выражения expressionToSearch*, функция CHARINDEX возвращает 0.
  
Функция CHARINDEX выполняет сравнения на основе параметров сортировки входных данных. Для выполнения сравнения в указанных параметрах сортировки можно воспользоваться функцией COLLATE, чтобы явно указать параметры сортировки для входных данных.
  
Начальная возвращенная позиция начинается с 1, а не с 0.
  
0x0000 (**char(0)**) имеет неопределенный символ в параметрах сортировки Windows и его нельзя включать в CHARINDEX.
  
## <a name="supplementary-characters-surrogate-pairs"></a>Дополнительные символы (суррогатные пары)  
При использовании параметров сортировки SC, оба *start_location* и возвращаемое значение суррогатные пары как один символ, а не как два. Дополнительные сведения см. в статье [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-starting-position-of-an-expression"></a>A. Возвращение начальной позиции выражения  
В следующем примере возвращается позиция, с которой начинается последовательность символов `bicycle` в столбце `DocumentSummary` таблицы `Document` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].
  
```sql
DECLARE @document varchar(64);  
SELECT @document = 'Reflectors are vital safety' +  
                   ' components of your bicycle.';  
SELECT CHARINDEX('bicycle', @document);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
-----------   
48            
```  
  
### <a name="b-searching-from-a-specific-position"></a>Б. Поиск с конкретной позиции  
В следующем примере используется необязательный *start_location* параметр, чтобы начать поиск `vital` пятого символа `DocumentSummary` столбца в [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] базы данных.
  
```sql
DECLARE @document varchar(64);  
  
SELECT @document = 'Reflectors are vital safety' +  
                   ' components of your bicycle.';  
SELECT CHARINDEX('vital', @document, 5);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
-----------   
16            
  
(1 row(s) affected)  
```  
  
### <a name="c-searching-for-a-nonexistent-expression"></a>В. Поиск несуществующего выражения  
В следующем примере показан результирующий набор, если свойство *expressionToFind* не найдено в *выражения expressionToSearch*.
  
```sql
DECLARE @document varchar(64);  
  
SELECT @document = 'Reflectors are vital safety' +  
                   ' components of your bicycle.';  
SELECT CHARINDEX('bike', @document);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
0
  
(1 row(s) affected)
```
  
### <a name="d-performing-a-case-sensitive-search"></a>Г. Выполнение поиска с учетом регистра  
В следующем примере выполняется поиск с учетом регистра для строки `'TEST'` в `'This is a Test``'`.
  
```sql
USE tempdb;  
GO  
--perform a case sensitive search  
SELECT CHARINDEX ( 'TEST',  
       'This is a Test'  
       COLLATE Latin1_General_CS_AS);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
0
```  
  
В следующем примере выполняется поиск с учетом регистра для строки `'Test'` в `'This is a Test'`.
  
```sql
  
USE tempdb;  
GO  
SELECT CHARINDEX ( 'Test',  
       'This is a Test'  
       COLLATE Latin1_General_CS_AS);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
13
```  
  
### <a name="e-performing-a-case-insensitive-search"></a>Д. Выполнение поиска без учета регистра  
В следующем примере выполняется поиск строки `'TEST'` в `'This is a Test'` без учета регистра.
  
```sql
  
USE tempdb;  
GO  
SELECT CHARINDEX ( 'TEST',  
       'This is a Test'  
       COLLATE Latin1_General_CI_AS);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
13
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="f-searching-from-the-start-of-a-string-expression"></a>Е. Поиск с начала указанного строкового выражения  
В следующем примере возвращается первый расположение `is` строка в `This is a string`, начиная с позиции 1 (первого символа) в строке.
  
```sql
SELECT CHARINDEX('is', 'This is a string');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
---------
3
```  
  
### <a name="g-searching-from-a-position-other-than-the-first-position"></a>Ж. Поиск с позиции, отличной от первой  
В следующем примере возвращается первый расположение `is` строка в `This is a string`, начиная с четвертого позиции.
  
```sql
SELECT CHARINDEX('is', 'This is a string', 4);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
---------
 6
 ```  
  
### <a name="h-results-when-the-string-is-not-found"></a>З. Результаты, если строка не найдена  
В следующем примере показан возвращаемое значение, если свойство *string_pattern* не найден в строке.
  
```sql
SELECT TOP(1) CHARINDEX('at', 'This is a string') FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
---------
0
```  
  
## <a name="see-also"></a>См. также:
[Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
[+ &#40; Объединение строк &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/string-concatenation-transact-sql.md)  
[Поддержка параметров сортировки и Юникода](../../relational-databases/collations/collation-and-unicode-support.md)
  
  



