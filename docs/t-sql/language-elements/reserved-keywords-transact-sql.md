---
title: "Зарезервированные ключевые слова (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- ODBC function calls
- keywords [SQL Server], reserved
- reserved words [SQL Server]
- keywords [SQL Server]
ms.assetid: ed8b3e27-6796-40f0-aef3-0cac5e0e2418
caps.latest.revision: "53"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: f2a3e554a7a3b46242c44c38137609322e6d89f4
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/19/2018
---
# <a name="reserved-keywords-transact-sql"></a>Зарезервированные ключевые слова (Transact-SQL)
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
|EXECUTE|PRIMARY|WITHIN GROUP|  
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
|**ДЕЙСТВИЕ**|**EXECUTE**|**PAD**|  
|**ADA**|**EXISTS**|**ЧАСТИЧНОЕ**|  
|**ADD**|**EXTERNAL**|**PASCAL**|  
|**ALL**|**EXTRACT**|**ПОЛОЖЕНИЕ**|  
|**ВЫДЕЛИТЬ**|**ЗНАЧЕНИЕ FALSE**|**ТОЧНОСТЬ**|  
|**ALTER**|**FETCH**|**ПОДГОТОВКА**|  
|**AND**|**FIRST**|**СОХРАНИТЬ**|  
|**ANY**|**FLOAT**|**PRIMARY**|  
|**—**|**FOR**|**ПЕРЕД**|  
|**Службы Analysis Services**|**ВНЕШНИЙ**|**PRIVILEGES**|  
|**ASC**|**FORTRAN**|**PROCEDURE**|  
|**УТВЕРЖДЕНИЕ**|**НАЙТИ**|**PUBLIC**|  
|**AT**|**FROM**|**READ**|  
|**AUTHORIZATION**|**ПОЛНОЕ**|**REAL**|  
|**AVG**|**GET**|**ССЫЛКИ**|  
|**BEGIN**|**GLOBAL**|**ОТНОСИТЕЛЬНЫЙ**|  
|**BETWEEN**|**GO**|**ОГРАНИЧЕНИЯ**|  
|**BIT**|**GOTO**|**REVOKE**|  
|**BIT_LENGTH**|**GRANT**|**RIGHT**|  
|**BOTH**|**GROUP**|**ROLLBACK**|  
|**BY**|**НАЛИЧИЕ**|**ROWS**|  
|**CASCADE**|**HOUR**|**SCHEMA**|  
|**CASCADED**|**УДОСТОВЕРЕНИЕ**|**SCROLL**|  
|**CASE**|**НЕМЕДЛЕННО**|**SECOND**|  
|**CAST**|**IN**|**РАЗДЕЛ**|  
|**КАТАЛОГ**|**ВКЛЮЧИТЬ**|**SELECT**|  
|**CHAR**|**INDEX**|**СЕАНС**|  
|**CHAR_LENGTH**|**ИНДИКАТОР**|**SESSION_USER**|  
|**СИМВОЛ**|**ИЗНАЧАЛЬНО**|**SET**|  
|**CHARACTER_LENGTH**|**ВНУТРЕННЕЕ**|**РАЗМЕР**|  
|**ФЛАЖОК**|**INPUT**|**SMALLINT**|  
|**CLOSE**|**БЕЗ УЧЕТА**|**SOME**|  
|**COALESCE**|**INSERT**|**SPACE**|  
|**РАЗБОР ПО КОПИЯМ**|**INT**|**SQL**|  
|**ПАРАМЕТРЫ СОРТИРОВКИ**|**ЦЕЛОЕ ЧИСЛО СО ЗНАКОМ**|**SQLCA**|  
|**COLUMN**|**INTERSECT**|**SQLCODE**|  
|**COMMIT**|**ИНТЕРВАЛ**|**SQLERROR**|  
|**CONNECT**|**В**|**SQLSTATE**|  
|**ПОДКЛЮЧЕНИЕ**|**—**|**SQLWARNING**|  
|**ОГРАНИЧЕНИЯ**|**ИЗОЛЯЦИЯ**|**SUBSTRING**|  
|**ОГРАНИЧЕНИЯ**|**JOIN**|**SUM**|  
|**CONTINUE**|**KEY**|**SYSTEM_USER**|  
|**ПРЕОБРАЗОВАНИЕ**|**LANGUAGE**|**TABLE**|  
|**СООТВЕТСТВУЮЩИЙ**|**LAST**|**ВРЕМЕННЫЕ**|  
|**COUNT**|**НАЧАЛЬНЫЕ**|**ЗАТЕМ**|  
|**СОЗДАНИЕ**|**LEFT**|**ВРЕМЯ**|  
|**CROSS**|**УРОВЕНЬ**|**ОТМЕТКА ВРЕМЕНИ**|  
|**ТЕКУЩИЙ**|**LIKE**|**TIMEZONE_HOUR**|  
|**CURRENT_DATE**|**ЛОКАЛЬНЫЕ**|**TIMEZONE_MINUTE**|  
|**CURRENT_TIME**|**LOWER**|**Кому**|  
|**CURRENT_TIMESTAMP**|**MATCH**|**В КОНЦЕ**|  
|**CURRENT_USER**|**MAX**|**ТРАНЗАКЦИИ**|  
|**CURSOR**|**MIN**|**TRANSLATE**|  
|**ДАТА**|**МИНУТЫ**|**ПЕРЕВОД**|  
|**DAY**|**МОДУЛЬ**|**TRIM**|  
|**DEALLOCATE**|**MONTH**|**ЗНАЧЕНИЕ TRUE**|  
|**DEC**|**ИМЕНА**|**UNION**|  
|**ДЕСЯТИЧНОЕ ЧИСЛО**|**НАЦИОНАЛЬНЫЙ**|**UNIQUE**|  
|**ОБЪЯВЛЕНИЯ**|**ЕСТЕСТВЕННОЕ**|**UNKNOWN**|  
|**DEFAULT**|**NCHAR**|**UPDATE**|  
|**ДОПУСКАЮЩЕЕ ЗАДЕРЖКУ**|**NEXT**|**UPPER**|  
|**DEFERRED**|**НЕТ**|**ИСПОЛЬЗОВАНИЕ**|  
|**DELETE**|**NONE**|**USER**|  
|**DESC**|**NOT**|**С ПОМОЩЬЮ**|  
|**DESCRIBE**|**NULL**|**VALUE**|  
|**ДЕСКРИПТОР**|**NULLIF**|**ЗНАЧЕНИЯ**|  
|**DIAGNOSTICS**|**ЧИСЛОВОЙ**|**VARCHAR**|  
|**DISCONNECT**|**OCTET_LENGTH**|**ПЕРЕМЕННОЙ**|  
|**DISTINCT**|**OF**|**VIEW**|  
|**DOMAIN**|**ON**|**КОГДА**|  
|**DOUBLE**|**ТОЛЬКО**|**КАЖДЫЙ РАЗ, КОГДА**|  
|**DROP**|**OPEN**|**WHERE**|  
|**ELSE**|**ПАРАМЕТР**|**WITH**|  
|**END**|**или**|**WORK**|  
|**END-EXEC**|**ПОРЯДОК**|**ЗАПИСИ**|  
|**ESCAPE-**|**ВНЕШНЕЕ**|**YEAR**|  
|**EXCEPT**|**OUTPUT**|**ЗОНЫ**|  
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
|CUME_DIST|NEW|TIMESTAMP|  
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
|DEFERRED|OUTPUT|VALUE|  
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
  
## <a name="see-also"></a>См. также  
 [SET QUOTED_IDENTIFIER &#40; Transact-SQL &#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)   
 [Уровень совместимости инструкции ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
  
  
