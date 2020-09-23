---
title: Константы (драйверы Майкрософт для PHP для SQL Server)
description: Сведения о константах, определенных в драйверах Microsoft SQLSRV и PDO_SQLSRV для PHP для SQL Server.
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- constants
ms.assetid: 9727c944-b645-48d6-9012-18dbde35ee3c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 771a14e8705af72f57571503c2dba9012c2e9879
ms.sourcegitcommit: 129f8574eba201eb6ade1f1620c6b80dfe63b331
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2020
ms.locfileid: "87435253"
---
# <a name="constants-microsoft-drivers-for-php-for-sql-server"></a>Константы (драйверы Майкрософт для PHP для SQL Server)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Эта статья описывает константы, которые определены [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="pdo_sqlsrv-driver-constants"></a>Константы драйвера PDO_SQLSRV  
Константы, перечисленные на [веб-сайте PDO](https://php.net/manual/book.pdo.php), допустимы в [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
Ниже описаны константы, характерные для продуктов Майкрософт, в драйвере PDO_SQLSRV.  
  
### <a name="transaction-isolation-level-constants"></a>Константы уровня изоляции транзакции  
Ключ **TransactionIsolation** , который используется с [PDO::__construct](../../connect/php/pdo-construct.md), принимает одну из следующих констант:  
  
-   PDO::SQLSRV_TXN_READ_UNCOMMITTED  
  
-   PDO::SQLSRV_TXN_READ_COMMITTED  
  
-   PDO::SQLSRV_TXN_REPEATABLE_READ  
  
-   PDO::SQLSRV_TXN_SNAPSHOT  
  
-   PDO::SQLSRV_TXN_SERIALIZABLE  
  
Дополнительные сведения о ключе **TransactionIsolation** см. в статье [Connection Options](../../connect/php/connection-options.md).  
  
### <a name="encoding-constants"></a>Константы кодировки  
Атрибут PDO::SQLSRV_ATTR_ENCODING можно передать в параметры [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md), [PDO::setAttribute](../../connect/php/pdo-setattribute.md), [PDO::prepare](../../connect/php/pdo-prepare.md), [PDOStatement::bindColumn](../../connect/php/pdostatement-bindcolumn.md) и [PDOStatement::bindParam](../../connect/php/pdostatement-bindparam.md).  
  
Для передачи в PDO::SQLSRV_ATTR_ENCODING доступны следующие значения:  
  
|Константа драйвера PDO_SQLSRV|Описание|  
|-------------------------------|---------------|  
|PDO::SQLSRV_ENCODING_BINARY|Данные представляют собой поток необработанных байтов с сервера без применения кодировки или преобразования.<br /><br />Не является допустимым для PDO::setAttribute.|  
|PDO::SQLSRV_ENCODING_SYSTEM|Данные представлены 8-битными символами, как указано в кодовой странице языкового стандарта Windows, установленного в системе. Для всех многобайтовых символов или символов, не соответствующих этой кодовой странице, подставляется однобайтовый символ вопросительного знака (?).|  
|PDO::SQLSRV_ENCODING_UTF8|Данные имеют кодировку UTF-8. Эта кодировка используется по умолчанию.|  
|PDO::SQLSRV_ENCODING_DEFAULT|Использует PDO::SQLSRV_ENCODING_SYSTEM, если указано во время соединения.<br /><br />Используйте кодирование соединения, если указано в подготовленной инструкции.|  
  
### <a name="query-timeout"></a>Время ожидания запроса  
Атрибут PDO::SQLSRV_ATTR_QUERY_TIMEOUT — это неотрицательное целое число, представляющее время ожидания в секундах. По умолчанию использует нуль (0), означающий отсутствие времени ожидания.  
  
Атрибут PDO::SQLSRV_ATTR_QUERY_TIMEOUT можно указать с [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md), [PDO::setAttribute](../../connect/php/pdo-setattribute.md) и [PDO::prepare](../../connect/php/pdo-prepare.md).  
  
### <a name="direct-or-prepared-execution"></a>Прямое или подготовленное выполнение  
С помощью атрибута PDO::SQLSRV_ATTR_DIRECT_QUERY можно выбрать выполнение прямого запроса или подготовленной инструкции. PDO::SQLSRV_ATTR_DIRECT_QUERY можно задать с помощью [PDO::prepare](../../connect/php/pdo-prepare.md) или [PDO::setAttribute](../../connect/php/pdo-setattribute.md). Дополнительные сведения о PDO::SQLSRV_ATTR_DIRECT_QUERY см. в статье [Выполнение прямых и подготовленных инструкций в драйвере PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md).  

### <a name="handling-numeric-fetches"></a>Обработка числовых выборок
Атрибут PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE можно использовать для обработки числовых выборок из столбцов с числовыми типами SQL (бит, целое число, smallint, tinyint, число с плавающей запятой и real). Если для PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE задано значение true, результаты из столбца целых чисел представляются как целые числа, а числа SQL с плавающей запятой и числа real представлены как числа с плавающей запятой. Этот атрибут можно задать с помощью [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md). 

Поведение форматирования десятичного числа по умолчанию можно изменить с помощью атрибутов PDO::SQLSRV_ATTR_FORMAT_DECIMALS и PDO::SQLSRV_ATTR_DECIMAL_PLACES. Поведение этих атрибутов идентично поведению соответствующих параметров на стороне SQLSRV (**FormatDecimals** и **DecimalPlaces**), за исключением того, что параметры вывода не поддерживаются для форматирования. Эти атрибуты можно установить как на уровне соединения, так и на уровне оператора с помощью [PDO::setAttribute](../../connect/php/pdo-setattribute.md) или [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md), но любой атрибут оператора будет переопределять соответствующий атрибут соединения. См. подробнее о [форматировании десятичных строк и денежных значений (драйвер PDO_SQLSRV)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md).

### <a name="handling-date-and-time-fetches"></a>Обработка выборок значений даты и времени

PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE указывает, нужно ли извлекать типы даты и времени в виде объектов [PHP DateTime](http://php.net/manual/en/class.datetime.php). Если оставить значение false, по умолчанию они будут возвращаться как строки. Этот атрибут можно установить как на уровне соединения, так и на уровне оператора с помощью [PDO::setAttribute](../../connect/php/pdo-setattribute.md) или [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md), но атрибут оператора будет переопределять соответствующий атрибут соединения. Дополнительные сведения см. в разделе [Как извлечь типы даты и времени в виде объектов даты и времени PHP с помощью драйвера PDO_SQLSRV](../../connect/php/how-to-retrieve-datetime-objects-using-pdo-sqlsrv-driver.md).

## <a name="sqlsrv-driver-constants"></a>SQLSRV  
Следующие разделы содержат константы, используемые драйвером SQLSRV.  
  
### <a name="err-constants"></a>Константы ERR  
Следующая таблица содержит константы, которые используются для указания того, возвращает ли [sqlsrv_errors](../../connect/php/sqlsrv-errors.md) ошибки и (или) предупреждения.  
  
|Значение|Описание|  
|---------|---------------|  
|SQLSRV_ERR_ALL|Возвращаются ошибки и предупреждения, созданные при последнем вызове функции **sqlsrv** . Это значение по умолчанию.|  
|SQLSRV_ERR_ERRORS|Возвращаются ошибки, созданные при последнем вызове функции **sqlsrv** .|  
|SQLSRV_ERR_WARNINGS|Возвращаются предупреждения, созданные при последнем вызове функции **sqlsrv** .|  
  
### <a name="fetch-constants"></a>Константы FETCH  
Следующая таблица содержит константы, которые используются для указания типа массива, возвращаемого [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md).  
  
|Константа SQLSRV|Описание|  
|-------------------|---------------|  
|SQLSRV_FETCH_ASSOC|**sqlsrv_fetch_array** возвращает следующую строку данных в виде ассоциативного массива.|  
|SQLSRV_FETCH_BOTH|**sqlsrv_fetch_array** возвращает следующую строку данных в виде массива с числовыми и ассоциативными ключами. Это значение по умолчанию.|  
|SQLSRV_FETCH_NUMERIC|**sqlsrv_fetch_array** возвращает следующую строку данных в виде массива с числовым индексом.|  
  
### <a name="logging-constants"></a>Константы ведения журнала  
Этот раздел содержит константы, которые используются для изменения параметров ведения журнала с помощью [sqlsrv_configure](../../connect/php/sqlsrv-configure.md). Дополнительные сведения об ведении журнала см. в статье [Logging Activity](../../connect/php/logging-activity.md).  
  
Следующая таблица содержит константы, которые можно использовать в качестве значения для параметра **LogSubsystems** :  
  
|Константа SQLSRV (целочисленный эквивалент в скобках)|Описание|  
|----------------------------------------------------------|---------------|  
|SQLSRV_LOG_SYSTEM_ALL (-1)|Включает ведения журнала для всех подсистем.|  
|SQLSRV_LOG_SYSTEM_CONN (2)|Включает ведения журнала по соединениям.|  
|SQLSRV_LOG_SYSTEM_INIT (1)|Включает ведения журнала по инициализации.|  
|SQLSRV_LOG_SYSTEM_OFF (0)|Отключает ведение журнала.|  
|SQLSRV_LOG_SYSTEM_STMT (4)|Включает ведения журнала по инструкциям.|  
|SQLSRV_LOG_SYSTEM_UTIL (8)|Включает ведение журнала по функциям ошибок (таким как **handle_error** и **handle_warning**).|  
  
Следующая таблица содержит константы, которые можно использовать в качестве значения для параметра **LogSeverity** :  
  
|Константа SQLSRV (целочисленный эквивалент в скобках)|Описание|  
|----------------------------------------------------------|---------------|  
|SQLSRV_LOG_SEVERITY_ALL (-1)|Указывает, что будут регистрироваться ошибки, предупреждения и уведомления.|  
|SQLSRV_LOG_SEVERITY_ERROR (1)|Указывает, что будут регистрироваться ошибки.|  
|SQLSRV_LOG_SEVERITY_NOTICE (4)|Указывает, что будут регистрироваться уведомления.|  
|SQLSRV_LOG_SEVERITY_WARNING (2)|Указывает, что будут регистрироваться предупреждения.|  
  
### <a name="nullable-constants"></a>Константы, допускающие значение NULL  
Следующая таблица содержит константы, которые можно использовать для определения того, допускает ли столбец значение NULL или такие сведения недоступны. Можно сравнить значение ключа **Nullable** , который возвращается [sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md) для определения состояния поддержки значений NULL столбца.  
  
|Константа SQLSRV (целочисленный эквивалент в скобках)|Описание|  
|----------------------------------------------------------|---------------|  
|SQLSRV_NULLABLE_YES (0)|Этот столбец допускает значение NULL.|  
|SQLSRV_NULLABLE_NO (1)|Столбец не допускает значение NULL.|  
|SQLSRV_NULLABLE_UNKNOWN (2)|Неизвестно, допускает ли столбец значение NULL.|  
  
### <a name="param-constants"></a>Константы PARAM  
Следующий список содержит константы для указания направления параметров при вызове [sqlsrv_query](../../connect/php/sqlsrv-query.md) или [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md).  
  
|Константа SQLSRV|Описание|  
|-------------------|---------------|  
|SQLSRV_PARAM_IN|Указывает параметр ввода.|  
|SQLSRV_PARAM_INOUT|Указывает двунаправленный параметр.|  
|SQLSRV_PARAM_OUT|Указывает параметр вывода.|  
  
### <a name="phptype-constants"></a>Константы PHPTYPE  
Следующая таблица содержит константы, которые используются для описания типов данных PHP. Дополнительные сведения о типах данных PHP см. в статье [Типы PHP](https://php.net/manual/en/language.types.php).  
  
|Константа SQLSRV|Тип данных PHP|  
|-------------------|-----------------|  
|SQLSRV_PHPTYPE_INT|Целое число|  
|SQLSRV_PHPTYPE_DATETIME|Datetime|  
|SQLSRV_PHPTYPE_FLOAT|Float|  
|SQLSRV_PHPTYPE_STREAM($encoding<sup>1</sup>)|Поток|  
|SQLSRV_PHPTYPE_STRING($encoding<sup>1</sup>)|Строка|  
  
1. **SQLSRV_PHPTYPE_STREAM** и **SQLSRV_PHPTYPE_STRING** принимают параметр, который указывает кодировку потока. Следующая таблица содержит константы SQLSRV, которые являются допустимыми параметрами, а также описание соответствующей кодировки.  
  
|Константа SQLSRV|Описание|  
|-------------------|---------------|  
|SQLSRV_ENC_BINARY|Данные возвращаются в виде потока необработанных байтов с сервера без применения кодировки или преобразования.|  
|SQLSRV_ENC_CHAR|Данные возвращаются в виде 8-битных символов, как указано в кодовой странице языкового стандарта Windows, установленного в системе. Для всех многобайтовых символов или символов, не соответствующих этой кодовой странице, подставляется однобайтовый символ вопросительного знака (?).<br /><br />Эта кодировка используется по умолчанию.|  
|"UTF-8"|Данные возвращаются с кодировкой UTF-8. Эта константа была добавлена в версии 1.1 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Дополнительные сведения о поддержке UTF-8 см. в статье [Практическое руководство. Отправка и извлечение данных UTF-8 с помощью встроенной поддержки UTF-8](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md).|  
  
> [!NOTE]  
> При использовании **SQLSRV_PHPTYPE_STREAM** или **SQLSRV_PHPTYPE_STRING** должна быть указана кодировка. Если параметр не указан, возвращается ошибка.  
  
Дополнительные сведения об этих константах см. в статье [Практическое руководство. Указание типов данных PHP](../../connect/php/how-to-specify-php-data-types.md)и [Практическое руководство. Извлечение символьных данных в виде потока с помощью драйвера SQLSRV](../../connect/php/how-to-retrieve-character-data-as-a-stream-using-the-sqlsrv-driver.md).  
  
### <a name="sqltype-constants"></a>Константы SQLTYPE  
Следующая таблица содержит константы, которые используются для описания типов данных SQL Server. Некоторые константы являются функциональными и могут принимать параметры, которые соответствуют точности, масштабу и (или) длине.  При привязке параметров должны использоваться функциональные константы. Для сравнения типов требуются стандартные (не функциональные) константы. Дополнительные сведения о типах данных SQL Server см. в статье [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md). Сведения о точности, масштабе и длине см. в статье [Точность, масштаб и длина (Transact-SQL)](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
|Константа SQLSRV|Тип данных SQL Server|  
|-------------------|------------------------|  
|SQLSRV_SQLTYPE_BIGINT|BIGINT|  
|SQLSRV_SQLTYPE_BINARY|binary|  
|SQLSRV_SQLTYPE_BIT|bit|  
|SQLSRV_SQLTYPE_CHAR|char<sup>5</sup>|  
|SQLSRV_SQLTYPE_CHAR($charCount)|char|  
|SQLSRV_SQLTYPE_DATE|date<sup>4</sup>|  
|SQLSRV_SQLTYPE_DATETIME|DATETIME|  
|SQLSRV_SQLTYPE_DATETIME2|datetime2<sup>4</sup>|  
|SQLSRV_SQLTYPE_DATETIMEOFFSET|datetimeoffset<sup>4</sup>|  
|SQLSRV_SQLTYPE_DECIMAL|decimal<sup>5</sup>|
|SQLSRV_SQLTYPE_DECIMAL($precision, $scale)|Decimal|  
|SQLSRV_SQLTYPE_FLOAT|FLOAT|  
|SQLSRV_SQLTYPE_IMAGE|image<sup>1</sup>|  
|SQLSRV_SQLTYPE_INT|INT|  
|SQLSRV_SQLTYPE_MONEY|money| 
|SQLSRV_SQLTYPE_NCHAR|nchar<sup>5</sup>|   
|SQLSRV_SQLTYPE_NCHAR($charCount)|nchar|  
|SQLSRV_SQLTYPE_NUMERIC|numeric<sup>5</sup>|
|SQLSRV_SQLTYPE_NUMERIC($precision, $scale)|NUMERIC|  
|SQLSRV_SQLTYPE_NVARCHAR|nvarchar<sup>5</sup>|  
|SQLSRV_SQLTYPE_NVARCHAR($charCount)|nvarchar|  
|SQLSRV_SQLTYPE_NVARCHAR('max')|nvarchar(MAX)|  
|SQLSRV_SQLTYPE_NTEXT|ntext<sup>2</sup>|  
|SQLSRV_SQLTYPE_REAL|real|  
|SQLSRV_SQLTYPE_SMALLDATETIME|smalldatetime|  
|SQLSRV_SQLTYPE_SMALLINT|smallint|  
|SQLSRV_SQLTYPE_SMALLMONEY|smallmoney|  
|SQLSRV_SQLTYPE_TEXT|text<sup>3</sup>|  
|SQLSRV_SQLTYPE_TIME|time<sup>4</sup>|  
|SQLSRV_SQLTYPE_TIMESTAMP|TIMESTAMP|  
|SQLSRV_SQLTYPE_TINYINT|tinyint|  
|SQLSRV_SQLTYPE_UNIQUEIDENTIFIER|UNIQUEIDENTIFIER|  
|SQLSRV_SQLTYPE_UDT|(UDT)|  
|SQLSRV_SQLTYPE_VARBINARY|varbinary<sup>5</sup>|  
|SQLSRV_SQLTYPE_VARBINARY($byteCount)|varbinary|  
|SQLSRV_SQLTYPE_VARBINARY('max')|varbinary(MAX)|  
|SQLSRV_SQLTYPE_VARCHAR|varchar<sup>5</sup>|  
|SQLSRV_SQLTYPE_VARCHAR($charCount)|varchar|  
|SQLSRV_SQLTYPE_VARCHAR('max')|varchar(MAX)|  
|SQLSRV_SQLTYPE_XML|Xml|  
  
1.  Это устаревший тип, соответствующий типу varbinary(max).  
  
2.  Это устаревший тип, соответствующий более новому типу nvarchar.  
  
3.  Это устаревший тип, соответствующий более новому типу varchar.  
  
4.  Поддержка PDO для этого типа была добавлена в версии 1.1 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  

5.  Эти константы следует использовать в операциях сравнения типов, и они не должны заменять функциональные константы на аналогичный синтаксис. Для привязки параметров следует использовать функциональные константы.

  
Следующая таблица содержит константы SQLTYPE, которые принимают параметры, а также диапазон допустимых значений для параметра.  
  
|SQLTYPE|Параметр|Диапазон допустимых значений для параметра|  
|-----------|-------------|---------------------------------|  
|SQLSRV_SQLTYPE_CHAR,<br /><br />SQLSRV_SQLTYPE_VARCHAR|charCount|1–8000|  
|SQLSRV_SQLTYPE_NCHAR,<br /><br />SQLSRV_SQLTYPE_NVARCHAR|charCount|1–4000|  
|SQLSRV_SQLTYPE_BINARY,<br /><br />SQLSRV_SQLTYPE_VARBINARY|byteCount|1–8000|  
|SQLSRV_SQLTYPE_DECIMAL,<br /><br />SQLSRV_SQLTYPE_NUMERIC|точность|1–38|  
|SQLSRV_SQLTYPE_DECIMAL,<br /><br />SQLSRV_SQLTYPE_NUMERIC|scale|1 — точность|  
  
### <a name="transaction-isolation-level-constants"></a>Константы уровня изоляции транзакции  
Ключ **TransactionIsolation** , который используется с [sqlsrv_connect](../../connect/php/sqlsrv-connect.md), принимает одну из следующих констант:  
  
-   SQLSRV_TXN_READ_UNCOMMITTED  
  
-   SQLSRV_TXN_READ_COMMITTED  
  
-   SQLSRV_TXN_REPEATABLE_READ  
  
-   SQLSRV_TXN_SNAPSHOT  
  
-   SQLSRV_TXN_SERIALIZABLE  
  
### <a name="cursor-and-scrolling-constants"></a>Курсор и прокрутка констант  
Следующие константы указывают тип курсора, который можно использовать в результирующем наборе:  
  
-   SQLSRV_CURSOR_FORWARD  
  
-   SQLSRV_CURSOR_STATIC  
  
-   SQLSRV_CURSOR_DYNAMIC  
  
-   SQLSRV_CURSOR_KEYSET  
  
-   SQLSRV_CURSOR_CLIENT_BUFFERED  
  
Следующие константы указывают, какую строку следует выбрать в результирующем наборе:  
  
-   SQLSRV_SCROLL_NEXT  
  
-   SQLSRV_SCROLL_PRIOR  
  
-   SQLSRV_SCROLL_FIRST  
  
-   SQLSRV_SCROLL_LAST  
  
-   SQLSRV_SCROLL_ABSOLUTE  
  
-   SQLSRV_SCROLL_RELATIVE  
  
Сведения об использовании этих констант см. в статье [Specifying a Cursor Type and Selecting Rows](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md).  
  
## <a name="see-also"></a>См. также:  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
  
