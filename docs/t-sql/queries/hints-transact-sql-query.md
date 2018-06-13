---
title: Указания запросов (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 05/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|queries
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Query_Hint_TSQL
- Query_TSQL
- Query
- Query Hint
- MAX_GRANT_PERCENT
- MAX_GRANT_PERCENT_TSQL
- MIN_GRANT_PERCENT
- MIN_GRANT_PERCENT_TSQL
- EXTERNALPUSHDOWN
- EXTERNALPUSHDOWN_TSQL
- NOLOCK_TSQL
- MAXDOP_TSQL
- USE_HINT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- REPORT PLAN query hint
- FORCE ORDER query hint
- HASH JOIN query hint
- query hints [SQL Server]
- OPTIMIZE FOR query hint
- FORCESCAN query hint
- RECOMPILE query hint
- MAXRECURSION query hint
- MERGE JOIN query hint
- HASH GROUP query hint
- KEEP PLAN query hint
- UNION query hint
- FORCESEEK query hint
- ORDER GROUP query hint
- LOOP JOIN query hint
- KEEPFIXED PLAN query hint
- FAST query hint
- MAXDOP query hint
- PARAMETERIZATION query hint
- hints [SQL Server], query
- JOIN query hint
- USE PLAN query hint
- EXPAND VIEWS query hint
- MAX_GRANT_PERCENT query hint
- MIN_GRANT_PERCENT query hint
- EXTERNALPUSHDOWN query hint
- USE HINT query hint
ms.assetid: 66fb1520-dcdf-4aab-9ff1-7de8f79e5b2d
caps.latest.revision: 136
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 484d0e3c9fccd0e65041665eef523dbf92311399
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34470295"
---
# <a name="hints-transact-sql---query"></a>Указания (Transact-SQL) — запросы
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Подсказки в запросе указывают, что для запроса должна использоваться заданная подсказка. Они влияют на все операторы в инструкции. Если в основном запросе используется операция UNION, только последний запрос, использующий ее, может содержать предложение OPTION. Подсказки в запросе указываются как часть предложения [OPTION](../../t-sql/queries/option-clause-transact-sql.md). Если оптимизатор запросов не формирует допустимый план из-за одного или нескольких указаний в запросе, возникает ошибка 8622.  
  
> [!CAUTION]  
> Поскольку оптимизатор запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обычно выбирает лучший план выполнения запроса, использовать подсказки рекомендуется только опытным разработчикам и администраторам баз данных в самом крайнем случае.  
  
 **Применимо к:**  
  
 [DELETE](../../t-sql/statements/delete-transact-sql.md)  
  
 [INSERT](../../t-sql/statements/insert-transact-sql.md)  
  
 [SELECT](../../t-sql/queries/select-transact-sql.md)  
  
 [UPDATE](../../t-sql/queries/update-transact-sql.md)  
  
 [MERGE](../../t-sql/statements/merge-transact-sql.md)  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<query_hint > ::=   
{ { HASH | ORDER } GROUP   
  | { CONCAT | HASH | MERGE } UNION   
  | { LOOP | MERGE | HASH } JOIN   
  | EXPAND VIEWS   
  | FAST number_rows   
  | FORCE ORDER   
  | { FORCE | DISABLE } EXTERNALPUSHDOWN  
  | IGNORE_NONCLUSTERED_COLUMNSTORE_INDEX  
  | KEEP PLAN   
  | KEEPFIXED PLAN  
  | MAX_GRANT_PERCENT = percent  
  | MIN_GRANT_PERCENT = percent  
  | MAXDOP number_of_processors   
  | MAXRECURSION number   
  | NO_PERFORMANCE_SPOOL   
  | OPTIMIZE FOR ( @variable_name { UNKNOWN | = literal_constant } [ , ...n ] )  
  | OPTIMIZE FOR UNKNOWN  
  | PARAMETERIZATION { SIMPLE | FORCED }  
  | RECOMPILE  
  | ROBUST PLAN   
  | USE HINT ( '<hint_name>' [ , ...n ] )
  | USE PLAN N'xml_plan'  | TABLE HINT ( exposed_object_name [ , <table_hint> [ [, ]...n ] ] )  
}  
  
<table_hint> ::=  
[ NOEXPAND ] {   
    INDEX ( index_value [ ,...n ] ) | INDEX = ( index_value )  
  | FORCESEEK [( index_value ( index_column_name [,... ] ) ) ]  
  | FORCESCAN  
  | HOLDLOCK   
  | NOLOCK   
  | NOWAIT  
  | PAGLOCK   
  | READCOMMITTED   
  | READCOMMITTEDLOCK   
  | READPAST   
  | READUNCOMMITTED   
  | REPEATABLEREAD   
  | ROWLOCK   
  | SERIALIZABLE   
  | SNAPSHOT  
  | SPATIAL_WINDOW_MAX_CELLS = integer  
  | TABLOCK   
  | TABLOCKX   
  | UPDLOCK   
  | XLOCK  
}  
```  
  
## <a name="arguments"></a>Аргументы  
 { HASH |ORDER } GROUP  
 Указывает, что агрегаты, описываемые в предложениях GROUP BY или DISTINCT запроса, должны использовать хэширование или упорядочивание.  
  
 { MERGE | HASH | CONCAT } UNION  
 Указывает, что все операции UNION выполняются слиянием, хэшированием или объединением наборов UNION. Если задано несколько указаний UNION, оптимизатор запросов выбирает наименее затратную стратегию из указанных.  
  
 { LOOP | MERGE | HASH } JOIN  
 Указывает, что все операции соединения во всем запросе выполняются с помощью рекомендаций LOOP JOIN, MERGE JOIN или HASH JOIN. Если задано больше одного указания соединения, оптимизатор запросов выбирает наименее затратную стратегию из допустимых.  
  
 Если в одном запросе указание соединения задано для определенной пары таблиц в предложении FROM, оно имеет приоритет в соединении двух таблиц, хотя также следует учитывать указания запросов. Таким образом, указание соединения для пары таблиц может только ограничивать выбор допустимых методов соединения для указания запроса. Дополнительные сведения см. в разделе [Указания соединений (Transact-SQL)](../../t-sql/queries/hints-transact-sql-join.md).  
  
 EXPAND VIEWS  
 Указывает, что выполняется разворачивание индексированных представлений и оптимизатор запросов не будет рассматривать индексированные представления как замену каким-либо частям запроса. Представление разворачивается при замене имени представления на определение представления в тексте запроса.  
  
 Это указание запроса виртуально запрещает прямое использование индексированных представлений и индексов для индексированных представлений в плане запроса.  
  
 Индексированное представление не разворачивается только в том случае, если на представление существует прямая ссылка в части SELECT запроса и определены подсказки WITH (NOEXPAND) или WITH (NOEXPAND, INDEX( *index_value* [ **,***...n* ] ) ). Дополнительные сведения о подсказке в запросе WITH (NOEXPAND) см. в разделе [FROM](../../t-sql/queries/from-transact-sql.md).  
  
 Действию этого указания подвержены только представления в части SELECT инструкций, включая находящиеся в инструкциях INSERT, UPDATEMERGE и DELETE.  
  
 FAST *number_rows*  
 Указывает, что запрос оптимизирован для быстрого получения первых *number_rows*. Это неотрицательное целое число. После возвращения первых *number_rows* строк запрос продолжает выполняться и возвращает полный результирующий набор.  
  
 FORCE ORDER  
 Указывает, что при оптимизации запроса сохраняется порядок соединения, заданный синтаксисом запроса. Использование подсказки FORCE ORDER не влияет на возможный реверс ролей в оптимизаторе запросов.  
  
> [!NOTE]  
> Инструкция MERGE получает доступ вначале к исходной таблице, затем к целевой в порядке соединения, принятом по умолчанию, если не задано предложение WHEN SOURCE NOT MATCHED. Если указать FORCE ORDER, сохраняется поведение по умолчанию.  
  
 { FORCE | DISABLE } EXTERNALPUSHDOWN  
 Принудительная передача или отключение передачи вычислений соответствующих выражений в Hadoop. Применяется только к запросам, использующим PolyBase. Не выполняет отправку в хранилище Azure.  
  
 KEEP PLAN  
 Заставляет оптимизатор запросов снизить приблизительный порог повторной компиляции для запроса. Предполагаемое пороговое значение повторной компиляции — это точка, в которой запрос автоматически перекомпилируется, если в таблице при выполнении инструкций UPDATE, DELETE или INSERT изменилось ожидаемое количество индексированных столбцов. Указывая подсказку KEEP PLAN, убедитесь, что запрос не будет часто перекомпилирован при выполнении множественных обновлений в таблице.  
  
 KEEPFIXED PLAN  
 Принуждает оптимизатор запросов не перекомпилировать запрос при изменении статистики. Указывая подсказку KEEPFIXED PLAN, убедитесь, что запрос будет перекомпилирован только при изменении схемы базовых таблиц или если по отношению к ним выполнена процедура **sp_recompile**.  
  
 IGNORE_NONCLUSTERED_COLUMNSTORE_INDEX  
 **Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Предотвращает использование в запросе некластеризованного индекса columnstore с оптимизацией для памяти. Если в запросе содержится указание запроса, исключающее использование индекса columnstore, а также указание индекса для использования индекса columnstore, то данные указания будут конфликтовать между собой, и запрос вернет ошибку.  
  
 MAX_GRANT_PERCENT = *percent*  
 Максимальный объем предоставленной памяти в PERCENT. Запрос гарантированно не превышает это ограничение. Реальное ограничение может быть ниже, если указано более низкое значение параметра регулятора ресурсов. Допустимые значения — от 0 до 100.  
  
**Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 MIN_GRANT_PERCENT = *percent*  
 Минимальный размер предоставления памяти в PERCENT = % от ограничения по умолчанию. Запрос гарантированно получает MAX(required memory, min grant), поскольку для запуска запроса требуется по меньшей мере необходимый объем памяти. Допустимые значения — от 0 до 100.  
  
**Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 MAXDOP *number*  
 **Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Переопределяет параметр конфигурации **max degree of parallelism** хранимой процедуры **sp_configure** и регулятора ресурсов для запросов, в которых указывается этот параметр. Указание запроса MAXDOP может превысить значение, настроенное с помощью sp_configure. Если MAXDOP превышает значение, настроенное с помощью Resource Governor, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] использует значение MAXDOP из Resource Governor, как описано в статье [ALTER WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/alter-workload-group-transact-sql.md). Все семантические правила, используемые параметром конфигурации **max degree of parallelism**, применимы при использовании подсказки в запросе MAXDOP. Дополнительные сведения см. в разделе [Настройка параметра конфигурации сервера max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md).  
  
> [!WARNING]     
> Если значение MAXDOP равно нулю, сервер выбирает максимальную степень параллелизма.  
  
 MAXRECURSION *number*     
 Указывает максимальное число рекурсий, допустимых для данного запроса. *number* представляет собой неотрицательное целое число от 0 до 32 767. Если указано значение 0, ограничения не применяются. Если этот параметр не указан, ограничение по умолчанию равно 100.  
  
 Если в процессе выполнения запроса достигнуто указанное число или число по умолчанию для подсказки MAXRECURSION, выполнение запроса завершается и возвращается ошибка.  
  
 Из-за этой ошибки все действия инструкции откатываются. Если это инструкция SELECT, может быть возвращена часть результатов или не возвращено ничего. Любые возвращенные частичные результаты могут не включать всех строк на рекурсивных уровнях, расположенных за указанным максимальным уровнем рекурсии.  
  
 Дополнительные сведения см. в разделе [WITH common_table_expression (Transact-SQL)](../../t-sql/queries/with-common-table-expression-transact-sql.md).     
  
 NO_PERFORMANCE_SPOOL    
 **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Запрещает добавление оператора очередей в планы запроса (за исключением тех планов, когда очередь необходима для гарантированного обеспечения допустимой семантики обновления). В некоторых сценариях оператор очередей может снизить производительность. Например, очередь использует базу данных tempdb, и за нее может возникнуть состязание при наличии множества параллельных запросов, выполняющихся с операциями очереди.  
  
 OPTIMIZE FOR ( *@variable_name* { UNKNOWN | = *literal_constant }* [ **,** ...*n* ] )     
 Указывает оптимизатору запросов, что при компиляции и оптимизации запросов нужно использовать конкретное значение для локальной переменной. Значение используется только в процессе оптимизации запроса, но не в процессе выполнения.  
  
 *@variable_name*  
 Имя локальной переменной, используемой в запросе, которой может быть присвоено значение для использования с указанием запроса OPTIMIZE FOR.  
  
 *UNKNOWN*  
 Указывает, что оптимизатор запросов использует статистические данные вместо начального значения, чтобы определить значение локальной переменной при оптимизации запросов.  
  
 *literal_constant*  
 Значение константы-литерала, присваиваемое *@variable_name* для использования совместно с указанием запроса OPTIMIZE FOR. *literal_constant* используется только в процессе оптимизации запроса, но не используется как значение *@variable_name* во время выполнения запроса. *literal_constant* может быть любым системным типом данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], который может быть выражен как константа-литерал. Тип данных значения *literal_constant* должен неявно приводиться к типу данных, на который ссылается аргумент *@variable_name* в запросе.  
  
 Подсказка OPTIMIZE FOR может использоваться для отмены определения параметров по умолчанию в оптимизаторе или при создании структуры плана. Дополнительные сведения см. в разделе [Перекомпиляция хранимой процедуры](../../relational-databases/stored-procedures/recompile-a-stored-procedure.md).  
  
 OPTIMIZE FOR UNKNOWN  
 Если запрос скомпилирован и оптимизирован, предписывает оптимизатору запросов использовать статистические данные вместо начальных значений для всех локальных переменных, включая параметры, созданные с принудительной параметризацией.  
  
 Если подсказки OPTIMIZE FOR @variable_name = *literal_constant* и OPTIMIZE FOR UNKNOWN используются в одном указании запроса, оптимизатор запросов будет использовать аргумент *literal_constant*, указанный для конкретного значения, и UNKNOWN — для оставшихся значений переменных. Значения используются только в процессе оптимизации запроса, но не в процессе выполнения.  
  
 PARAMETERIZATION { SIMPLE | FORCED }     
 Указывает правила параметризации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которые оптимизатор запросов применяет к запросу при его компиляции.  
  
> [!IMPORTANT]  
> Указание запроса PARAMETERIZATION может быть задано только в структуре плана для переопределения текущего значения параметра SET базы данных PARAMETERIZATION. Оно не может быть определено напрямую в запросе.    
> Дополнительные сведения см. в разделе [Указание механизма параметризации запросов с помощью структур плана](../../relational-databases/performance/specify-query-parameterization-behavior-by-using-plan-guides.md).
  
 Значение SIMPLE дает оптимизатору запросов указание использовать простую параметризацию. Значение FORCED предписывает оптимизатору запросов использовать принудительную параметризацию. Дополнительные сведения см. в разделах [Принудительная параметризация](../../relational-databases/query-processing-architecture-guide.md#ForcedParam) и [Простая параметризация](../../relational-databases/query-processing-architecture-guide.md#SimpleParam) в руководстве по архитектуре обработки запросов.  
  
 RECOMPILE  
 Указывает компоненту [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] отбросить план, сформированный после выполнения запроса, заставляя оптимизатор запросов перекомпилировать план запроса при следующем выполнении этого запроса. Без указания подсказки RECOMPILE компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] кэширует планы запросов и использует их повторно. При компиляции планов запроса указание запроса RECOMPILE использует текущие значения всех локальных переменных в запросе и, если запрос находится внутри хранимой процедуры, текущие значения для всех параметров.  
  
 Подсказка RECOMPILE — это полезная альтернатива созданию хранимых процедур, использующих предложение WITH RECOMPILE, в тех случаях, когда нужно перекомпилировать лишь часть запросов в хранимой процедуре, а не всю хранимую процедуру. Дополнительные сведения см. в разделе [Перекомпиляция хранимой процедуры](../../relational-databases/stored-procedures/recompile-a-stored-procedure.md). Подсказка RECOMPILE также полезна для создания структур планов.  
  
 ROBUST PLAN  
 Заставляет оптимизатор запросов использовать план, который работает со строками наибольшего потенциального размера, возможно, с потерей производительности. При обработке запроса промежуточным таблицам и операторам может понадобиться сохранять и обрабатывать строки, которые шире, чем любые из входных строк. Строки могут быть настолько широки, что иногда некоторые операторы не смогут их обработать. Когда это происходит, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] возвращает ошибку при выполнении запроса. С помощью подсказки ROBUST PLAN оптимизатору запросов дается указание не выбирать ни один из планов запросов, который может вызвать проблему.  
  
 Если такой план невозможен, оптимизатор запросов возвращает ошибку сразу, не откладывая обнаружение ошибок на момент выполнения запроса. Строки могут содержать столбцы переменной длины; компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] позволяет указать для строк максимальный потенциальный размер, при превышении которого компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] может не суметь обработать их. В основном, несмотря на максимальный потенциальный размер, приложение сохраняет строки, имеющие актуальные размеры с ограничениями, которые компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] может обработать. Если компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] встречает слишком длинную строку, возвращается ошибка выполнения.  
 
<a name="use_hint"></a> USE HINT ( **'***hint_name***'** )    
 **Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] с пакетом обновления 1 (SP1)) и [!INCLUDE[ssSDS](../../includes/sssds-md.md)].
 
 Предоставляет одно или несколько дополнительных указаний обработчику запросов в соответствии с именем подсказки **в одиночных кавычках**.   

 Поддерживаются следующие имена подсказок:    
 
*  'DISABLE_OPTIMIZED_NESTED_LOOP'  
 Заставляет обработчик запросов не использовать операцию сортировки (сортировки пакетов) для оптимизации соединений вложенного цикла при формировании плана запроса. Это эквивалентно [флагу трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2340.
*  'FORCE_LEGACY_CARDINALITY_ESTIMATION'  
 Заставляет оптимизатор запросов использовать модель [оценки кратности](../../relational-databases/performance/cardinality-estimation-sql-server.md) для [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более ранних версий. Это эквивалентно [флагу трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 9481 или параметру [Конфигурация области баз данных](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) LEGACY_CARDINALITY_ESTIMATION=ON.
*  'ENABLE_QUERY_OPTIMIZER_HOTFIXES'  
 Включает исправления в оптимизаторе запросов, выпущенные в накопительных пакетах обновления и пакетах обновления SQL Server. Это эквивалентно [флагу трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 4199 или параметру [Конфигурация области баз данных](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) QUERY_OPTIMIZER_HOTFIXES=ON.
*  'DISABLE_PARAMETER_SNIFFING'  
 Указывает оптимизатору запросов использовать распространение среднего значения данных во время компиляции запроса с одним или несколькими параметрами, что делает план запроса независимым от значения параметра, которое сначала использовалось при компиляции запроса. Это эквивалентно [флагу трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 4136 или параметру [Конфигурация области баз данных](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) PARAMETER_SNIFFING=OFF.
*  'ASSUME_MIN_SELECTIVITY_FOR_FILTER_ESTIMATES'  
 Заставляет SQL Server создавать план с минимальной избирательностью при оценке и предикатов AND для фильтров, которые будут применяться при корреляции. Это эквивалентно [флагу трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 4137 при использовании модели оценки кратности в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более ранних версиях и имеет тот же эффект, что и при использовании [флага трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 9471 с моделью оценки кратности в [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] или более поздних версиях.
*  'DISABLE_OPTIMIZER_ROWGOAL'  
 Заставляет SQL Server создать план без использования корректировок цели строки с запросами, содержащими ключевые слова TOP, OPTION (FAST N), IN или EXISTS. Это эквивалентно [флагу трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 4138.
*  'ENABLE_HIST_AMENDMENT_FOR_ASC_KEYS'  
 Позволяет использовать автоматически созданную быструю статистику (поправку к гистограмме) для любого начального столбца индекса, для которого требуется оценить кратность. Гистограмма, используемая для оценки кратности, будет так откорректирована во время компиляции запроса, чтобы учитывать фактическое максимальное или минимальное значение этого столбца. Это эквивалентно [флагу трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 4139. 
*  'ASSUME_JOIN_PREDICATE_DEPENDS_ON_FILTERS'  
 Побуждает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создать план запроса с допущением простого вложения вместо допущения базового вложения по умолчанию для соединений в модели [оценки кратности](../../relational-databases/performance/cardinality-estimation-sql-server.md) оптимизатора запросов версии [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] или более поздних. Это эквивалентно [флагу трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 9476. 
*  'FORCE_DEFAULT_CARDINALITY_ESTIMATION'    
 Заставляет оптимизатор запросов использовать модель [оценки кратности](../../relational-databases/performance/cardinality-estimation-sql-server.md), которая соответствует текущему уровню совместимости базы данных. Используйте это указание для переопределения параметра [Конфигурация области баз данных](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) LEGACY_CARDINALITY_ESTIMATION=ON или [флаг трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 9481.
*  "DISABLE_INTERLEAVED_EXECUTION_TVF"   
 Отключает выполнение с чередованием для функций с табличным значением с несколькими инструкциями. Дополнительные сведения см. в разделе [Выполнение с чередованием для функций с табличным значением с несколькими инструкциями](../../relational-databases/performance/adaptive-query-processing.md#interleaved-execution-for-multi-statement-table-valued-functions).
*  "DISABLE_BATCH_MODE_MEMORY_GRANT_FEEDBACK"     
 Отключает обратную связь по временно предоставляемому буферу памяти в пакетном режиме. Дополнительные сведения см. в разделе [Обратная связь по временно предоставляемому буферу памяти в пакетном режиме](../../relational-databases/performance/adaptive-query-processing.md#batch-mode-memory-grant-feedback).
*  "DISABLE_BATCH_MODE_ADAPTIVE_JOINS"     
 Отключает адаптивные соединения в пакетном режиме. Дополнительные сведения см. в разделе [Адаптивные соединения в пакетном режиме](../../relational-databases/performance/adaptive-query-processing.md#batch-mode-adaptive-joins).
 
> [!TIP]
> В именах указаний учитывается регистр.
  
  Список всех поддерживаемых имен USE HINT можно запросить с помощью динамического административного представления [sys.dm_exec_valid_use_hints](../../relational-databases/system-dynamic-management-views/sys-dm-exec-valid-use-hints-transact-sql.md).    
  
> [!IMPORTANT] 
> Некоторые указания USE HINT могут конфликтовать с флагами трассировки, включенными на глобальном уровне или уровне сеанса, или параметрами конфигурации области баз данных. В этом случае приоритет всегда имеет указание уровня запроса (USE HINT). Если USE HINT конфликтует с другим указанием запроса или флагом трассировки, включенным на уровне запроса (например, с помощью QUERYTRACEON), при попытке выполнить запрос [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выведет ошибку. 

 USE PLAN N **'***xml_plan***'**     
 Принуждает оптимизатор запросов использовать существующий план запроса для запроса, определенного параметром **'***xml_plan***'**. Подсказку USE PLAN нельзя указывать в инструкциях INSERT, UPDATE MERGE и DELETE.  
  
TABLE HINT **(***exposed_object_name* [ **,** \<table_hint> [ [**,** ]...*n* ] ] **)** Применяет заданное табличное указание к таблице или представлению, которое соответствует *exposed_object_name*. Табличные указания рекомендуется использовать в качестве подсказок в запросах только в контексте [структуры плана](../../relational-databases/performance/plan-guides.md).  
  
 Аргумент *exposed_object_name* может представлять одну из следующих ссылок.  
  
-   Если в предложении [FROM](../../t-sql/queries/from-transact-sql.md) запроса используется псевдоним таблицы или представления, этим псевдонимом является *exposed_object_name*.  
  
-   Если псевдоним не используется, *exposed_object_name* является точным соответствием таблицы или представления, на которые ссылается предложение FROM. Например, если в таблице или представлении имеется ссылка с двухкомпонентным именем, аргумент *exposed_object_name* представляет собой это двухкомпонентное имя.  
  
 Если аргумент *exposed_object_name* задан без указания табличной подсказки, все индексы, заданные в запросе как часть табличной подсказки, не учитываются, а использование индексов определяется оптимизатором запросов. Этот метод можно использовать для устранения влияния табличного указания INDEX, если невозможно изменить первоначальный запрос. См. пример К.  
  
**\<table_hint> ::=** { [ NOEXPAND ] { INDEX ( *index_value* [ ,...*n* ] ) | INDEX = ( *index_value* ) | FORCESEEK [**(***index_value***(***index_column_name* [**,**... ] **))** ]| FORCESCAN | HOLDLOCK | NOLOCK | NOWAIT | PAGLOCK | READCOMMITTED | READCOMMITTEDLOCK | READPAST | READUNCOMMITTED | REPEATABLEREAD | ROWLOCK | SERIALIZABLE | SNAPSHOT | SPATIAL_WINDOW_MAX_CELLS | TABLOCK | TABLOCKX | UPDLOCK | XLOCK } Является табличным указанием, применяемым в качестве указания запроса к таблице или представлению, которое соответствует *exposed_object_name*. Описание этих указаний см. в разделе [Табличные указания (Transact-SQL)](../../t-sql/queries/hints-transact-sql-table.md).  
  
 Табличные указания, за исключением INDEX, FORCESCAN и FORCESEEK, не могут использоваться как указания запроса, кроме тех случаев, когда в запросе уже содержится предложение WITH, задающее табличное указание. Дополнительные сведения см. в подразделе "Примечания".  
  
> [!CAUTION] 
> Указание FORCESEEK с параметрами ограничивает число планов, которые могут быть использованы оптимизатором, в отличие от указания FORCESEEK без параметров. Из-за этого может чаще возникать ошибка "Невозможно сформировать план". В будущих выпусках внутренние изменения оптимизатора могут привести к увеличению числа этих планов.  
  
## <a name="remarks"></a>Remarks  
 Указания запросов нельзя задавать в инструкции INSERT, кроме случая, когда внутри инструкции используется предложение SELECT.  
  
 Указания запросов можно задавать только в запросах верхнего уровня, но не во вложенных запросах. Если табличная подсказка задана в качестве подсказки в запросе, ее можно указать в запросе верхнего уровня или во вложенном запросе. Тем не менее значение аргумента *exposed_object_name* в предложении TABLE HINT должно точно соответствовать видимому имени в запросе или вложенном запросе.  
  
## <a name="specifying-table-hints-as-query-hints"></a>Определение табличных указаний как указаний запроса  
 Табличные указания INDEX, FORCESCAN или FORCESEEK рекомендуется использовать в качестве указаний запроса только в контексте [структуры плана](../../relational-databases/performance/plan-guides.md). Структуры планов полезны, если нельзя изменить первоначальный запрос, например потому, что он является приложением стороннего разработчика. Указания запроса, заданные в структуре планов, добавляются к запросу перед его компиляцией и оптимизацией. В автоматизированных запросах предложение TABLE HINT используется только при тестировании инструкций структуры планов. Для всех других нерегламентированных запросов рекомендуется задавать эти указания только как табличные.  
  
 Табличные указания INDEX, FORCESCAN и FORCESEEK, определенные в качестве указаний запроса, допустимы для следующих объектов:  
  
-   Таблицы  
-   Представления  
-   Индексированные представления  
-   Обобщенные табличные выражения (подсказку необходимо указывать в инструкции SELECT, результирующий набор которой заполняет обобщенное табличное выражение)  
-   Динамические административные представления  
-   Именованные вложенные запросы  
  
Табличные указания INDEX, FORCESCAN и FORCESEEK могут быть заданы как указания запроса для запроса, у которого нет существующих табличных указаний. Кроме того, они могут использоваться для замены соответственно существующих указаний INDEX, FORCESCAN или FORCESEEK в таком запросе. Табличные указания, за исключением INDEX, FORCESCAN и FORCESEEK, не могут использоваться как указания запроса, кроме тех случаев, когда в запросе уже содержится предложение WITH, задающее табличное указание. В этом случае, чтобы сохранить семантику запроса, необходимо также задать соответствующее табличное указание в качестве указания запроса, задав в предложении OPTION ключевое слово TABLE HINT. Например, если запрос содержит табличное указание NOLOCK, то предложение OPTION в параметре **@hints** руководства плана также должно содержать указание NOLOCK. См. пример Л. Если задать табличное указание, отличное от INDEX, FORCESCAN или FORCESEEK, с использованием TABLE HINT в предложении OPTION без совпадающего указания запроса (или наоборот), будет возвращена ошибка 8702, показывающая, что предложение OPTION может вызвать изменение в семантике запроса, и запрос завершится с ошибкой.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-merge-join"></a>A. Использование MERGE JOIN  
 В следующем примере операция JOIN в запросе выполняется с помощью MERGE JOIN. В этом примере используется база данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
SELECT *   
FROM Sales.Customer AS c  
INNER JOIN Sales.CustomerAddress AS ca ON c.CustomerID = ca.CustomerID  
WHERE TerritoryID = 5  
OPTION (MERGE JOIN);  
GO    
```  
  
### <a name="b-using-optimize-for"></a>Б. Использование OPTIMIZE FOR  
 В следующем примере оптимизатору запросов предписывается использовать значение `'Seattle'` для локальной переменной `@city_name` и использовать статистические данные для определения локальной переменной `@postal_code` при оптимизации запроса. В этом примере используется база данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
DECLARE @city_name nvarchar(30);  
DECLARE @postal_code nvarchar(15);  
SET @city_name = 'Ascheim';  
SET @postal_code = 86171;  
SELECT * FROM Person.Address  
WHERE City = @city_name AND PostalCode = @postal_code  
OPTION ( OPTIMIZE FOR (@city_name = 'Seattle', @postal_code UNKNOWN) );  
GO  
```  
  
### <a name="c-using-maxrecursion"></a>В. Использование MAXRECURSION  
 Подсказка MAXRECURSION может использоваться для предотвращения входа в бесконечный цикл из-за неверно сформированного рекурсивного обобщенного табличного выражения. В следующем примере преднамеренно формируется бесконечный цикл и используется указание MAXRECURSION для ограничения числа уровней рекурсии двумя. В этом примере используется база данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
--Creates an infinite loop  
WITH cte (CustomerID, PersonID, StoreID) AS  
(  
    SELECT CustomerID, PersonID, StoreID  
    FROM Sales.Customer  
    WHERE PersonID IS NOT NULL  
  UNION ALL  
    SELECT cte.CustomerID, cte.PersonID, cte.StoreID  
    FROM cte   
    JOIN  Sales.Customer AS e   
        ON cte.PersonID = e.CustomerID  
)  
--Uses MAXRECURSION to limit the recursive levels to 2  
SELECT CustomerID, PersonID, StoreID  
FROM cte  
OPTION (MAXRECURSION 2);  
GO  
```  
  
 После исправления ошибки в коде подсказка MAXRECURSION больше не нужна.  
  
### <a name="d-using-merge-union"></a>Г. Использование MERGE UNION  
 В следующем примере используется указание запроса MERGE UNION. В этом примере используется база данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
SELECT *  
FROM HumanResources.Employee AS e1  
UNION  
SELECT *  
FROM HumanResources.Employee AS e2  
OPTION (MERGE UNION);  
GO  
```  
  
### <a name="e-using-hash-group-and-fast"></a>Д. Использование HASH GROUP и FAST  
 В следующем примере используется указания запросов HASH GROUP и FAST. В этом примере используется база данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
SELECT ProductID, OrderQty, SUM(LineTotal) AS Total  
FROM Sales.SalesOrderDetail  
WHERE UnitPrice < $5.00  
GROUP BY ProductID, OrderQty  
ORDER BY ProductID, OrderQty  
OPTION (HASH GROUP, FAST 10);  
GO    
```  
  
### <a name="f-using-maxdop"></a>Е. Использование MAXDOP  
 В следующем примере используется указание запроса MAXDOP. В этом примере используется база данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```sql  
SELECT ProductID, OrderQty, SUM(LineTotal) AS Total  
FROM Sales.SalesOrderDetail  
WHERE UnitPrice < $5.00  
GROUP BY ProductID, OrderQty  
ORDER BY ProductID, OrderQty  
OPTION (MAXDOP 2);    
GO
```  
  
### <a name="g-using-index"></a>Ж. Использование INDEX  
 В следующем примере используется указание в запросе INDEX. В первом примере задан один индекс. Во втором примере указывается несколько индексов для одной табличной ссылки. В обоих примерах в связи с использованием указания INDEX по отношению к таблице с псевдонимом необходимо указать тот же псевдоним в предложении TABLE HINT в качестве имени объекта, к которому предоставляется доступ. В этом примере используется база данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
EXEC sp_create_plan_guide   
    @name = N'Guide1',   
    @stmt = N'SELECT c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e   
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 2;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT(e, INDEX (IX_Employee_ManagerID)))';  
GO  
EXEC sp_create_plan_guide   
    @name = N'Guide2',   
    @stmt = N'SELECT c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e  
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 2;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT(e, INDEX(PK_Employee_EmployeeID, IX_Employee_ManagerID)))';  
GO    
```  
  
### <a name="h-using-forceseek"></a>З. Использование FORCESEEK  
 В следующем примере используется табличное указание FORCESEEK. Поскольку указание INDEX применяется к таблице с двухкомпонентным именем, в предложении TABLE HINT необходимо задать двухкомпонентное имя, совпадающее с именем видимого объекта. В этом примере используется база данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
EXEC sp_create_plan_guide   
    @name = N'Guide3',   
    @stmt = N'SELECT c.LastName, c.FirstName, HumanResources.Employee.Title  
              FROM HumanResources.Employee  
              JOIN Person.Contact AS c ON HumanResources.Employee.ContactID = c.ContactID  
              WHERE HumanResources.Employee.ManagerID = 3  
              ORDER BY c.LastName, c.FirstName;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT( HumanResources.Employee, FORCESEEK))';  
GO    
```  
  
