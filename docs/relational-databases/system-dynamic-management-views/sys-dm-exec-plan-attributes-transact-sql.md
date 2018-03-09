---
title: "sys.dm_exec_plan_attributes (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 10/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_plan_attributes_TSQL
- dm_exec_plan_attributes_TSQL
- dm_exec_plan_attributes
- sys.dm_exec_plan_attributes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_plan_attributes dynamic management function
ms.assetid: dacf3ab3-f214-482e-aab5-0dab9f0a3648
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c9a90a964bd8c1fce911e62ac9081b47d349e0a5
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmexecplanattributes-transact-sql"></a>sys.dm_exec_plan_attributes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по одной строке для каждого атрибута плана, ассоциированного с планом, заданным посредством дескриптора плана. Функция с табличным значением может использоваться для получения подробных сведений об определенном плане, например значения ключа кэша или количество одновременных текущих выполнений плана.  
  
> [!NOTE]  
>  Некоторые из сведений, возвращаемых этой функцией, сопоставляется [sys.syscacheobjects](../../relational-databases/system-compatibility-views/sys-syscacheobjects-transact-sql.md) представлением обратной совместимости.

## <a name="syntax"></a>Синтаксис  
```  
sys.dm_exec_plan_attributes ( plan_handle )  
```  
  
## <a name="arguments"></a>Аргументы  
 *plan_handle*  
 Уникально идентифицирует план запроса для запущенного пакета, план которого хранится в кэше планов. *plan_handle* — **varbinary(64)**. Дескриптор плана можно получить из [sys.dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md) динамическое административное представление.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|атрибут|**varchar(128)**|Имя атрибута, ассоциированного с этим планом. В таблице немедленно ниже перечислены возможных атрибутах, их типы данных и их описания.|  
|value|**sql_variant**|Значение атрибута, ассоциированного с этим планом.|  
|is_cache_key|**бит**|Указывает, используется ли атрибут в качестве части ключа уточняющего запроса к кэшу для плана.|  

Из приведенной выше таблицы **атрибут** может принимать следующие значения:

