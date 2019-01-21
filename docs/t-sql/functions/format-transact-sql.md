---
title: FORMAT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- FORMAT_TSQL
- FORMAT
dev_langs:
- TSQL
helpviewer_keywords:
- FORMAT function
ms.assetid: dad6f24c-b8d9-4dbe-a561-9b167b8f20c8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 64341fd261cb1c1e419b925049cf86403a64ab3e
ms.sourcegitcommit: 96032813f6bf1cba680b5e46d82ae1f0f2da3d11
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54299602"
---
# <a name="format-transact-sql"></a>FORMAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

> [!div class="nextstepaction"]
> [Поделитесь своим мнением о содержании документации по SQL.](https://aka.ms/sqldocsurvey)


Возвращает значение, указанное в формате, языке и региональных параметрах (необязательно) в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Для выполнения форматирования значения даты, времени и чисел с учетом локали в виде строк используется функция FORMAT. Для общих преобразований типов данных продолжайте использовать CAST и CONVERT.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
FORMAT ( value, format [, culture ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *value*  
 Выражение поддерживаемого типа данных для форматирования. Список допустимых типов см. в таблице в последующем разделе «Примечания».  
  
 *format*  
 Шаблон формата **nvarchar**.  
  
 Аргумент *format* должен содержать допустимую строку формата .NET Framework в виде стандартной строки формата (например, "C" или "D") либо в виде шаблона пользовательских символов, обозначающих даты и числовые значения (например, "ММММ ДД, гггг (дддд)"). Составное форматирование не поддерживается. Полные сведения об этих шаблонах форматирования приведены в разделах документации по .NET Framework, посвященных форматированию строк в целом, пользовательским форматам даты и времени, а также пользовательским форматам чисел. Хорошей отправной точкой является раздел [Типы форматирования](https://go.microsoft.com/fwlink/?LinkId=211776).  
  
 *culture*  
 Необязательный аргумент **nvarchar**, обозначающий язык и региональные параметры.  
  
 Если аргумент *culture* не указан, то используется язык текущего сеанса. Язык может быть задан неявно или явно с использованием инструкции SET LANGUAGE. В качестве аргумента *culture* принимает любой язык и региональные параметры, поддерживаемые .NET Framework; его применение не ограничивается языками, поддерживаемыми [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если аргумент *culture* недопустим, то FORMAT выдаст ошибку.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **nvarchar** или NULL  
  
 Длина возвращаемого значения определяется аргументом *format*.  
  
## <a name="remarks"></a>Remarks  
 Функция FORMAT возвращает значение NULL для ошибок, когда *culture* не является *valid*. Например, NULL возвращается, если значение, заданное в *format*, недопустимо.  
 
 Функция FORMAT не детерминирована.   
  
 Функция FORMAT предполагает наличие среды выполнения CLR платформы .NET Framework.  
  
 Эта функция не может работать удаленно, так как возможность ее работы зависит от наличия среды CLR. Удаленный вызов функции, требующей наличия среды CLR, может привести к ошибке на удаленном сервере.  
  
 Функция FORMAT использует правила форматирования среды CLR, согласно которым двоеточия и точки должны экранироваться. Поэтому когда строка форматирования (второй параметр) содержит двоеточие или точку, они должны быть экранированы обратной косой чертой, если входное значение (первый параметр) имеет тип данных **time**. См. пример [Г. Использование функции FORMAT с типами данных времени](#ExampleD).  
  
 В приведенной ниже таблице перечислены приемлемые типы данных для аргумента *value*, а также содержатся сведения об их сопоставлении с эквивалентными типами .NET Framework.  
  
|Категория|Тип|Тип .NET|  
|--------------|----------|---------------|  
|Числовой|BIGINT|Int64|  
|Числовой|ssNoversion|Int32|  
|Числовой|smallint|Int16|  
|Числовой|TINYINT|Byte|  
|Числовой|Decimal|SqlDecimal|  
|Числовой|NUMERIC|SqlDecimal|  
|Числовой|FLOAT|Double|  
|Числовой|REAL|Один|  
|Числовой|SMALLMONEY|Decimal|  
|Числовой|money|Decimal|  
|Дата и время|Дата|DateTime|  
|Дата и время|time|TimeSpan|  
|Дата и время|DATETIME|DateTime|  
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
 В следующем примере показано форматирование числовых значений с помощью заданного пользовательского формата. В примере предполагается, что текущая дата — 27 сентября 2012 г. Дополнительные сведения об этих и других пользовательских форматах см. в статье [Пользовательские строки форматирования чисел](https://msdn.microsoft.com/library/0c899ak8.aspx).  
  
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
 В приведенном ниже примере возвращаются 5 строк из таблицы **Sales.CurrencyRate** в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Столбец **EndOfDateRate** в таблице хранится как тип **money**. В этом примере столбец возвращается неформатированным, затем форматируется в формате .NET Number, формате типа General и Currency. Дополнительные сведения об этих и других числовых форматах см. в статье [Стандартные строки форматирования чисел](https://msdn.microsoft.com/library/dwhawy9k.aspx).  
  
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
  
###  <a name="ExampleD"></a> Г. Использование функции FORMAT с типами данных времени  
 В этих случаях функция FORMAT возвращает значение NULL, так как символы `.` и `:` не экранированы.  
  
```sql  
SELECT FORMAT(cast('07:35' as time), N'hh.mm');   --> returns NULL  
SELECT FORMAT(cast('07:35' as time), N'hh:mm');   --> returns NULL  
```  
  
 Функция FORMAT возвращает форматированную строку, так как символы `.` и `:` экранированы.  
  
```sql  
SELECT FORMAT(cast('07:35' as time), N'hh\.mm');  --> returns 07.35  
SELECT FORMAT(cast('07:35' as time), N'hh\:mm');  --> returns 07:35  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
 [STR (Transact-SQL)](../../t-sql/functions/str-transact-sql.md)  
 [Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)   
  
  