### <a name="i-using-multiple-table-hints"></a>И. Использование нескольких табличных указаний  
 В следующем примере к одной таблице применяется указание INDEX, а к другой — указание FORCESEEK. В этом примере используется база данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
EXEC sp_create_plan_guide   
    @name = N'Guide4',   
    @stmt = N'SELECT e.ManagerID, c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e   
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 3;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT (e, INDEX( IX_Employee_ManagerID))   
                       , TABLE HINT (c, FORCESEEK))';  
GO  
```  
  
### <a name="j-using-table-hint-to-override-an-existing-table-hint"></a>К. Использование TABLE HINT для замещения существующего табличного указания  
 В следующем примере показано, как использовать указание TABLE HINT без задания указания для переопределения поведения указания таблицы INDEX, заданного в предложении FROM запроса. В этом примере используется база данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
EXEC sp_create_plan_guide   
    @name = N'Guide5',   
    @stmt = N'SELECT e.ManagerID, c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e WITH (INDEX (IX_Employee_ManagerID))  
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 3;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT(e))';  
GO    
```  
  
### <a name="k-specifying-semantics-affecting-table-hints"></a>Л. Определение табличных указаний, влияющих на семантику  
 В следующем примере показаны два табличных указания в запросе: NOLOCK, которое изменяет семантику, и INDEX, которое не изменяет семантику. Чтобы сохранить семантику запроса, указание NOLOCK задается в предложении OPTIONS структуры плана. В дополнение к указанию NOLOCK заданы указания INDEX и FORCESEEK, а также заменено не влияющее на семантику указание INDEX в запросе при компиляции и оптимизации инструкции. В этом примере используется база данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
