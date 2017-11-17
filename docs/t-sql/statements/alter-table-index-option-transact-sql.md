---
title: "index_option (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/08/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- index_option
ms.assetid: 8a14f12d-2fbf-4036-b8b2-8db3354e0eb7
caps.latest.revision: 68
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: cd1366409f9fb0af271b26fad3b8b911f99acc06
ms.openlocfilehash: e7563f9fe992dcf4f9308cccbf11f6310b7925a7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/08/2017

---
# <a name="alter-table-indexoption-transact-sql"></a>Index_option ALTER TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Указывает набор параметров, которые могут быть применены на индекс, который является частью определения ограничения, созданные с помощью [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
{   
    PAD_INDEX = { ON | OFF }  
  | FILLFACTOR = fillfactor  
  | IGNORE_DUP_KEY = { ON | OFF }  
  | STATISTICS_NORECOMPUTE = { ON | OFF }  
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS = { ON | OFF }  
  | SORT_IN_TEMPDB = { ON | OFF }   
  | ONLINE = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
  | DATA_COMPRESSION = { NONE |ROW | PAGE | COLUMNSTORE | COLUMNSTORE_ARCHIVE }  
      [ ON PARTITIONS ( { <partition_number_expression> | <range> }   
      [ , ...n ] ) ]  
  | ONLINE = { ON [ ( <low_priority_lock_wait> ) ] | OFF }  
}  
  
<range> ::=   
<partition_number_expression> TO <partition_number_expression>  
  
<single_partition_rebuild__option> ::=  
{  
    SORT_IN_TEMPDB = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
  | DATA_COMPRESSION = {NONE | ROW | PAGE | COLUMNSTORE | COLUMNSTORE_ARCHIVE } }  
  | ONLINE = { ON [ ( <low_priority_lock_wait> ) ] | OFF }  
}  
  
