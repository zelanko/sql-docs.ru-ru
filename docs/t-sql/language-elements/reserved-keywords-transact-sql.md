---
title: "Зарезервированные ключевые слова (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- ODBC function calls
- keywords [SQL Server], reserved
- reserved words [SQL Server]
- keywords [SQL Server]
ms.assetid: ed8b3e27-6796-40f0-aef3-0cac5e0e2418
caps.latest.revision: 53
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: efaa21099f422ae812168561351a359fc89f8e0d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="reserved-keywords-transact-sql"></a>Зарезервированные ключевые слова Transact-SQL
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует зарезервированные ключевые слова для определения, манипулирования и доступа к базам данных. Зарезервированные ключевые слова являются частью грамматики языка [!INCLUDE[tsql](../../includes/tsql-md.md)], которые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует для синтаксического анализа инструкций и пакетов языка [!INCLUDE[tsql](../../includes/tsql-md.md)]. Хотя синтаксис скриптов языка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет использовать зарезервированные слова [!INCLUDE[tsql](../../includes/tsql-md.md)] в качестве идентификаторов и имен объектов, это можно сделать только при помощи идентификаторов с разделителями.  
  
 Следующая таблица содержит список зарезервированных слов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
||||  
|-|-|-|  
|ADD|EXTERNAL|PROCEDURE|  
|ALL|FETCH|PUBLIC|  
|ALTER|FILE|RAISERROR|  
|и|FILLFACTOR|READ|  
|ANY|FOR|READTEXT|  
|AS|FOREIGN|RECONFIGURE|  
|ASC|FREETEXT|REFERENCES|  
|AUTHORIZATION|FREETEXTTABLE|REPLICATION|  
|BACKUP|FROM|RESTORE|  
|BEGIN|ПОЛНОЕ|RESTRICT|  
|BETWEEN|FUNCTION|RETURN|  
|BREAK|GOTO|REVERT|  
|BROWSE|GRANT|REVOKE|  
|BULK|GROUP|RIGHT|  
|BY|HAVING|ROLLBACK|  
|CASCADE|HOLDLOCK|ROWCOUNT|  
|CASE|IDENTITY|ROWGUIDCOL|  
|CHECK|IDENTITY_INSERT|RULE|  
|CHECKPOINT|IDENTITYCOL|SAVE|  
|CLOSE|IF|SCHEMA|  
|CLUSTERED|IN|SECURITYAUDIT|  
|COALESCE|INDEX|SELECT|  
|COLLATE|INNER|SEMANTICKEYPHRASETABLE|  
|COLUMN|INSERT|SEMANTICSIMILARITYDETAILSTABLE|  
|COMMIT|INTERSECT|SEMANTICSIMILARITYTABLE|  
|COMPUTE|INTO|SESSION_USER|  
|CONSTRAINT|IS|SET|  
|CONTAINS|JOIN|SETUSER|  
|CONTAINSTABLE|KEY|SHUTDOWN|  
|CONTINUE|KILL|SOME|  
|CONVERT|LEFT|STATISTICS|  
|CREATE|LIKE|SYSTEM_USER|  
|CROSS|LINENO|TABLE|  
|CURRENT|LOAD|TABLESAMPLE|  
|CURRENT_DATE|MERGE|TEXTSIZE|  
|CURRENT_TIME|NATIONAL|THEN|  
|CURRENT_TIMESTAMP|NOCHECK|TO|  
|CURRENT_USER|NONCLUSTERED|В начало|  
|CURSOR|NOT|TRAN|  
|DATABASE|NULL|TRANSACTION|  
|DBCC|NULLIF|TRIGGER|  
|DEALLOCATE|OF|TRUNCATE|  
|DECLARE|OFF|TRY_CONVERT|  
|DEFAULT|OFFSETS|TSEQUAL|  
|DELETE|ON|UNION|  
|DENY|OPEN|UNIQUE|  
|DESC|OPENDATASOURCE|UNPIVOT|  
|DISK;|OPENQUERY|UPDATE|  
|DISTINCT|OPENROWSET|UPDATETEXT|  
|DISTRIBUTED|OPENXML|USE|  
|DOUBLE|OPTION|Пользователь|  
|DROP|или|VALUES|  
|DUMP;|ORDER|VARYING|  
|ELSE|OUTER|VIEW|  
|END|OVER|WAITFOR|  
|ERRLVL|PERCENT|WHEN|  
|ESCAPE|PIVOT|WHERE|  
|EXCEPT|PLAN|WHILE|  
|EXEC|PRECISION|на|  
|Выполните|PRIMARY|WITHIN GROUP|  
|EXISTS|PRINT|WRITETEXT|  
|EXIT|PROC||  
  
 Кроме того, стандартом ISO определяется список зарезервированных ключевых слов. Избегайте применения зарезервированных ключевых слов ISO в качестве имен и идентификаторов объектов. Список зарезервированных ключевых слов ODBC, приведенный в следующей таблице, совпадает со списком зарезервированных ключевых слов ISO.  
  
