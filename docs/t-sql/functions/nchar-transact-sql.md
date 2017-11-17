---
title: "NCHAR (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
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
- nchar
- nchar_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- NCHAR function
- Unicode [SQL Server], NCHAR function
ms.assetid: 68cefc68-7c4f-4326-80c1-300f90cf19db
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: b70c591517177ad9febd1d0d9873a41192bf9414
ms.contentlocale: ru-ru
ms.lasthandoff: 10/17/2017

---
# <a name="nchar-transact-sql"></a>NCHAR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает символ Юникода с указанным целочисленным кодом, определенным в стандарте Юникода.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
NCHAR ( integer_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *integer_expression*  
 Если параметры сортировки базы данных не содержат флаг дополнительных символов (SC), то используются положительные целые числа от 0 до 65 535 (от 0 до 0xFFFF). При указании значения вне этого диапазона возвращается значение NULL. Дополнительные сведения о дополнительных символах см. в разделе [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
 Если параметры сортировки базы данных не поддерживают флаг дополнительных символов (SC), то используются положительные целые числа от 0 до 1 114 111 (от 0 до 0x10FFFF). При указании значения вне этого диапазона возвращается значение NULL.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **nchar(1)** когда параметры сортировки базы данных по умолчанию не поддерживает дополнительные символы.  
  
 **nvarchar(2)** Если параметры сортировки базы данных по умолчанию поддерживает дополнительные символы.  
  
 Если параметр *integer_expression* лежит в диапазоне 0 – 0xFFFF, возвращается только один знак. Для больших значений NCHAR возвращает соответствующую суррогатную пару. Не создавайте суррогатные пары с применением `NCHAR(<High surrogate>) + NCHAR(\<Low Surrogate>)`. Вместо этого используйте параметры сортировки базы данных, которые поддерживают дополнительные символы, с указанием кодовой точки в Юникоде для суррогатной пары. В следующем примере рассматривается как старый метод конструирования суррогатной пары, так и предпочтительный метод с указанием кодовой точки в Юникоде.  
  
```  
CREATE DATABASE test COLLATE Finnish_Swedish_100_CS_AS_SC;  
DECLARE @d nvarchar(10) = N'ࣅ炙   
-– Old style method.  
SELECT NCHAR(0xD84C) + NCHAR(0xDD7F);   
  
-- Preferred method.   
SELECT NCHAR(143743);   
  
-- Alternative preferred method.  
SELECT NCHAR(UNICODE(@d));    
```  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-nchar-and-unicode"></a>A. Использование функций NCHAR и UNICODE  
 В следующем примере функции `UNICODE` и `NCHAR` используются для вывода значения `UNICODE` и `NCHAR` (символ Юникода) второго символа строки `København` и вывода второго фактического символа `ø`.  
  
```  
DECLARE @nstring nchar(8);  
SET @nstring = N'København';  
SELECT UNICODE(SUBSTRING(@nstring, 2, 1)),   
   NCHAR(UNICODE(SUBSTRING(@nstring, 2, 1)));  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------- -   
248         ø  
(1 row(s) affected)  
```  
  
### <a name="b-using-substring-unicode-convert-and-nchar"></a>Б. Использование функций SUBSTRING, UNICODE, CONVERT и NCHAR  
 В следующем пример функции `SUBSTRING`, `UNICODE`, `CONVERT` и `NCHAR` используются для печати номера символа, символа Юникода и значения Юникода каждого символа в строке `København`.  
  
```  
-- The @position variable holds the position of the character currently  
-- being processed. The @nstring variable is the Unicode character   
-- string to process.  
DECLARE @position int, @nstring nchar(9);  
-- Initialize the current position variable to the first character in   
-- the string.  
SET @position = 1;  
-- Initialize the character string variable to the string to process.  
-- Notice that there is an N before the start of the string. This   
-- indicates that the data following the N is Unicode data.  
SET @nstring = N'København';  
-- Print the character number of the position of the string you are at,   
-- the actual Unicode character you are processing, and the UNICODE   
-- value for this particular character.  
PRINT 'Character #' + ' ' + 'Unicode Character' + ' ' + 'UNICODE Value';  
WHILE @position <= DATALENGTH(@nstring)  
   BEGIN  
   SELECT @position,   
      NCHAR(UNICODE(SUBSTRING(@nstring, @position, 1))),  
      CONVERT(NCHAR(17), SUBSTRING(@nstring, @position, 1)),  
      UNICODE(SUBSTRING(@nstring, @position, 1))  
   SELECT @position = @position + 1  
   END;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Character # Unicode Character UNICODE Value  
  
----------- ---- ----------------- -----------   
1           K    K                 75  
  
(1 row(s) affected)  
  
----------- ---- ----------------- -----------   
2           ø    ø                 248  
  
(1 row(s) affected)  
  
----------- ---- ----------------- -----------   
3           b    b                 98  
  
(1 row(s) affected)  
  
----------- ---- ----------------- -----------   
4           e    e                 101  
  
(1 row(s) affected)  
  
----------- ---- ----------------- -----------   
5           n    n                 110  
  
(1 row(s) affected)  
  
----------- ---- ----------------- -----------   
6           h    h                 104  
  
(1 row(s) affected)  
  
----------- ---- ----------------- -----------   
7           a    a                 97  
  
(1 row(s) affected)  
  
----------- ---- ----------------- -----------   
8           v    v                 118  
  
(1 row(s) affected)  
  
----------- ---- ----------------- -----------   
9           n    n                 110  
  
(1 row(s) affected)  
  
----------- ---- ----------------- -----------   
10          NULL                   NULL  
  
(1 row(s) affected)  
  
----------- ---- ----------------- -----------   
11          NULL                   NULL  
  
(1 row(s) affected)  
  
----------- ---- ----------------- -----------   
12          NULL                   NULL  
  
(1 row(s) affected)  
  
----------- ---- ----------------- -----------   
13          NULL                   NULL  
  
(1 row(s) affected)  
  
----------- ---- ----------------- -----------   
14          NULL                   NULL  
  
(1 row(s) affected)  
  
----------- ---- ----------------- -----------   
15          NULL                   NULL  
  
(1 row(s) affected)  
  
----------- ---- ----------------- -----------   
16          NULL                   NULL  
  
(1 row(s) affected)  
  
----------- ---- ----------------- -----------   
17          NULL                   NULL  
  
(1 row(s) affected)  
  
----------- ---- ----------------- -----------   
18          NULL                   NULL  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)   
 [Юникод &#40; Transact-SQL &#41;](../../t-sql/functions/unicode-transact-sql.md)  
  
  