<low_priority_lock_wait>::=  
{  
    WAIT_AT_LOW_PRIORITY ( MAX_DURATION = <time> [ MINUTES ] ,   
                           ABORT_AFTER_WAIT = { NONE | SELF | BLOCKERS } )   
}  
```  
  
## <a name="arguments"></a>Аргументы  
 PAD_INDEX  **=**  {ON | **OFF** }  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Определяет разреженность индекса. Значение по умолчанию — OFF.  
  
 ON  
 Процент свободного места, определяемый параметром FILLFACTOR, применяется к страницам индекса промежуточного уровня.  
  
 ОТКЛЮЧЕНИЕ или *fillfactor* не указан  
 Страницы промежуточного уровня заполнены почти в соответствии их производительным возможностям, на них остается место как минимум для одной строки максимального размера, какой только может иметь индекс, с заданным набором ключей на промежуточных страницах.  
  
 Значение коэффициента ЗАПОЛНЕНИЯ  **=**  *fillfactor*  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Определяет величину в процентах, показывающую насколько должен компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] заполнять конечный уровень каждой страницы индекса во время его создания и изменения. Заданное значение должно быть целым числом от 1 до 100. Значение по умолчанию равно 0.  
  
> [!NOTE]  
>  Значения коэффициента заполнения 0 и 100 одинаковы во всех отношениях.  
  
 IGNORE_DUP_KEY  **=**  {ON | **OFF** }  
 Определяет ответ на ошибку, случающуюся, когда операция вставки пытается вставить в уникальный индекс повторяющиеся значения ключа. Параметр IGNORE_DUP_KEY применяется только к операциям вставки, производимым после создания или перестроения индекса. Параметр не имеет значения при выполнении [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md), [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md), или [обновление](../../t-sql/queries/update-transact-sql.md). Значение по умолчанию — OFF.  
  
 ON  
 Предупреждение возникает при вставке повторяющиеся значения ключа в уникальный индекс. Сбой только строки, нарушающие ограничение уникальности.  
  
 OFF  
 Сообщение об ошибке возникает, если в уникальный индекс вставляются повторяющиеся значения ключа. Выполняется откат всей операции INSERT.  
  
 IGNORE_DUP_KEY не может быть присвоено значение ON для индексов, созданных на представлении, неуникальных индексов, XML-индексы, Пространственные индексы и отфильтрованных индексов.  
  
 Для просмотра значения IGNORE_DUP_KEY используйте [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).  
  
 Для обратной совместимости синтаксиса аргумент WITH IGNORE_DUP_KEY эквивалентен аргументу WITH IGNORE_DUP_KEY = ON.  
  
 STATISTICS_NORECOMPUTE  **=**  {ON | **OFF** }  
 Указывает, пересчитываются ли статистики. Значение по умолчанию — OFF.  
  
 ON  
 Устаревшие статистики не пересчитываются автоматически.  
  
 OFF  
 Автоматическое обновление статистических данных включено.  
  
 ALLOW_ROW_LOCKS  **=**  { **ON** | {OFF}  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Указывает, разрешена ли блокировка строк. Значение по умолчанию — ON.  
  
 ON  
 Блокировки строк допустимы при доступе к индексу. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] определяет, когда используются блокировки строки.  
  
 OFF  
 Блокировки строк не используются.  
  
 ALLOW_PAGE_LOCKS  **=**  { **ON** | {OFF}  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Указывает, разрешена ли блокировка страниц. Значение по умолчанию — ON.  
  
 ON  
 Блокировки страниц возможны при доступе к индексу. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] определяет, когда используются блокировки страниц.  
  
 OFF  
 Блокировки страниц не используются.  
  
 ПАРАМЕТР SORT_IN_TEMPDB  **=**  {ON | **OFF** }  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Указывает, следует ли сохранять результаты сортировки в **tempdb**. Значение по умолчанию — OFF.  
  
 ON  
 Промежуточные результаты сортировки, используемые для построения индекса, хранятся в **tempdb**. Это может уменьшить время, необходимое для создания индекса, если **tempdb** находится на разных наборах дисков пользовательской базы данных. Однако это увеличивает использование места на диске, которое используется при индексировании.  
  
 OFF  
 Промежуточные результаты сортировки хранятся в той же базе данных, где и индекс.  
  
 ONLINE  **=**  {ON | **OFF** }  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Определяет, будут ли базовые таблицы и связанные индексы доступны для запросов и изменения данных во время операций с индексами. Значение по умолчанию — OFF. REBUILD может выполняться как операция в режиме ONLINE.  
  
> [!NOTE]  
>  Уникальные некластеризованные индексы нельзя создавать в режиме в сети. К ним относятся индексы, создаваемые из-за ограничений UNIQUE и PRIMARY KEY.  
  
 ON  
 Долгосрочные блокировки таблицы не поддерживаются во время операций с индексами. Во время главной фазы операций с индексами только блокировка с намерением совмещаемого доступа (IS) удерживается в исходной таблице. Это включает запросы или обновления применительно к обрабатываемой базовой таблице и индексам. В начале операции совмещаемая блокировка (S) удерживается на исходном объекте в течение очень короткого времени. В конце операции на источнике на короткое время удерживается совмещаемая блокировка (S), если создается некластеризованный индекс. Если в режиме в сети создается или удаляется кластеризованный индекс и, если перестраивается кластеризованный или некластеризованный индекс, удерживается блокировка SCH-M (изменения схемы). Хотя блокировки индекса в сети — это короткие блокировки метаданных, но блокировка изменения схемы (Sch-M) должна ожидать завершения всех блокирующих транзакций для этой таблицы. Во время ожидания Sch-M блокирует все другие транзакции, ожидающие за этой блокировкой доступа к одной таблице. При создании индекса для временной локальной таблицы параметр ONLINE не может принимать значение ON.  
  
> [!NOTE]  
>  Перестроение индекса в сети можно задать *low_priority_lock_wait* параметров, описанных далее в этом разделе. *low_priority_lock_wait* управляет приоритетом блокировки S и Sch-M во время перестроения индекса в сети.  
  
 OFF  
 Блокировки таблиц применяются во время выполнения операций с индексами. Это предотвращает доступ к базовой таблице всех пользователей во время операции. Блокировку изменения схемы (Sch-M) в таблице получает операция с индексами вне сети, которая создает, перестраивает или удаляет кластеризованный индекс либо перестраивает или удаляет некластеризованный индекс. Это предотвращает доступ к базовой таблице всех пользователей во время операции. Операция с индексами вне сети, создающая некластеризованный индекс, получает совмещаемую блокировку (S) в таблице. Это запрещает проводить обновления базовой таблицы, но разрешает проводить операции чтения, например инструкции SELECT.  
  
 Дополнительные сведения см. в разделе [как Online операциях с индексом](../../relational-databases/indexes/how-online-index-operations-work.md).  
  
> [!NOTE]  
>  Операции с индексами в сети доступны не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 MAXDOP  **=**  *max_degree_of_parallelism*  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Переопределяет **максимальная степень параллелизма** параметр конфигурации в течение операции с индексами. Дополнительные сведения см. в разделе [Настройка параметра конфигурации сервера max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md). MAXDOP можно использовать для ограничения числа процессоров, используемых при параллельном выполнении планов. Максимальное число процессоров — 64.  
  
 *max_degree_of_parallelism* может быть:  
  
 - 1 — подавляет формирование параллельных планов.  
 - \>1 — ограничивает максимальное количество процессоров, используемых в параллельных операциях с индексами для заданного числа.  
 - 0 (по умолчанию) — используется действительное количество процессоров или меньше зависимости от текущей рабочей нагрузки системы.  
  
 Дополнительные сведения см. в статье [Настройка параллельных операций с индексами](../../relational-databases/indexes/configure-parallel-index-operations.md).  
  
> [!NOTE]  
>  Параллельные операции с индексами доступны не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 DATA_COMPRESSION  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Задает режим сжатия данных для указанной таблицы, номера секции или диапазона секций. Существуют следующие параметры выбора.  
  
 NONE  
 Таблица или указанные секции не сжимаются. Применяется только к таблицам rowstore, не относится к таблицам columnstore.  
  
 ROW  
 Таблицы или указанные секции сжимаются, используя сжатие строк. Применяется только к таблицам rowstore, не относится к таблицам columnstore.  
  
 PAGE  
 Таблицы или указанные секции сжимаются, используя сжатие страниц. Применяется только к таблицам rowstore, не относится к таблицам columnstore.  
  
 COLUMNSTORE  
 **Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Применяется только к таблицам columnstore. COLUMNSTORE указывает, что должна быть распакована секция, которая была упакована с помощью параметра COLUMNSTORE_ARCHIVE. При восстановлении данных индекса COLUMNSTORE по-прежнему будут сжаты с использованием сжатия columnstore, который используется для всех таблиц columnstore.  
  
 COLUMNSTORE_ARCHIVE  
 **Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Применяется только к таблицам columnstore, представляющим собой таблицы, которые хранятся с кластеризованным индексом columnstore. Дополнительные COLUMNSTORE_ARCHIVE сжатие указанной секции до меньшего размера. Это может использоваться для архивации или в других ситуациях, где требуется уменьшение объема пространства и допускается увеличение затрат времени на хранение и извлечение.  
  
 Дополнительные сведения о сжатии см. в разделе [сжатие данных](../../relational-databases/data-compression/data-compression.md).  
  
В СЕКЦИЯХ **(** { \<выражение_номера_секции > | \<диапазона >} [ **,**...  *n*  ] **)** **Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Указывает секции, к которым применяется параметр DATA_COMPRESSION. Если таблица не секционирована, аргумент ON PARTITIONS приведет к ошибке. Если не указано предложение ON PARTITIONS, параметр DATA_COMPRESSION применяется ко всем секциям секционированной таблицы.  
  
\<выражение_номера_секции > можно указать одним из следующих способов:  
  
-   Указать номер секции, например: ON PARTITIONS (2).  
-   Указать номера нескольких секций через запятые, например ON PARTITIONS (1, 5).  
-   Указать диапазоны и отдельные секции, например: ON PARTITIONS (2, 4, 6 TO 8).  
  
\<диапазон > можно указать как номера секций, разделенные словом TO, например: ON PARTITIONS (6 – 8).  
  
 Чтобы для разных секций задать разные типы сжатия данных, укажите параметр DATA_COMPRESSION несколько раз, например следующим образом.  
  
```sql  
--For rowstore tables  
REBUILD WITH   
(  
DATA_COMPRESSION = NONE ON PARTITIONS (1),   
DATA_COMPRESSION = ROW ON PARTITIONS (2, 4, 6 TO 8),   
DATA_COMPRESSION = PAGE ON PARTITIONS (3, 5)  
)  
  