> [!NOTE]  
>  Иногда список зарезервированных ключевых слов стандарта ISO более строгий, чем список [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а иногда менее строгий. Например, список зарезервированных ключевых слов ISO содержит **INT**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не должен выделять это слово как зарезервированное ключевое слово.  
  
 Зарезервированные ключевые слова языка [!INCLUDE[tsql](../../includes/tsql-md.md)] можно использовать для идентификаторов или имен баз данных или таких объектов базы данных, как таблицы, столбцы, представления и т. п. Для этого необходимо использовать идентификаторы, заключенные в кавычки, или идентификаторы с разделителями. Зарезервированные ключевые слова можно без ограничений использовать в качестве имен переменных или параметров хранимых процедур.  
  
## <a name="odbc-reserved-keywords"></a>Зарезервированные ключевые слова ODBC  
 Следующие слова зарезервированы для использования в вызовах функций ODBC. Эти слова не входят в минимальную грамматику SQL, поэтому, чтобы обеспечить совместимость с драйверами, поддерживающими базовую грамматику SQL, приложения должны избегать использования этих ключевых слов.  
  
 Следующая таблица содержит текущий список зарезервированных ключевых слов ODBC.  
  
||||  
|-|-|-|  
|**АБСОЛЮТНЫЙ**|**EXEC**|**ОПЕРАТОР OVERLAPS**|  
|**ДЕЙСТВИЕ**|**EXECUTE**|**ПАНЕЛЬ**|  
|**ADA**|**СУЩЕСТВУЕТ**|**ЧАСТИЧНОЕ**|  
|**ДОБАВИТЬ**|**EXTERNAL**|**PASCAL**|  
|**ALL**|**ИЗВЛЕЧЕНИЕ**|**ПОЛОЖЕНИЕ**|  
|**ВЫДЕЛИТЬ**|**ЗНАЧЕНИЕ FALSE**|**ТОЧНОСТЬ**|  
|**ALTER**|**ВЫБОРКИ**|**ПОДГОТОВКА**|  
|**AND**|**ПЕРВЫЙ**|**СОХРАНИТЬ**|  
|**ЛЮБОЙ**|**ЧИСЛО С ПЛАВАЮЩЕЙ ЗАПЯТОЙ**|**PRIMARY**|  
|**—**|**ДЛЯ**|**ПЕРЕД**|  
|**Службы Analysis Services**|**ВНЕШНИЙ**|**ПРИВИЛЕГИИ**|  
|**ASC**|**FORTRAN**|**ПРОЦЕДУРА**|  
|**УТВЕРЖДЕНИЕ**|**НАЙТИ**|**PUBLIC**|  
|**AT**|**FROM**|**ЧТЕНИЕ**|  
|**АВТОРИЗАЦИЯ**|**ПОЛНОЕ**|**REAL**|  
|**СР.**|**ПОЛУЧИТЬ**|**ССЫЛКИ**|  
|**BEGIN**|**ГЛОБАЛЬНЫЕ**|**ОТНОСИТЕЛЬНЫЙ**|  
|**BETWEEN**|**ПЕРЕЙТИ**|**ОГРАНИЧЕНИЯ**|  
|**БИТ**|**ОПЕРАТОР GOTO**|**REVOKE**|  
|**BIT_LENGTH**|**GRANT**|**RIGHT**|  
|**ОБА**|**ГРУППЫ**|**ОТКАТ**|  
|**ПО**|**НАЛИЧИЕ**|**СТРОКИ**|  
|**CASCADE**|**ЧАС**|**СХЕМЫ**|  
|**КАСКАДОМ**|**УДОСТОВЕРЕНИЕ**|**ПРОКРУТКИ**|  
|**РЕГИСТР**|**НЕМЕДЛЕННО**|**ВТОРОЙ**|  
|**ПРИВЕДЕНИЕ ТИПОВ**|**IN**|**РАЗДЕЛ**|  
|**КАТАЛОГ**|**ВКЛЮЧИТЬ**|**SELECT**|  
|**CHAR**|**ИНДЕКС**|**СЕАНС**|  
|**CHAR_LENGTH**|**ИНДИКАТОР**|**ФУНКЦИЯ SESSION_USER**|  
|**СИМВОЛ**|**ИЗНАЧАЛЬНО**|**НАБОР**|  
|**CHARACTER_LENGTH**|**ВНУТРЕННЕЕ**|**РАЗМЕР**|  
|**ФЛАЖОК**|**ВХОДНЫЕ ДАННЫЕ**|**SMALLINT**|  
|**ЗАКРЫТЬ**|**БЕЗ УЧЕТА**|**НЕКОТОРЫЕ**|  
|**ФУНКЦИЯ ОБЪЕДИНЕНИЯ**|**INSERT**|**ПРОБЕЛ**|  
|**РАЗБОР ПО КОПИЯМ**|**INT**|**SQL**|  
|**ПАРАМЕТРЫ СОРТИРОВКИ**|**ЦЕЛОЕ ЧИСЛО СО ЗНАКОМ**|**SQLCA**|  
|**СТОЛБЕЦ**|**INTERSECT**|**SQLCODE**|  
|**ФИКСАЦИЯ**|**ИНТЕРВАЛ**|**SQLERROR**|  
|**ПОДКЛЮЧЕНИЕ**|**В**|**SQLSTATE**|  
|**ПОДКЛЮЧЕНИЕ**|**IS**|**SQLWARNING**|  
|**ОГРАНИЧЕНИЯ**|**ИЗОЛЯЦИЯ**|**SUBSTRING**|  
|**ОГРАНИЧЕНИЯ**|**ПРИСОЕДИНЕНИЕ**|**СУММА**|  
|**ПРОДОЛЖИТЬ**|**КЛЮЧ**|**ФУНКЦИЯ SYSTEM_USER**|  
|**ПРЕОБРАЗОВАНИЕ**|**LANGUAGE**|**ТАБЛИЦА**|  
|**СООТВЕТСТВУЮЩИЙ**|**ПОСЛЕДНИЙ**|**ВРЕМЕННЫЕ**|  
|**СЧЕТЧИК**|**НАЧАЛЬНЫЕ**|**ЗАТЕМ**|  
|**СОЗДАНИЕ**|**LEFT**|**ВРЕМЯ**|  
|**КРОСС-**|**УРОВЕНЬ**|**ОТМЕТКА ВРЕМЕНИ**|  
|**ТЕКУЩИЙ**|**LIKE**|**TIMEZONE_HOUR**|  
|**CURRENT_DATE**|**ЛОКАЛЬНЫЕ**|**TIMEZONE_MINUTE**|  
|**CURRENT_TIME**|**НИЖЕ**|**КОМУ**|  
|**CURRENT_TIMESTAMP**|**MATCH**|**В КОНЦЕ**|  
|**ФУНКЦИЯ CURRENT_USER**|**MAX**|**ТРАНЗАКЦИИ**|  
|**КУРСОР**|**МИН.**|**ПЕРЕВЕСТИ**|  
|**ДАТА**|**МИНУТЫ**|**ПЕРЕВОД**|  
|**ДЕНЬ**|**МОДУЛЬ**|**ФУНКЦИЯ TRIM**|  
|**DEALLOCATE**|**МЕСЯЦ**|**ЗНАЧЕНИЕ TRUE**|  
|**DEC**|**ИМЕНА**|**ОБЪЕДИНЕНИЕ**|  
|**ДЕСЯТИЧНОЕ ЧИСЛО**|**НАЦИОНАЛЬНЫЙ**|**УНИКАЛЬНЫЙ**|  
|**ОБЪЯВЛЕНИЯ**|**ЕСТЕСТВЕННОЕ**|**НЕИЗВЕСТНЫЙ**|  
|**ПО УМОЛЧАНИЮ**|**NCHAR**|**UPDATE**|  
|**ДОПУСКАЮЩЕЕ ЗАДЕРЖКУ**|**ДАЛЕЕ**|**ВЕРХНИЙ**|  
|**ОТЛОЖЕНО**|**НЕТ**|**ИСПОЛЬЗОВАНИЕ**|  
|**DELETE**|**NONE**|**ПОЛЬЗОВАТЕЛЬ**|  
|**DESC**|**NOT**|**С ПОМОЩЬЮ**|  
|**ОПИСАНИЯ**|**NULL**|**VALUE**|  
|**ДЕСКРИПТОР**|**ФУНКЦИЯ NULLIF**|**ЗНАЧЕНИЯ**|  
|**ДИАГНОСТИКА**|**ЧИСЛОВОЙ**|**VARCHAR**|  
|**ОТКЛЮЧЕНИЕ**|**OCTET_LENGTH**|**ПЕРЕМЕННОЙ**|  
|**DISTINCT**|**ИЗ**|**ПРЕДСТАВЛЕНИЕ**|  
|**ДОМЕН**|**ON**|**КОГДА**|  
|**DOUBLE**|**ТОЛЬКО**|**КАЖДЫЙ РАЗ, КОГДА**|  
|**DROP**|**ОТКРЫТЬ**|**WHERE**|  
|**ELSE**|**ПАРАМЕТР**|**С ПОМОЩЬЮ**|  
|**END**|**OR**|**РАБОТЫ**|  
|**END-EXEC**|**ПОРЯДОК**|**ЗАПИСИ**|  
|**ESCAPE-**|**ВНЕШНЕЕ**|**ГОД**|  
|**ЗА ИСКЛЮЧЕНИЕМ**|**ВЫХОДНЫЕ ДАННЫЕ**|**ЗОНЫ**|  
|**ИСКЛЮЧЕНИЕ**|||  
  
## <a name="future-keywords"></a>Будущие ключевые слова  
 Следующие ключевые слова могут быть зарезервированы в будущих выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по мере реализации новых возможностей. Старайтесь не использовать эти слова в качестве идентификаторов.  
  
||||  
|-|-|-|  
|ABSOLUTE|HOST|RELATIVE|  
|ACTION|HOUR|RELEASE|  
|ADMIN|IGNORE|RESULT|  
|AFTER|IMMEDIATE|RETURNS|  
|AGGREGATE|INDICATOR|ROLE|  
|ALIAS|INITIALIZE|ROLLUP|  
|ALLOCATE|INITIALLY|ROUTINE|  
|ARE|INOUT|ROW|  
|ARRAY|INPUT|ROWS|  
|ASENSITIVE|INT|SAVEPOINT|  
|ASSERTION|INTEGER|SCROLL|  
|ASYMMETRIC|INTERSECTION|SCOPE|  
|AT|INTERVAL|SEARCH|  
|ATOMIC|ISOLATION|SECOND|  
|BEFORE|ITERATE|SECTION|  
|BINARY|LANGUAGE|SENSITIVE|  
|BIT|LARGE|SEQUENCE|  
|BLOB|LAST|SESSION|  
|BOOLEAN|LATERAL|SETS|  
|BOTH|LEADING|SIMILAR|  
|BREADTH|LESS|SIZE|  
|CALL|LEVEL|SMALLINT|  
|CALLED|LIKE_REGEX|SPACE|  
|CARDINALITY|LIMIT|SPECIFIC|  
|CASCADED|LN|SPECIFICTYPE|  
|CAST|LOCAL|SQL|  
|CATALOG|LOCALTIME|SQLEXCEPTION|  
|CHAR|LOCALTIMESTAMP|SQLSTATE|  
|CHARACTER|LOCATOR|SQLWARNING|  
|CLASS|MAP|START|  
|CLOB|MATCH|STATE|  
|COLLATION|MEMBER|STATEMENT|  
|COLLECT|METHOD|STATIC|  
|COMPLETION|MINUTE|STDDEV_POP|  
|CONDITION|MOD|STDDEV_SAMP|  
|CONNECT|MODIFIES|STRUCTURE|  
|CONNECTION|MODIFY|SUBMULTISET|  
|CONSTRAINTS|MODULE|SUBSTRING_REGEX|  
|CONSTRUCTOR|MONTH|SYMMETRIC|  
|CORR|MULTISET|SYSTEM|  
|CORRESPONDING|NAMES|TEMPORARY|  
|COVAR_POP|NATURAL|TERMINATE|  
|COVAR_SAMP|NCHAR|THAN|  
|CUBE|NCLOB|TIME|  
|CUME_DIST|NEW|timestamp|  
|CURRENT_CATALOG|NEXT|TIMEZONE_HOUR|  
|CURRENT_DEFAULT_TRANSFORM_GROUP|Нет|TIMEZONE_MINUTE|  
|CURRENT_PATH|None|TRAILING|  
|CURRENT_ROLE|NORMALIZE|TRANSLATE_REGEX|  
|CURRENT_SCHEMA|NUMERIC|TRANSLATION|  
|CURRENT_TRANSFORM_GROUP_FOR_TYPE|OBJECT|TREAT|  
|CYCLE|OCCURRENCES_REGEX|TRUE|  
|DATA|OLD|UESCAPE|  
|DATE|ONLY|UNDER|  
|DAY|OPERATION|UNKNOWN|  
|DEC|ORDINALITY|UNNEST|  
|DECIMAL|OUT|USAGE|  
|DEFERRABLE|OVERLAY|USING|  
|DEFERRED|OUTPUT|Value|  
|DEPTH|PAD|VAR_POP|  
|DEREF|Параметр|VAR_SAMP|  
|DESCRIBE|PARAMETERS|VARCHAR|  
|DESCRIPTOR|PARTIAL|VARIABLE|  
|DESTROY|PARTITION|WHENEVER|  
|DESTRUCTOR|PATH|WIDTH_BUCKET|  
|DETERMINISTIC|POSTFIX|WITHOUT|  
|DICTIONARY|PREFIX|WINDOW|  
|DIAGNOSTICS|PREORDER|WITHIN|  
|DISCONNECT|PREPARE|WORK|  
|DOMAIN|PERCENT_RANK|WRITE|  
|DYNAMIC|PERCENTILE_CONT|XMLAGG|  
|EACH|PERCENTILE_DISC|XMLATTRIBUTES|  
|ELEMENT|POSITION_REGEX|XMLBINARY|  
|END-EXEC|PRESERVE|XMLCAST|  
|EQUALS|PRIOR|XMLCOMMENT|  
|EVERY|PRIVILEGES|XMLCONCAT|  
|EXCEPTION|RANGE|XMLDOCUMENT|  
|FALSE|READS|XMLELEMENT|  
|FILTER|REAL|XMLEXISTS|  
|FIRST|RECURSIVE|XMLFOREST|  
|FLOAT|REF|XMLITERATE|  
|FOUND|REFERENCING|XMLNAMESPACES|  
|FREE|REGR_AVGX|XMLPARSE|  
|FULLTEXTTABLE|REGR_AVGY|XMLPI|  
|FUSION|REGR_COUNT|XMLQUERY|  
|GENERAL|REGR_INTERCEPT|XMLSERIALIZE|  
|GET|REGR_R2|XMLTABLE|  
|GLOBAL|REGR_SLOPE|XMLTEXT|  
|GO|REGR_SXX|XMLVALIDATE|  
|GROUPING|REGR_SXY|YEAR|  
|HOLD|REGR_SYY|ZONE|  
  
## <a name="see-also"></a>См. также:  
 [SET QUOTED_IDENTIFIER &#40; Transact-SQL &#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)   
 [Уровень совместимости инструкции ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
  
  
