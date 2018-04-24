---
title: CHARINDEX (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b0da42fc1b6a06c0a17f758bf692f065c1e3866c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
Символьное [выражение](../../t-sql/language-elements/expressions-transact-sql.md), содержащее последовательность символов, которую надо найти. Аргумент *expressionToFind* ограничен длиной 8000 символов.
  
*expressionToSearch*  
Символьное выражение, в котором производится поиск.
  
*start_location*  
Выражение тип **integer** или **bigint**, с которого начинается поиск. Если аргумент *start_location* не указан, имеет отрицательное значение или равен нулю, то поиск начинается с начала выражения *expressionToSearch*.
  
## <a name="return-types"></a>Типы возвращаемых данных
**bigint**, если *expressionToSearch* имеет тип данных **varchar(max)**, **nvarchar(max)** или **varbinary(max)**; в противном случае **int**.
  
## <a name="remarks"></a>Remarks  
Если один из аргументов *expressionToFind* или *expressionToSearch* имеет тип данных Юникода (**nvarchar** или **nchar**), а другой аргумент — нет, то другой аргумент преобразовывается в тип данных Юникода. Функция CHARINDEX не поддерживает типы данных **text**, **ntext** и **image**.
  
Если *expressionToFind* или *expressionToSearch* имеет значение NULL, то CHARINDEX возвращает значение NULL.
  
Если аргумент *expressionToFind* не найден в *expressionToSearch*, функция CHARINDEX возвращает 0.
  
Функция CHARINDEX выполняет сравнения на основе параметров сортировки входных данных. Для выполнения сравнения в указанных параметрах сортировки можно воспользоваться функцией COLLATE, чтобы явно указать параметры сортировки для входных данных.
  
Начальная возвращенная позиция начинается с 1, а не с 0.
  
Символ 0x0000 (**char(0)**) не определен в параметрах сортировки Windows, и его нельзя включать в CHARINDEX.
  
## <a name="supplementary-characters-surrogate-pairs"></a>Дополнительные символы (суррогатные пары)  
Если используются параметры сортировки SC, и в *start_location*, и в возвращаемом значении суррогатные пары учитываются как один символ, а не как два. Дополнительные сведения см. в статье [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).
  
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
В приведенном ниже примере используется необязательный параметр *start_location* для поиска `vital` в столбце `DocumentSummary` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)], начиная с пятого символа.
  
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
В приведенном ниже примере показан результирующий набор, если аргумент *expressionToFind* не найден в аргументе *expressionToSearch*.
  
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
В приведенном ниже примере выполняется поиск строки `'TEST'` с учетом регистра в `'This is a Test``'`.
  
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
  
В приведенном ниже примере выполняется поиск строки `'Test'` с учетом регистра в `'This is a Test'`.
  
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
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="f-searching-from-the-start-of-a-string-expression"></a>Е. Поиск с начала строкового выражения  
В приведенном ниже примере возвращается первая позиция строки `is` в `This is a string`, начиная с позиции 1 (первого символа) в строке.
  
```sql
SELECT CHARINDEX('is', 'This is a string');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
---------
3
```  
  
### <a name="g-searching-from-a-position-other-than-the-first-position"></a>Ж. Поиск с позиции, отличной от первой  
В приведенном ниже примере возвращается первая позиция строки `is` в `This is a string`, начиная с четвертой позиции.
  
```sql
SELECT CHARINDEX('is', 'This is a string', 4);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
---------
 6
 ```  
  
### <a name="h-results-when-the-string-is-not-found"></a>З. Результаты в случае, если строка не найдена  
В приведенном ниже примере демонстрируется возвращаемое значение в случае, если значение *string_pattern* не найдено в строке.
  
```sql
SELECT TOP(1) CHARINDEX('at', 'This is a string') FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
---------
0
```  
  
## <a name="see-also"></a>См. также раздел
 [LEN (Transact-SQL)](../../t-sql/functions/len-transact-sql.md)  
 [PATINDEX (Transact-SQL)](../../t-sql/functions/patindex-transact-sql.md)  
 [Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)  
 [+ (объединение строк) (Transact-SQL)](../../t-sql/language-elements/string-concatenation-transact-sql.md)  
 [Поддержка параметров сортировки и Юникода](../../relational-databases/collations/collation-and-unicode-support.md)  
  
  


