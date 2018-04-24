---
title: CONCAT (Transact-SQL) | Документы Майкрософт
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
- CONCAT
- CONCAT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CONCAT function
ms.assetid: fce5a8d4-283b-4c47-95e5-4946402550d5
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 71f52ba08f2fd5fe94af4b16dbcac06746564e09
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="concat-transact-sql"></a>CONCAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Возвращает строку, являющуюся результатом объединения двух или более строковых значений. (Сведения о добавлении разделяющего значения во время объединения см. в описании функции [CONCAT_WS](../../t-sql/functions/concat-ws-transact-sql.md).)
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
CONCAT ( string_value1, string_value2 [, string_valueN ] )  
```  
  
## <a name="arguments"></a>Аргументы  
*string_value*  
Строковое значение для объединения с другими значениями.
  
## <a name="return-types"></a>Типы возвращаемых данных
Строка, длина и тип которой зависят от входных данных.
  
## <a name="remarks"></a>Remarks  
**CONCAT** принимает переменное количество строковых аргументов и объединяет их в одну строку. Для этого требуется не менее двух входных значений. В противном случае возникает ошибка. Все аргументы неявно преобразуются в строковые типы и затем объединяются. Значения NULL неявно преобразуются в пустую строку. Если все аргументы имеют значение NULL, то возвращается пустая строка типа **varchar**(1). Неявное преобразование в строки выполняется по существующим правилам преобразования типов данных. Дополнительные сведения о преобразовании типов данных см. в статье [Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md).
  
Тип возвращаемого значения зависит от типа аргументов. Описанные выше основные понятия проиллюстрированы в следующей таблице.
  
|Входной тип|Выходной тип и длина|  
|---|---|
|Если какой-либо аргумент имеет системный тип SQL-CLR, тип SQL-CLR UDT или `nvarchar(max)`|**nvarchar(max)**|  
|В противном случае, если какой-либо аргумент имеет тип **varbinary(max)** или **varchar(max)**|**varchar(max)**, если только один из параметров не представляет собой значение **nvarchar** любой длины. Если это так, то результат имеет тип **nvarchar(max)**.|  
|В противном случае, если какой либо из аргументов имеет значение **nvarchar**(<= 4000)|**nvarchar**(<= 4000)|  
|Во всех остальных случаях|**varchar**(<= 8000), если только один из параметров не представляет собой значение nvarchar любой длины. Если это так, то результат имеет тип **nvarchar(max)**.|  
  
Когда аргументы имеют значение <= 4000 для **nvarchar** или <= 8000 для **varchar**, неявное преобразование может повлиять на длину результата. Другие типы данных имеют разные длины, когда они неявно преобразуются в строки. Например, значение **int** (14) имеет длину строки 12, а длина значения **float** составляет 32. Таким образом, после объединения двух целых чисел формируется строка длиной не менее 24.
  
Если ни один из входных аргументов не принадлежит к поддерживаемому типу большого объекта (LOB), то длина возвращаемого типа усекается до 8000, независимо от того, какой это тип. Это усечение позволяет сохранить пространство и обеспечить эффективность формирования плана.
  
Функция CONCAT может выполняться удаленно на связанном сервере версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] или более поздней. Если связанный сервер имеет более раннюю версию, операция CONCAT выполняется локально после возврата не сцепленных значений со связанного сервера.
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-concat"></a>A. Использование CONCAT  
  
```sql
SELECT CONCAT ( 'Happy ', 'Birthday ', 11, '/', '25' ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
-------------------------  
Happy Birthday 11/25  
  
(1 row(s) affected)  
```  
  
### <a name="b-using-concat-with-null-values"></a>Б. Использование CONCAT со значениями NULL  
  
```sql
CREATE TABLE #temp (  
    emp_name nvarchar(200) NOT NULL,  
    emp_middlename nvarchar(200) NULL,  
    emp_lastname nvarchar(200) NOT NULL  
);  
INSERT INTO #temp VALUES( 'Name', NULL, 'Lastname' );  
SELECT CONCAT( emp_name, emp_middlename, emp_lastname ) AS Result  
FROM #temp;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
------------------  
NameLastname  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также раздел
 [CONCAT_WS (Transact-SQL)](../../t-sql/functions/concat-ws-transact-sql.md)   
 [FORMATMESSAGE (Transact-SQL)](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME (Transact-SQL)](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE (Transact-SQL)](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE (Transact-SQL)](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG (Transact-SQL)](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE (Transact-SQL)](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF (Transact-SQL)](../../t-sql/functions/stuff-transact-sql.md)  
 [TRANSLATE (Transact-SQL)](../../t-sql/functions/translate-transact-sql.md)  
 [Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)  
  