EXEC sp_create_plan_guide   
    @name = N'Guide6',   
    @stmt = N'SELECT c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e   
                   WITH (NOLOCK, INDEX (PK_Employee_EmployeeID))  
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 3;',  
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT (e, INDEX(IX_Employee_ManagerID), NOLOCK, FORCESEEK))';  
GO    
```  
  
 В следующем примере показан альтернативный метод сохранения семантики запроса, позволяющий оптимизатору выбрать другой индекс, в отличие от заданного в табличном указании. Это делается путем задания указания NOLOCK в предложении OPTIONS (поскольку оно изменяет семантику) и указания ключевого слова TABLE HINT только со ссылкой на таблицу, без указания INDEX. В этом примере используется база данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
EXEC sp_create_plan_guide   
    @name = N'Guide7',   
    @stmt = N'SELECT c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e   
                   WITH (NOLOCK, INDEX (PK_Employee_EmployeeID))  
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 2;',  
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT (e, NOLOCK))';  
GO  
```  
### <a name="l-using-use-hint"></a>М. Указание USE HINT  
 В следующем примере используются указания запросов RECOMPILE и USE HINT. В этом примере используется база данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
**Применимо к**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
```sql  
SELECT * FROM Person.Address  
WHERE City = 'SEATTLE' AND PostalCode = 98104
OPTION (RECOMPILE, USE HINT ('ASSUME_MIN_SELECTIVITY_FOR_FILTER_ESTIMATES', 'DISABLE_PARAMETER_SNIFFING')); 
GO  
```  
    
## <a name="see-also"></a>См. также  
 [Указания (Transact-SQL)](../../t-sql/queries/hints-transact-sql.md)   
 [sp_create_plan_guide (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sp_control_plan_guide (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql.md)  
 [Флаги трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)
  
  
