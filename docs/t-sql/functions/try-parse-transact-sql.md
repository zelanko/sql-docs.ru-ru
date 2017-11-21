---
title: "TRY_PARSE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- TRY_PARSE_TSQL
- TRY_PARSE
dev_langs:
- TSQL
helpviewer_keywords:
- TRY_PARSE function
ms.assetid: 292bac1d-edd8-468c-8ff1-8c7de625bc55
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 735d1e38b81a08da50cba340b0e5663d6e6d5755
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="tryparse-transact-sql"></a>TRY_PARSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает результат выражения, преобразованный в запрошенный тип данных, или значение NULL, если привести тип в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удается. Используйте инструкцию TRY_PARSE только для преобразования данных из строкового типа в типы даты или времени и числовые типы.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
TRY_PARSE ( string_value AS data_type [ USING culture ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *string_value*  
 **nvarchar(4000)** значение, представляющее форматированное значение для преобразования в указанный тип данных.  
  
 *string_value* должно быть допустимым представлением требуемого типа данных или TRY_PARSE возвращает значение null.  
  
 *Тип данных*  
 Литерал, представляющий тип данных, запрошенный в качестве результата.  
  
 *язык и региональные параметры*  
 Необязательная строка, идентифицирующая культуру, в котором *string_value* форматируется.  
  
 Если *языка и региональных параметров* аргумент не задан, используется язык текущего сеанса. Язык может быть задан неявно или явно с использованием инструкции SET LANGUAGE. *язык и региональные параметры* принимает любой язык и региональные параметры, поддерживаемые платформой .NET Framework; это не ограничивается языками, поддерживаемыми [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если *языка и региональных параметров* аргумент не является допустимым, инструкция PARSE выдаст ошибку.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Возвращает результат выражения, преобразованный в запрошенный тип данных, или значение NULL, если привести тип не удается.  
  
## <a name="remarks"></a>Замечания  
 Используйте инструкцию TRY_PARSE только для преобразования данных из строкового типа в типы даты или времени и числовые типы. Для общих преобразований типов данных продолжайте использовать CAST и CONVERT. Следует учитывать, что разбор строкового значения приводит к некоторой потере производительности.  
  
 Для выполнения инструкции TRY_PARSE требуется среда CLR платформы .NET Framework.  
  
 Данная функция не будет работать удаленно, поскольку возможность ее работы зависит от наличия среды CLR. Удаленный вызов функции, требующей наличия среды CLR, приведет к ошибке на удаленном сервере.  
  
 **Дополнительные сведения о параметре data_type**  
  
 Значения для *data_type* параметра зависят от типов, приведенных в следующей таблице, включая стили. Представленные сведения о стилях позволяют определить, какие типы шаблонов разрешены. Дополнительные сведения о стилях см. в документации платформы .NET Framework для **System.Globalization.NumberStyles** и **параметра DateTimeStyles** перечисления.  
  
|Категория|Тип|Тип .NET|Используемые стили|  
|--------------|----------|---------------|-----------------|  
|Числовой|bigint|Int64|NumberStyles.Number|  
|Числовой|int|Int32|NumberStyles.Number|  
|Числовой|smallint|Int16|NumberStyles.Number|  
|Числовой|tinyint|Byte|NumberStyles.Number|  
|Числовой|decimal|Decimal|NumberStyles.Number|  
|Числовой|numeric|Decimal|NumberStyles.Number|  
|Числовой|float|Double|NumberStyles.Float|  
|Числовой|real|Один|NumberStyles.Float|  
|Числовой|smallmoney|Decimal|NumberStyles.Currency|  
|Числовой|money|Decimal|NumberStyles.Currency|  
|Дата и время|date|DateTime|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Дата и время|time|TimeSpan|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Дата и время|datetime|DateTime|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Дата и время|smalldatetime|DateTime|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Дата и время|datetime2|DateTime|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Дата и время|datetimeoffset|DateTimeOffset|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
  
 **Дополнительные сведения о параметре культуры**  
  
 В следующей таблице показаны сопоставления между языками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и культурами платформы .NET Framework.  
  
|Полное имя|Псевдоним|LCID|Конкретная культура|  
|---------------|-----------|----------|----------------------|  
|us_english|Английский|1033|ru-RU|  
|Deutsch|Немецкий|1031|de-DE|  
|Français|Французский|1036|fr-FR|  
|日本語|Японский|1041|ja-JP|  
|Dansk|Датский|1030|da-DK|  
|Español|Испанский|3082|es-ES|  
|Italiano|Итальянский|1040|it-IT|  
|Nederlands|Нидерландский|1043|nl-NL|  
|Norsk|Норвежский|2068|nn-NO|  
|Português|Португальский|2070|pt-PT|  
|Suomi|Финский|1035|fi|  
|Svenska|Шведский|1053|sv-SE|  
|čeština|Чешский|1029|Cs-CZ|  
|magyar|Венгерский|1038|Hu-HU|  
|polski|Польский|1045|Pl-PL|  
|română|Румынский|1048|Ro-RO|  
|hrvatski|Хорватский|1050|hr-HR|  
|slovenčina|Словацкий|1051|Sk-SK|  
|slovenski|Словенский|1060|Sl-SI|  
|ελληνικά|Греческий|1032|El-GR|  
|български|Болгарский|1026|bg-BG|  
|русский|Русский|1049|Ru-RU|  
|Türkçe|Турецкий|1055|Tr-TR|  
|British|British English|2057|en-GB|  
|eesti|Эстонский|1061|Et-EE|  
|latviešu|Латышский|1062|lv-LV|  
|lietuvių|Литовский|1063|lt-LT|  
|Português (Brasil)|Бразильский|1046|pt-BR|  
|繁體中文|Китайский (традиционный)|1028|zh-TW|  
|한국어|Корейский|1042|Ko-KR|  
|简体中文|Китайский (упрощенный)|2052|zh-CN|  
|Арабский|Арабский|1025|ar-SA|  
|ไทย|Тайский|1054|Th-TH|  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-simple-example-of-tryparse"></a>A. Простой пример использования TRY_PARSE  
  
```  
SELECT TRY_PARSE('Jabberwokkie' AS datetime2 USING 'en-US') AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
NULL  
  
(1 row(s) affected)  
```  
  
### <a name="b-detecting-nulls-with-tryparse"></a>Б. Обнаружение значений NULL с помощью TRY_PARSE  
  
```  
SELECT  
    CASE WHEN TRY_PARSE('Aragorn' AS decimal USING 'sr-Latn-CS') IS NULL  
        THEN 'True'  
        ELSE 'False'  
END  
AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
True  
  
(1 row(s) affected)  
```  
  
### <a name="c-using-iif-with-tryparse-and-implicit-culture-setting"></a>В. Использование функции IIF с TRY_PARSE и неявная установка культуры  
  
```  
SET LANGUAGE English;  
SELECT IIF(TRY_PARSE('01/01/2011' AS datetime2) IS NULL, 'True', 'False') AS Result;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
False  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:  
 [Синтаксический анализ &#40; Transact-SQL &#41;](../../t-sql/functions/parse-transact-sql.md)   
 [Функции преобразования &#40; Transact-SQL &#41;](../../t-sql/functions/conversion-functions-transact-sql.md)   
 [TRY_CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/try-convert-transact-sql.md)   
 [Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  

