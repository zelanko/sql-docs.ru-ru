---
title: "ФОРМАТ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FORMAT_TSQL
- FORMAT
dev_langs:
- TSQL
helpviewer_keywords:
- FORMAT function
ms.assetid: dad6f24c-b8d9-4dbe-a561-9b167b8f20c8
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 75f944ad28bc56300db7ca9dd7220036faaea711
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="format-transact-sql"></a>FORMAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает значение, указанное в формате, языке и региональных параметрах (необязательно) в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Для выполнения форматирования значения даты, времени и чисел с учетом локали в виде строк используется функция FORMAT. Для общих преобразований типов данных продолжайте использовать CAST и CONVERT.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
FORMAT ( value, format [, culture ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *value*  
 Выражение поддерживаемого типа данных для форматирования. Список допустимых типов см. в таблице в последующем разделе «Примечания».  
  
 *Формат*  
 **nvarchar** шаблон формата.  
  
 *Формат* аргумент должен содержать допустимую строку форматирования .NET Framework, как строка стандартного формата (например, «C» или «D») или в виде шаблона пользовательских символов для дат и числовые значения (например, «мммм дд, гггг (дддд)») . Составное форматирование не поддерживается. Полное описание этих шаблонах форматирования см. в документации .NET Framework по форматированию строк в целом, настраиваемые дата и форматы времени и пользовательские числовые форматы. Хорошей отправной точкой является раздел «[типы форматирования](http://go.microsoft.com/fwlink/?LinkId=211776).»  
  
 *язык и региональные параметры*  
 Необязательный **nvarchar** аргумент, задающий язык и региональные параметры.  
  
 Если *языка и региональных параметров* аргумент не задан, используется язык текущего сеанса. Язык может быть задан неявно или явно с использованием инструкции SET LANGUAGE. *язык и региональные параметры* принимает любой язык и региональные параметры, поддерживаемые .NET Framework в качестве аргумента; это не ограничивается языками, поддерживаемыми [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если *языка и региональных параметров* аргумент не является допустимым, то FORMAT выдаст ошибку.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **nvarchar** или иметь значение null  
  
 Длина возвращаемого значения определяется *формат*.  
  
## <a name="remarks"></a>Замечания  
 ФОРМАТ возвращает значение NULL для ошибки, отличный от *языка и региональных параметров* , не *допустимый*. Например, возвращается значение NULL, если значение, указанное в *формат* является недопустимым.  
 
 Функция FORMAT не детерминирована.   
  
 ФОРМАТ зависит от наличия из .NET Framework Common Language Runtime (CLR).  
  
 Эта функция не может быть удаленной, так как она зависит от наличия среды CLR. Удаленный вызов функции, требуется среда CLR, может привести к ошибке на удаленном сервере.  
  
 ФОРМАТ зависит от среды CLR форматирование правила, которые определяют, что необходимо поставить двоеточие и точка. Таким образом, если строки формата (второй параметр) содержит двоеточие или точка, двоеточие или период необходимо экранировать с обратной косой черты, если входное значение имеет (первый параметр) **время** тип данных. В разделе [г. ФОРМАТ с типами данных времени](#ExampleD).  
  
 В следующей таблице перечислены приемлемые типы данных для *значение* аргумента вместе с эквивалентными типами .NET Framework сопоставления.  
  
|Категория|Тип|Тип .NET|  
|--------------|----------|---------------|  
|Числовой|bigint|Int64|  
|Числовой|int|Int32|  
|Числовой|smallint|Int16|  
|Числовой|tinyint|Byte|  
|Числовой|decimal|SqlDecimal|  
|Числовой|numeric|SqlDecimal|  
|Числовой|float|Double|  
|Числовой|real|Single|  
|Числовой|smallmoney|Decimal|  
|Числовой|money|Decimal|  
|Дата и время|date|DateTime|  
|Дата и время|time|TimeSpan|  
|Дата и время|datetime|DateTime|  
|Дата и время|smalldatetime|DateTime|  
|Дата и время|datetime2|DateTime|  
|Дата и время|datetimeoffset|DateTimeOffset|  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-simple-format-example"></a>A. Простой пример функции FORMAT  
 В следующем примере возвращается простой набор данных, отформатированный для различных языков и региональных параметров.  
  
```sql  
DECLARE @d DATETIME = '10/01/2011';  
SELECT FORMAT ( @d, 'd', 'en-US' ) AS 'US English Result'  
      ,FORMAT ( @d, 'd', 'en-gb' ) AS 'Great Britain English Result'  
      ,FORMAT ( @d, 'd', 'de-de' ) AS 'German Result'  
      ,FORMAT ( @d, 'd', 'zh-cn' ) AS 'Simplified Chinese (PRC) Result';   
  
SELECT FORMAT ( @d, 'D', 'en-US' ) AS 'US English Result'  
      ,FORMAT ( @d, 'D', 'en-gb' ) AS 'Great Britain English Result'  
      ,FORMAT ( @d, 'D', 'de-de' ) AS 'German Result'  
      ,FORMAT ( @d, 'D', 'zh-cn' ) AS 'Chinese (Simplified PRC) Result';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
US English Result Great Britain English Result  German Result Simplified Chinese (PRC) Result  
----------------  ----------------------------- ------------- -------------------------------------  
10/1/2011         01/10/2011                    01.10.2011    2011/10/1  
  
(1 row(s) affected)  
  
US English Result            Great Britain English Result  German Result                    Chinese (Simplified PRC) Result  
---------------------------- ----------------------------- -----------------------------  ---------------------------------------  
Saturday, October 01, 2011   01 October 2011               Samstag, 1. Oktober 2011        2011年10月1日  
  
(1 row(s) affected)  
```  
  
### <a name="b-format-with-custom-formatting-strings"></a>Б. Функция FORMAT с пользовательскими строками форматирования  
 В следующем примере показано форматирование числовых значений с помощью заданного пользовательского формата. В примере предполагается, что текущая дата — 27 сентября 2012 г. Дополнительные сведения об этих и других пользовательских форматов см. в разделе [строки настраиваемых числовых форматов](http://msdn.microsoft.com/library/0c899ak8.aspx).  
  
```sql  
DECLARE @d DATETIME = GETDATE();  
SELECT FORMAT( @d, 'dd/MM/yyyy', 'en-US' ) AS 'DateTime Result'  
       ,FORMAT(123456789,'###-##-####') AS 'Custom Number Result';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
DateTime Result  Custom Number Result  
--------------   --------------------  
27/09/2012       123-45-6789  
  
(1 row(s) affected)  
```  
  
### <a name="c-format-with-numeric-types"></a>В. Функция FORMAT с числовыми типами  
 В следующем примере возвращается 5 строк из **Sales.CurrencyRate** в таблицу [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] базы данных. Столбец **EndOfDateRate** хранится как тип **деньги** в таблице. В этом примере столбец возвращается неформатированным, затем форматируется в формате .NET Number, формате типа General и Currency. Дополнительные сведения об этих и других численных форматах см. в разделе [строки стандартного числового формата](http://msdn.microsoft.com/library/dwhawy9k.aspx).  
  
```sql  
SELECT TOP(5)CurrencyRateID, EndOfDayRate  
            ,FORMAT(EndOfDayRate, 'N', 'en-us') AS 'Number Format'  
            ,FORMAT(EndOfDayRate, 'G', 'en-us') AS 'General Format'  
            ,FORMAT(EndOfDayRate, 'C', 'en-us') AS 'Currency Format'  
FROM Sales.CurrencyRate  
ORDER BY CurrencyRateID;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
CurrencyRateID EndOfDayRate  Numeric Format  General Format  Currency Format  
-------------- ------------  --------------  --------------  ---------------  
1              1.0002        1.00            1.0002          $1.00  
2              1.55          1.55            1.5500          $1.55  
3              1.9419        1.94            1.9419          $1.94  
4              1.4683        1.47            1.4683          $1.47  
5              8.2784        8.28            8.2784          $8.28  
  
(5 row(s) affected)  
  
```  
  
 Этот пример задает немецкий язык и региональные параметры (de-de).  
  
```sql  
SELECT TOP(5)CurrencyRateID, EndOfDayRate  
      ,FORMAT(EndOfDayRate, 'N', 'de-de') AS 'Numeric Format'  
      ,FORMAT(EndOfDayRate, 'G', 'de-de') AS 'General Format'  
      ,FORMAT(EndOfDayRate, 'C', 'de-de') AS 'Currency Format'  
FROM Sales.CurrencyRate  
ORDER BY CurrencyRateID;  
```  
  
```  
CurrencyRateID EndOfDayRate  Numeric Format  General Format  Currency Format  
-------------- ------------  --------------  --------------  ---------------  
1              1.0002        1,00            1,0002          1,00 €  
2              1.55          1,55            1,5500          1,55 €  
3              1.9419        1,94            1,9419          1,94 €  
4              1.4683        1,47            1,4683          1,47 €  
5              8.2784        8,28            8,2784          8,28 €  
  
 (5 row(s) affected)  
```  
  
###  <a name="ExampleD"></a> Г. Функция FORMAT с типами данных времени  
 FORMAT возвращает значение NULL в этих случаях, поскольку `.` и `:` без escape-символа.  
  
```sql  
SELECT FORMAT(cast('07:35' as time), N'hh.mm');   --> returns NULL  
SELECT FORMAT(cast('07:35' as time), N'hh:mm');   --> returns NULL  
```  
  
 Возвращает формат форматированную строку, так как `.` и `:` исключаются.  
  
```sql  
SELECT FORMAT(cast('07:35' as time), N'hh\.mm');  --> returns 07.35  
SELECT FORMAT(cast('07:35' as time), N'hh\:mm');  --> returns 07:35  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  

