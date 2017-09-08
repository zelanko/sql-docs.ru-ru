---
title: "Функция PATINDEX (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/19/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PATINDEX
- PATINDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- first occurrence of pattern [SQL Server]
- searches [SQL Server], pattern starting position
- starting position of patten search
- pattern searching [SQL Server]
- PATINDEX function
ms.assetid: c0dfb17f-2230-4e36-98da-a9b630bab656
caps.latest.revision: 53
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: abf357840512c1447f0977a151ca742b148f45d2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="patindex-transact-sql"></a>PATINDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Для любого допустимого символьного или текстового типа данных возвращает начальную позицию первого вхождения шаблона в указанном выражении или нули, если шаблон не найден.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
PATINDEX ( '%pattern%' , expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *шаблон*  
 Символьное выражение, содержащее последовательность символов, которую надо найти. Можно использовать подстановочные знаки; Тем не менее, необходимо следовать после и выполнить знак % *шаблон* (за исключением того, когда производится поиск первых или последних символов). *шаблон* выражение относится к символьному типу данных. *шаблон* ограничен 8000 символов.  
  
 *expression*  
 — [Выражение](../../t-sql/language-elements/expressions-transact-sql.md), обычно столбец, в котором производится поиск по указанному шаблону. *выражение* относится к символьному типу данных.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **bigint** Если *выражение* имеет **varchar(max)** или **nvarchar(max)** типов данных; в противном случае **int**.  
  
## <a name="remarks"></a>Замечания  
 Если параметр *шаблон* или *выражение* имеет значение NULL, функция PATINDEX возвращает NULL.  
  
 Функция PATINDEX выполняет сравнение с учетом параметров сортировки входных значений. Для выполнения сравнения в указанных параметрах сортировки можно воспользоваться функцией COLLATE, чтобы явно указать параметры сортировки для входных данных.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Дополнительные символы (суррогатные пары)  
 При использовании параметров сортировки SC возвращаемое значение рассматривает любые суррогатные пары UTF-16 *выражение* параметра в виде одного символа. Дополнительные сведения см. в статье [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
 0x0000 (**char(0)**) имеет неопределенный символ в параметрах сортировки Windows и его нельзя включать в PATINDEX.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-simple-patindex-example"></a>A. Простой пример PATINDEX  
 В следующем примере проверяется ограниченной последовательности знаков (`interesting data`) для начального расположения символов `ter`.  
  
```  
SELECT PATINDEX('%ter%', 'interesting data');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `3`  
  
### <a name="b-using-a-pattern-with-patindex"></a>Б. Использование шаблона в функции PATINDEX  
 В следующем примере производится поиск позиции, с которой начинается шаблон `ensure` в указанной строке столбца `DocumentSummary` в таблице `Document` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT PATINDEX('%ensure%',DocumentSummary)  
FROM Production.Document  
WHERE DocumentNode = 0x7B40;  
GO   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
-----------  
64  
(1 row(s) affected)
```  
  
 Если не ограничить строки для поиска предложением `WHERE`, запрос возвращает все строки, содержащиеся в таблице, и выдает ненулевые значения для тех строк, в которых найден шаблон, либо нулевые для тех, где он не найден.  
  
### <a name="c-using-wildcard-characters-with-patindex"></a>В. Использование символов-шаблонов в функции PATINDEX  
 В следующих примерах символы-шаблоны % и _ используются для поиска позиции, где в указанной строке (индекс начинается с позиции 1) начинается шаблон `'en'`, за которым следует один любой символ и `'ure'`:  
  
```  
SELECT PATINDEX('%en_ure%', 'please ensure the door is locked');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
-----------  
8  
```  
  
 `PATINDEX` работает аналогично `LIKE`, то есть можно можно использовать любой из этих шаблонов. Нет необходимости заключать шаблон в символы процентов (%). `PATINDEX('a%', 'abc')` возвращает 1 и `PATINDEX('%a', 'cba')` возвращает 3.  
  
 В отличие от `LIKE`, `PATINDEX` возвращает позицию, аналогично `CHARINDEX`.  
  
### <a name="d-using-collate-with-patindex"></a>Г. Использование предложения COLLATE в функции PATINDEX  
 Следующий пример показывает, как функция `COLLATE` явно определяет параметры сортировки при поиске в выражении.  
  
```  
USE tempdb;  
GO  
SELECT PATINDEX ( '%ein%', 'Das ist ein Test'  COLLATE Latin1_General_BIN) ;  
GO  
```  
  
### <a name="e-using-a-variable-to-specify-the-pattern"></a>Д. Использование переменной для указания шаблона  
 В следующем примере используется переменная для передачи значения для *шаблон* параметра. В этом примере используется [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] базы данных.  
  
```  
DECLARE @MyValue varchar(10) = 'safety';   
SELECT PATINDEX('%' + @MyValue + '%', DocumentSummary)   
FROM Production.Document  
WHERE DocumentNode = 0x7B40;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ------------  
 22
 ```  
  

  
## <a name="see-also"></a>См. также:  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)   
 [&#40; Подстановочный знак — символ &#40; s &#41; для соответствия &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
 [&#40; Подстановочный знак — символ &#40; s &#41; Не для соответствия &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)   
 [_ &#40; Шаблон — совпадение одного символа &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)   
 [Символ процента &#40; Подстановочный знак — символ &#40; s &#41; для соответствия &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)  
  
  