|Attribute|Тип данных|Описание|  
|---------------|---------------|-----------------|  
|set_options|**int**|Показывает значения параметров, с использованием которых был скомпилирован план.|  
|objectid|**int**|Одно из основных ключевых слов, используемое для поиска объекта в кэш-памяти. Это идентификатор объекта, хранимый в [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) для объектов базы данных (процедуры, представления, триггеры и т. д.). Для планов типа «Нерегламентированный» или «Подготовленный» — это внутренний хэш текста пакета.|  
|dbid|**int**|Идентификатор базы данных, содержащей сущность, к которой относится план.<br /><br /> Для нерегламентированных и подготовленных планов это идентификатор базы данных, из которой выполняется пакет.|  
|dbid_execute|**int**|Для системных объектов, хранящихся в **ресурсов** базы данных, идентификатор базы данных, из которой выполняется кэшированный план. Во всех остальных случаях это значение равно 0.|  
|user_id|**int**|Значение «-2» означает, что представленный пакет не зависит от неявного разрешения имен и может совместно использоваться разными пользователями. Этот метод является предпочтительным. Любое другое значение обозначает идентификатор пользователя, отправившего запрос к базе данных.| 
|language_id|**smallint**|Идентификатор языка соединения, в результате которого был создан объект кэша. Дополнительные сведения см. в разделе [sys.syslanguages &#40; Transact-SQL &#41; ](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md).|  
|date_format|**smallint**|Формат даты соединения, во время которого был создан объект кэша. Дополнительные сведения см. в разделе [SET DATEFORMAT &#40; Transact-SQL &#41; ](../../t-sql/statements/set-dateformat-transact-sql.md).|  
|date_first|**tinyint**|Значение первой даты. Дополнительные сведения см. в разделе [SET DATEFIRST &#40; Transact-SQL &#41; ](../../t-sql/statements/set-datefirst-transact-sql.md).|  
|status|**int**|Биты внутреннего состояния, являющиеся частью ключа уточняющего запроса к кэшу.|  
|required_cursor_options|**int**|Параметры курсора, указанные пользователем, такие как тип курсора.|  
|acceptable_cursor_options|**int**|Параметры курсора, которые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может неявно преобразовывать для поддержания выполнения инструкции. Например, пользователь может указать динамический курсор, но оптимизатор запросов может преобразовать этот тип курсора в статический.|  
|inuse_exec_context|**int**|Количество выполняемых в данный момент пакетов, использующих план запроса.|  
|free_exec_context|**int**|Количество контекстов выполнения в кэш-памяти для плана запроса, которые не используются в данный момент.|  
|hits_exec_context|**int**|Количество получений контекста выполнения из кэш-памяти планов и его повторных использований, приводящее к снижению издержек на повторную компиляцию инструкции SQL. Это значение является статистическим для всех пакетов, выполняющихся в настоящий момент.|  
|misses_exec_context|**int**|Количество обнаружений отсутствия контекста выполнения в кэш-памяти планов, приводящее к созданию нового контекста выполнения для пакета выполнения.|  
|removed_exec_context|**int**|Количество контекстов выполнения, которые были удалены по причине слишком активного использования памяти для плана в кэш-памяти.|  
|inuse_cursors|**int**|Количество выполняемых в данный момент пакетов, содержащих один или более курсоров, использующих план в кэш-памяти.|  
|free_cursors|**int**|Количество бездействующих или свободных курсоров для плана в кэш-памяти.|  
|hits_cursors|**int**|Количество получений неактивного курсора из плана в кэш-памяти и его повторных использований. Это значение является статистическим для всех пакетов, выполняющихся в настоящий момент.|  
|misses_cursors|**int**|Количество случаев обнаружения отсутствия неактивного курсора в кэш-памяти.|  
|removed_cursors|**int**|Количество курсоров, которые были удалены по причине слишком активного использования памяти для плана в кэше.|  
|sql_handle|**varbinary**(64)|Дескриптор SQL для пакета.|  
|merge_action_type|**smallint**|Тип плана выполнения триггеров, используемого в результате инструкции MERGE.<br /><br /> 0 указывает план без триггеров, или план триггеров, который не выполняется в результате инструкции MERGE, или план триггеров, который выполняется в результате инструкции MERGE, в которой задано только действие DELETE.<br /><br /> 1 указывает план триггеров INSERT, который выполняется в результате инструкции MERGE.<br /><br /> 2 указывает план триггеров UPDATE, который выполняется в результате инструкции MERGE.<br /><br /> 3 указывает план триггеров DELETE, который выполняется в результате инструкции MERGE, содержащей соответствующее действие INSERT или UPDATE.<br /><br /> Для вложенных триггеров, выполняемых каскадными операциями, это значение является действием инструкции MERGE, запустившей каскад.|  
  
## <a name="permissions"></a>Разрешения  
 На [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо разрешение VIEW SERVER STATE на сервере.  
  
 На [!INCLUDE[ssSDS](../../includes/sssds-md.md)] уровней Premium необходимо разрешение VIEW DATABASE STATE в базе данных. На [!INCLUDE[ssSDS](../../includes/sssds-md.md)] уровней Standard и Basic требуется [!INCLUDE[ssSDS](../../includes/sssds-md.md)] учетная запись администратора.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="set-options"></a>Параметры SET  
 Копирует же скомпилированного плана могут отличаться только по значению в **set_options** столбца. Это указывает на то, что разные соединения используют разные наборы параметров SET для одного запроса. Использование разных наборов параметров, как правило, нежелательно, поскольку приводит к дополнительным компиляциям, меньшему повторному использованию планов и расширению кэша планов по причине размещения нескольких копий планов в кэш-памяти.  
  
### <a name="evaluating-set-options"></a>Оценка параметров SET  
 Чтобы преобразовать значение, возвращенное в **set_options** , параметры, с которыми был скомпилирован план, необходимо вычитать эти значения из **set_options** значения, начиная с максимально возможного значения, пока не будет связаться с 0. Каждое вычитаемое значение соответствует одному параметру, который использовался в плане запроса. Например если значение в **set_options** 251, параметры план был скомпилирован с ANSI_NULL_DFLT_ON (128), QUOTED_IDENTIFIER (64), ANSI_NULLS(32), ANSI_WARNINGS (16), CONCAT_NULL_YIELDS_NULL (8), Parallel Plan(2) и ANSI_PADDING (1).  
  
|Параметр|Значение|  
|------------|-----------|  
|ANSI_PADDING|1|  
|Parallel Plan|2|  
|FORCEPLAN|4|  
|CONCAT_NULL_YIELDS_NULL|8|  
|ANSI_WARNINGS|16|  
|ANSI_NULLS|32|  
|QUOTED_IDENTIFIER|64|  
|ANSI_NULL_DFLT_ON|128|  
|ANSI_NULL_DFLT_OFF|256|  
|NoBrowseTable<br /><br /> Указывает, что план не использует рабочую таблицу для реализации операции FOR BROWSE.|512|  
|TriggerOneRow<br /><br /> Указывает, что план содержит однострочную оптимизацию для таблиц разности триггеров AFTER.|1024|  
|ResyncQuery<br /><br /> Указывает, что запрос был направлен внутренней системной хранимой процедурой.|2048|  
|ARITH_ABORT|4096|  
|NUMERIC_ROUNDABORT|8192|  
|DATEFIRST|16384|  
|DATEFORMAT|32768|  
|LanguageID|65536|  
|UPON<br /><br /> Указывает, что параметру базы данных PARAMETERIZATION присвоено значение FORCED при компиляции плана.|131072|  
|ROWCOUNT|**Область применения:** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 262144|  
  
## <a name="cursors"></a>Курсоры  
 Неактивные курсоры кэшируются в скомпилированном плане так, чтобы одновременно работающие пользователи курсоров могли повторно использовать память, использованную для хранения курсора. Предположим, что пакет объявляет и использует курсор без его освобождения. Если два пользователя выполняют один и тот же пакет, то будет два активных курсора. После освобождения курсоров (потенциально в разных пакетах), память, используемая для хранения курсора, кэшируется и не освобождается. Этот список неактивных курсоров хранится в скомпилированном плане. При следующем выполнении пакета пользователем память кэшированного курсора будет использоваться повторно и инициализироваться соответствующим образом, как для активного курсора.  
  
### <a name="evaluating-cursor-options"></a>Оценка параметров курсора  
 Чтобы преобразовать значение, возвращенное в **required_cursor_options** и **acceptable_cursor_options** , параметры, с которыми был скомпилирован план, необходимо вычитать эти значения из значения столбца, начиная с Наибольшее возможное значение, вплоть до 0. Каждое вычитаемое значение соответствует одному курсору, который использовался в плане запроса.  
  
|Параметр|Значение|  
|------------|-----------|  
|Нет|0|  
|INSENSITIVE|1|  
|SCROLL|2|  
|READ ONLY|4|  
|FOR UPDATE|8|  
|LOCAL|16|  
|GLOBAL|32|  
|FORWARD_ONLY|64|  
|KEYSET|128|  
|DYNAMIC|256|  
|SCROLL_LOCKS|512|  
|OPTIMISTIC|1024|  
|STATIC|2048|  
|FAST_FORWARD|4096|  
|IN PLACE|8192|  
|ДЛЯ *select_statement*|16384|  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-attributes-for-a-specific-plan"></a>A. Возврат атрибутов для конкретного плана  
 Следующий пример возвращает все атрибуты для указанного плана. В первый раз динамическое административное представление `sys.dm_exec_cached_plans` опрашивается для получения дескриптора указанного плана. Во втором запросе `<plan_handle>` заменяется значением дескриптора плана из первого запроса.  
  
```sql  
SELECT plan_handle, refcounts, usecounts, size_in_bytes, cacheobjtype, objtype   
FROM sys.dm_exec_cached_plans;  
GO  
SELECT attribute, value, is_cache_key  
FROM sys.dm_exec_plan_attributes(<plan_handle>);  
GO  
```  
  
### <a name="b-returning-the-set-options-for-compiled-plans-and-the-sql-handle-for-cached-plans"></a>Б. Возврат параметров SET для скомпилированных планов и дескриптора SQL для планов в кэш-памяти  
 Следующий пример возвращает значение, представляющее параметры, с использованием которых был скомпилирован план. Кроме того, возвращается дескриптор SQL для всех кэшированных планов.  
  
```sql  
SELECT plan_handle, pvt.set_options, pvt.sql_handle  
FROM (  
    SELECT plan_handle, epa.attribute, epa.value   
    FROM sys.dm_exec_cached_plans   
        OUTER APPLY sys.dm_exec_plan_attributes(plan_handle) AS epa  
    WHERE cacheobjtype = 'Compiled Plan') AS ecpa   
PIVOT (MAX(ecpa.value) FOR ecpa.attribute IN ("set_options", "sql_handle")) AS pvt;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [&#40; динамические административные представления и функции, связанные с выполнением Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_cached_plans &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)   
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.Objects &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
  

