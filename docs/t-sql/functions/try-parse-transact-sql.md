---
description: TRY_PARSE (Transact-SQL)
title: TRY_PARSE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- TRY_PARSE_TSQL
- TRY_PARSE
dev_langs:
- TSQL
helpviewer_keywords:
- TRY_PARSE function
ms.assetid: 292bac1d-edd8-468c-8ff1-8c7de625bc55
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current||>= sql-server-2016||>= sql-server-linux-2017||= sqlallproducts-allversions||=azure-sqldw-latest
ms.openlocfilehash: f6529be493a9f35349b1a4f9b4b0c44fe379c85b
ms.sourcegitcommit: 197a6ffb643f93592edf9e90b04810a18be61133
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2020
ms.locfileid: "91379497"
---
# <a name="try_parse-transact-sql"></a>TRY_PARSE (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa](../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  Возвращает результат выражения, преобразованный в запрошенный тип данных, или значение NULL, если привести тип в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удается. Используйте инструкцию TRY_PARSE только для преобразования данных из строкового типа в типы даты или времени и числовые типы.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
TRY_PARSE ( string_value AS data_type [ USING culture ] )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *string_value*  
 Значение **nvarchar(4000)** , представляющее форматированное значение для преобразования в указанный тип данных.  
  
 *string_value* должно быть допустимым представлением требуемого типа данных, или инструкция TRY_PARSE возвратит значение NULL.  
  
 *data_type*  
 Литерал, представляющий тип данных, запрошенный в качестве результата.  
  
 *culture*  
 Дополнительная строка, идентифицирующая культуру, в которой форматируется *string_value*.  
  
 Если аргумент *culture* не указан, то используется язык текущего сеанса. Язык может быть задан неявно или явно с использованием инструкции SET LANGUAGE. Значение *culture* принимает любую культуру, поддерживаемую .NET Framework; его применение не ограничивается языками, явно поддерживаемыми [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если аргумент *culture* недопустим, то PARSE выдаст ошибку.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Возвращает результат выражения, преобразованный в запрошенный тип данных, или значение NULL, если привести тип не удается.  
  
## <a name="remarks"></a>Комментарии  
 Используйте инструкцию TRY_PARSE только для преобразования данных из строкового типа в типы даты или времени и числовые типы. Для общих преобразований типов данных продолжайте использовать CAST и CONVERT. Следует учитывать, что разбор строкового значения приводит к некоторой потере производительности.  
  
 Для выполнения инструкции TRY_PARSE требуется среда CLR платформы .NET Framework.  
  
 Данная функция не будет работать удаленно, поскольку возможность ее работы зависит от наличия среды CLR. Удаленный вызов функции, требующей наличия среды CLR, приведет к ошибке на удаленном сервере.  
  
 **Дополнительные сведения о параметре data_type**  
  
 Значения параметра *data_type* ограничиваются списком типов, приведенным в следующей таблице, включая стили. Представленные сведения о стилях позволяют определить, какие типы шаблонов разрешены. Дополнительные сведения о стилях см. в документации по платформе .NET Framework для перечислений **System.Globalization.NumberStyles** и **DateTimeStyles**.  
  
|Категория|Тип|Тип .NET|Используемые стили|  
|--------------|----------|---------------|-----------------|  
|Числовой|BIGINT|Int64|NumberStyles.Number|  
|Числовой|INT|Int32|NumberStyles.Number|  
|Числовой|smallint|Int16|NumberStyles.Number|  
|Числовой|tinyint|Byte|NumberStyles.Number|  
|Числовой|Decimal|Decimal|NumberStyles.Number|  
|Числовой|NUMERIC|Decimal|NumberStyles.Number|  
|Числовой|FLOAT|Double|NumberStyles.Float|  
|Числовой|real|Один|NumberStyles.Float|  
|Числовой|smallmoney|Decimal|NumberStyles.Currency|  
|Числовой|money|Decimal|NumberStyles.Currency|  
|Дата и время|Дата|Дата и время|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Дата и время|time|TimeSpan|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Дата и время|DATETIME|Дата и время|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Дата и время|smalldatetime|Дата и время|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Дата и время|datetime2|Дата и время|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
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
|Suomi|Финский|1035|fi-FI|  
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
|русский|русском языке|1049|Ru-RU|  
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
  
### <a name="a-simple-example-of-try_parse"></a>A. Простой пример использования TRY_PARSE  
  
```sql
SELECT TRY_PARSE('Jabberwokkie' AS datetime2 USING 'en-US') AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
NULL  
  
(1 row(s) affected)  
```  
  
### <a name="b-detecting-nulls-with-try_parse"></a>Б. Обнаружение значений NULL с помощью TRY_PARSE  
  
```sql
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
  
### <a name="c-using-iif-with-try_parse-and-implicit-culture-setting"></a>В. Использование функции IIF с TRY_PARSE и неявная установка культуры  
  
```sql
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
  
## <a name="see-also"></a>См. также  
 [PARSE (Transact-SQL)](../../t-sql/functions/parse-transact-sql.md)   
 [Функции преобразования (Transact-SQL)](../../t-sql/functions/conversion-functions-transact-sql.md)   
 [TRY_CONVERT (Transact-SQL)](../../t-sql/functions/try-convert-transact-sql.md)   
 [Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  