--For columnstore tables  
REBUILD WITH   
(  
DATA_COMPRESSION = COLUMNSTORE ON PARTITIONS (1, 3, 5),   
DATA_COMPRESSION = COLUMNSTORE_ARCHIVE ON PARTITIONS (2, 4, 6 TO 8)  
)  
```  
  
**\<single_partition_rebuild__option >**  
 В большинстве случаев при перестроении индекса перестраиваются все секции секционированного индекса. Следующие параметры при применении к одному разделу не перестраивают все секции.  
  
-   SORT_IN_TEMPDB  
-   MAXDOP  
-   DATA_COMPRESSION  
  
**low_priority_lock_wait**  
 **Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Объект **КОММУТАТОР** или перестроение индекса в сети завершается сразу нет блокирующих операций для этой таблицы. *WAIT_AT_LOW_PRIORITY* указывает, что если **КОММУТАТОР** или немедленно невозможно выполнить операцию перестроения индекса в сети, он ожидает. Операция содержит блокировки с низким приоритетом, позволяя другим операциям, удерживающие блокировки, конфликтующие с инструкцией DDL, чтобы продолжить. Пропуск **WAIT AT LOW PRIORITY** параметр эквивалентен `WAIT_AT_LOW_PRIORITY ( MAX_DURATION = 0 minutes, ABORT_AFTER_WAIT = NONE)`.  
  
MAX_DURATION = *время* [**МИНУТ** ]  
 Время ожидания (целочисленное значение, указанное в минутах), **КОММУТАТОР** или блокировка перестроения индекса в сети, может быть запрошена только при выполнении команды DDL. Будет выполнена попытка немедленного запуска операции SWITCH или перестроения индекса в режиме «в сети». Если операция будет заблокирована для **MAX_DURATION** время один из **ABORT_AFTER_WAIT** выполняться действия. **MAX_DURATION** времени всегда находится в минутах и слово **МИНУТ** можно опустить.  
  
ABORT_AFTER_WAIT = [**NONE** | **SELF** | **ПРЕПЯТСТВИЯ** }]  
 None  
 По-прежнему **КОММУТАТОР** или индекса в сети операция перестроения без изменения приоритета блокировки (с помощью обычного приоритета).  
  
SELF  
 Выход из **КОММУТАТОР** или операция DDL перестроения индекса в сети, выполняющейся в данный момент без выполнения действий.  
  
BLOCKERS  
 Остановка всех пользовательских транзакций, которые в данный момент блокирующие **КОММУТАТОР** или, чтобы можно было продолжить данную операцию операцию DDL по перестроению индекса в сети.  
 Требуется ПРЕПЯТСТВИЯ **разрешение ALTER ANY CONNECTION** разрешение.  
  
## <a name="remarks"></a>Замечания  
 Полное описание параметров индекса см. в разделе [CREATE INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-index-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [column_constraint &#40; Transact-SQL &#41;](../../t-sql/statements/alter-table-column-constraint-transact-sql.md)   
 [computed_column_definition &#40; Transact-SQL &#41;](../../t-sql/statements/alter-table-computed-column-definition-transact-sql.md)   
 [table_constraint &#40; Transact-SQL &#41;](../../t-sql/statements/alter-table-table-constraint-transact-sql.md)  
  
 

