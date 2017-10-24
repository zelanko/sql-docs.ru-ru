---
title: "CONCAT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 046278bb3016b39df8039a1450a58b177d2bc180
ms.contentlocale: ru-ru
ms.lasthandoff: 10/17/2017

---
# <a name="concat-transact-sql"></a>CONCAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Возвращает строку, являющуюся результатом объединения двух или более строковых значений. (Для добавления отделение значения во время объединения, в разделе [CONCAT_WS](../../t-sql/functions/concat-ws-transact-sql.md).)
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
CONCAT ( string_value1, string_value2 [, string_valueN ] )  
```  
  
## <a name="arguments"></a>Аргументы  
*string_value*  
Строковое значение для объединения с другими значениями.
  
## <a name="return-types"></a>Возвращаемые типы
Строка, длина и тип которой зависят от входных данных.
  
## <a name="remarks"></a>Замечания  
**CONCAT** принимает переменное количество строковых аргументов и объединяет их в одну строку. Для этого требуется не менее двух входных значений. В противном случае возникает ошибка. Все аргументы неявно преобразуются в строковые типы и затем объединяются. Значения NULL неявно преобразуются в пустую строку. Если все аргументы имеют значение null, возвращается пустая строка типа **varchar**(1) возвращается. Неявное преобразование в строки выполняется по существующим правилам преобразования типов данных. Дополнительные сведения о преобразованиях типов данных см. в разделе [CAST и CONVERT &#40; Transact-SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md).
  
Тип возвращаемого значения зависит от типа аргументов. Описанные выше основные понятия проиллюстрированы в следующей таблице.
  
|Входной тип|Выходной тип и длина|  
|---|---|
|Если какой-либо аргумент имеет системный тип SQL-CLR, тип SQL-CLR UDT или `nvarchar(max)`|**nvarchar(max)**|  
|В противном случае, если любой из аргументов **varbinary(max)** или **varchar(max)**|**varchar(max)** Если один из параметров не **nvarchar** любой длины. Если Да, то результатом является **nvarchar(max)**.|  
|В противном случае, если любой из аргументов **nvarchar**(< = 4000)|**nvarchar**(< = 4000)|  
|Во всех остальных случаях|**varchar**(< = 8000), если только один из параметров не является nvarchar любой длины. Если Да, то результатом является **nvarchar(max)**.|  
  
Если аргументы являются < = 4000 для **nvarchar**, или < = 8000 для **varchar**, неявное преобразование может повлиять на длину результата. Другие типы данных имеют разные длины, когда они неявно преобразуются в строки. Например **int** (14) имеет длину строки 12, а **float** имеет длину 32. Таким образом, после объединения двух целых чисел формируется строка длиной не менее 24.
  
Если ни один из входных аргументов не принадлежит к поддерживаемому типу большого объекта (LOB), то длина возвращаемого типа усекается до 8000, независимо от того, какой это тип. Это усечение позволяет сохранить пространство и обеспечить эффективность формирования плана.
  
CONCAT, функция может выполняться удаленно на связанном сервере, которая является версией [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий. Для более старых связанных серверов операция CONCAT будет выполняться локально после со связанного сервера возвращаются значения не объединяются.
  
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
  
## <a name="see-also"></a>См. также:
[Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)  
[CONCAT_WS (Transact-SQL)](../../t-sql/functions/concat-ws-transact-sql.md)   
  



