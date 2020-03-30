---
title: Зарезервированные ключевые слова (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- ODBC function calls
- keywords [SQL Server], reserved
- reserved words [SQL Server]
- keywords [SQL Server]
ms.assetid: ed8b3e27-6796-40f0-aef3-0cac5e0e2418
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cc0390a01bec10b58ed29d1824e8d0b482e78358
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68091772"
---
# <a name="reserved-keywords-transact-sql"></a>Зарезервированные ключевые слова (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует зарезервированные ключевые слова для определения, манипулирования и доступа к базам данных. Зарезервированные ключевые слова являются частью грамматики языка [!INCLUDE[tsql](../../includes/tsql-md.md)], которые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует для синтаксического анализа инструкций и пакетов языка [!INCLUDE[tsql](../../includes/tsql-md.md)]. Хотя синтаксис скриптов языка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет использовать зарезервированные слова [!INCLUDE[tsql](../../includes/tsql-md.md)] в качестве идентификаторов и имен объектов, это можно сделать только при помощи идентификаторов с разделителями.  
  
 Следующая таблица содержит список зарезервированных слов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и Хранилища данных SQL Azure.  
  
||||  
|-|-|-|  
|ADD|EXTERNAL|PROCEDURE|  
|ALL|FETCH|PUBLIC|  
|ALTER|FILE|RAISERROR|  
|AND|FILLFACTOR|READ|  
|ANY|FOR|READTEXT|  
|AS|FOREIGN|RECONFIGURE|  
|ASC|FREETEXT|REFERENCES|  
|AUTHORIZATION|FREETEXTTABLE|РЕПЛИКАЦИЯ|  
|BACKUP|FROM|RESTORE|  
|BEGIN|FULL|RESTRICT|  
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
|DROP|OR|VALUES|  
|DUMP;|ORDER|VARYING|  
|ELSE|OUTER|VIEW|  
|END|OVER|WAITFOR|  
|ERRLVL|PERCENT|WHEN|  
|ESCAPE|PIVOT|WHERE|  
|EXCEPT|PLAN|WHILE|  
|EXEC|PRECISION|WITH|  
|EXECUTE|PRIMARY|WITHIN GROUP|  
|EXISTS|PRINT|WRITETEXT|  
|EXIT|PROC||
  
Следующая таблица содержит список зарезервированных слов, предназначенный исключительно для **Хранилища данных SQL Azure**.

|||
|-|-|
|**LABEL**||
  
 Кроме того, стандартом ISO определяется список зарезервированных ключевых слов. Избегайте применения зарезервированных ключевых слов ISO в качестве имен и идентификаторов объектов. Список зарезервированных ключевых слов ODBC, приведенный в следующей таблице, совпадает со списком зарезервированных ключевых слов ISO.  
  
> [!NOTE]  
>  Иногда список зарезервированных ключевых слов стандарта ISO более строгий, чем список [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а иногда менее строгий. Например, список зарезервированных ключевых слов ISO содержит **INT**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не должен выделять это слово как зарезервированное ключевое слово.  
  
 Зарезервированные ключевые слова языка [!INCLUDE[tsql](../../includes/tsql-md.md)] можно использовать для идентификаторов или имен баз данных или таких объектов базы данных, как таблицы, столбцы, представления и т. п. Для этого необходимо использовать идентификаторы, заключенные в кавычки, или идентификаторы с разделителями. Зарезервированные ключевые слова можно без ограничений использовать в качестве имен переменных или параметров хранимых процедур.  
  
## <a name="odbc-reserved-keywords"></a>Зарезервированные ключевые слова ODBC  
 Следующие слова зарезервированы для использования в вызовах функций ODBC. Эти слова не входят в минимальную грамматику SQL, поэтому, чтобы обеспечить совместимость с драйверами, поддерживающими базовую грамматику SQL, приложения должны избегать использования этих ключевых слов.  
  
 Следующая таблица содержит текущий список зарезервированных ключевых слов ODBC.  
  
||||  
|-|-|-|  
|**ABSOLUTE**|**EXEC**|**OVERLAPS**|  
|**ДЕЙСТВИЕ**|**EXECUTE**|**PAD**|  
|**ADA**|**EXISTS**|**PARTIAL**|  
|**ADD**|**EXTERNAL**|**PASCAL**|  
|**ALL**|**EXTRACT**|**POSITION**|  
|**ALLOCATE**|**FALSE**|**PRECISION**|  
|**ALTER**|**FETCH**|**PREPARE**|  
|**AND**|**FIRST**|**PRESERVE**|  
|**ANY**|**FLOAT**|**PRIMARY**|  
|**ARE**|**FOR**|**PRIOR**|  
|**Службы Analysis Services**|**FOREIGN**|**PRIVILEGES**|  
|**ASC**|**FORTRAN**|**PROCEDURE**|  
|**ASSERTION**|**FOUND**|**PUBLIC**|  
|**AT**|**FROM**|**READ**|  
|**AUTHORIZATION**|**ПОЛНОЕ**|**REAL**|  
|**AVG**|**GET**|**REFERENCES**|  
|**BEGIN**|**GLOBAL**|**RELATIVE**|  
|**BETWEEN**|**GO**|**RESTRICT**|  
|**BIT**|**GOTO**|**REVOKE**|  
|**BIT_LENGTH**|**GRANT**|**RIGHT**|  
|**BOTH**|**GROUP**|**ROLLBACK**|  
|**BY**|**HAVING**|**ROWS**|  
|**CASCADE**|**HOUR**|**SCHEMA**|  
|**CASCADED**|**IDENTITY**|**SCROLL**|  
|**CASE**|**IMMEDIATE**|**SECOND**|  
|**CAST**|**IN**|**SECTION**|  
|**CATALOG**|**INCLUDE**|**SELECT**|  
|**CHAR**|**INDEX**|**SESSION**|  
|**CHAR_LENGTH**|**INDICATOR**|**SESSION_USER**|  
|**CHARACTER**|**INITIALLY**|**SET**|  
|**CHARACTER_LENGTH**|**INNER**|**SIZE**|  
|**CHECK**|**INPUT**|**SMALLINT**|  
|**CLOSE**|**INSENSITIVE**|**SOME**|  
|**COALESCE**|**INSERT**|**SPACE**|  
|**COLLATE**|**INT**|**SQL**|  
|**COLLATION**|**INTEGER**|**SQLCA**|  
|**COLUMN**|**INTERSECT**|**SQLCODE**|  
|**COMMIT**|**INTERVAL**|**SQLERROR**|  
|**CONNECT**|**INTO**|**SQLSTATE**|  
|**CONNECTION**|**IS**|**SQLWARNING**|  
|**CONSTRAINT**|**ISOLATION**|**SUBSTRING**|  
|**CONSTRAINTS**|**JOIN**|**SUM**|  
|**CONTINUE**|**KEY**|**SYSTEM_USER**|  
|**CONVERT**|**LANGUAGE**|**TABLE**|  
|**CORRESPONDING**|**LAST**|**TEMPORARY**|  
|**COUNT**|**LEADING**|**THEN**|  
|**CREATE**|**LEFT**|**TIME**|  
|**CROSS**|**LEVEL**|**TIMESTAMP**|  
|**CURRENT**|**LIKE**|**TIMEZONE_HOUR**|  
|**CURRENT_DATE**|**LOCAL**|**TIMEZONE_MINUTE**|  
|**CURRENT_TIME**|**LOWER**|**Кому**|  
|**CURRENT_TIMESTAMP**|**MATCH**|**TRAILING**|  
|**CURRENT_USER**|**MAX**|**TRANSACTION**|  
|**CURSOR**|**MIN**|**TRANSLATE**|  
|**DATE**|**MINUTE**|**TRANSLATION**|  
|**DAY**|**MODULE**|**TRIM**|  
|**DEALLOCATE**|**MONTH**|**TRUE**|  
|**DEC**|**NAMES**|**UNION**|  
|**DECIMAL**|**NATIONAL**|**UNIQUE**|  
|**DECLARE**|**NATURAL**|**UNKNOWN**|  
|**DEFAULT**|**NCHAR**|**UPDATE**|  
|**DEFERRABLE**|**NEXT**|**UPPER**|  
|**DEFERRED**|**NO**|**USAGE**|  
|**DELETE**|**NONE**|**USER**|  
|**DESC**|**NOT**|**USING**|  
|**DESCRIBE**|**NULL**|**VALUE**|  
|**DESCRIPTOR**|**NULLIF**|**VALUES**|  
|**DIAGNOSTICS**|**NUMERIC**|**VARCHAR**|  
|**DISCONNECT**|**OCTET_LENGTH**|**VARYING**|  
|**DISTINCT**|**OF**|**VIEW**|  
|**DOMAIN**|**ON**|**WHEN**|  
|**DOUBLE**|**ONLY**|**WHENEVER**|  
|**DROP**|**OPEN**|**WHERE**|  
|**ELSE**|**OPTION**|**WITH**|  
|**END**|**OR**|**WORK**|  
|**END-EXEC**|**ORDER**|**WRITE**|  
|**ESCAPE**|**OUTER**|**YEAR**|  
|**EXCEPT**|**OUTPUT**|**ZONE**|  
|**EXCEPTION**|||  
  
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
|CURRENT_DEFAULT_TRANSFORM_GROUP|NO|TIMEZONE_MINUTE|  
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
|DEFERRED|OUTPUT|Значение|  
|DEPTH|PAD|VAR_POP|  
|DEREF|ПАРАМЕТР|VAR_SAMP|  
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
|FILTER|real|XMLEXISTS|  
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
 [SET QUOTED_IDENTIFIER (Transact-SQL)](../../t-sql/statements/set-quoted-identifier-transact-sql.md)   
 [Уровень совместимости инструкции ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
  
  
