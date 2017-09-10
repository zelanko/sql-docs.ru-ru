---
title: "DATABASEPROPERTYEX (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATABASEPROPERTYEX
- DATABASEPROPERTYEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DATABASEPROPERTYEX function
- displaying database properties
- database properties [SQL Server]
ms.assetid: 8a9e0ffb-28b5-4640-95b2-a54e3e5ad941
caps.latest.revision: 84
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 737aed43128be71a53c8087be11176bc4e364e8a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="databasepropertyex-transact-sql"></a>DATABASEPROPERTYEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает текущее значение заданного параметра базы данных или свойство для указанной в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
DATABASEPROPERTYEX ( database , property )  
```  
  
## <a name="arguments"></a>Аргументы  
*database*  
Представляет собой выражение, представляющее имя базы данных, для которой возвращается информация об именованном свойстве. *База данных* — **nvarchar(128)**.  
Для [!INCLUDE[ssSDS](../../includes/sssds-md.md)] должно быть именем текущей базы данных. Возвращает значение NULL для всех свойств, если указано другое имя базы данных.
  
*Свойство*  
Выражение, представляющее собой имя возвращаемого свойства базы данных. *Свойство* — **varchar(128)**, и может принимать одно из следующих значений. Возвращаемый тип — **sql_variant**. В следующей таблице перечислены базовые типы данных для каждого из свойств.
  
> [!NOTE]  
>  Если база данных не запущена, свойства, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает значение NULL, нужен доступ к базе данных напрямую, а не получение значения из метаданных. Это происходит в случае, если для базы данных параметр AUTO_CLOSE установлен в ON или если база данных находится в режиме вне сети по другой причине.  
  
|Свойство|Description|Возвращенное значение|  
|---|---|---|
|Параметры сортировки|Имя параметров сортировки, установленных для базы данных по умолчанию.|Имя параметров сортировки.<br /><br /> NULL = база данных не запущена.<br /><br /> Базовый тип данных: **nvarchar(128)**|  
|ComparisonStyle|Стиль сравнения Windows для параметров сортировки. ComparisonStyle является точечного рисунка, который вычисляется с помощью следующих значений для возможных стилей.<br /><br /> Не учитывать регистр: 1<br /><br /> Без учета диакритических знаков: 2<br /><br /> Не учитывать кану: 65536<br /><br /> Игнорировать ширину: 131072<br /><br /> <br /><br /> Например, значение по умолчанию — 196609 — образуется в результате сочетания параметров «Без учета регистра», «Без учета типа японской азбуки» и «Без учета ширины».|Возвращает стиль сравнения.<br /><br /> Возвращает значение 0 для всех двоичных параметров сортировки.<br /><br /> Базовый тип данных: **int**|  
|Выпуск|Уровень выпуска или службы базы данных.|**Применяется к**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].<br /><br /> <br /><br /> Web = база данных Web Edition<br /><br /> Business = база данных Business Edition<br /><br /> Basic<br /><br /> Standard Edition<br /><br /> Premium<br /><br /> Системный (для базы данных master)<br /><br /> NULL = база данных не запущена.<br /><br /> Базовый тип данных: **nvarchar**(64)|  
|IsAnsiNullDefault|База данных следует правилам ISO по разрешению значений NULL.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|  
|IsAnsiNullsEnabled|При всех сравнениях со значением NULL результат не определен.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|  
|IsAnsiPaddingEnabled|Строки перед сравнением или вставкой дополняются до одной и той же длины.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|  
|IsAnsiWarningsEnabled|Сообщения об ошибках или предупреждения отображаются, если появляются стандартные условия ошибки.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|  
|IsArithmeticAbortEnabled|Запрос завершается, если в процессе его выполнения происходит ошибка переполнения или деления на нуль.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|  
|IsAutoClose|После выхода последнего пользователя база данных корректно выключается и освобождает ресурсы.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|  
|IsAutoCreateStatistics|Оптимизатор запросов при необходимости создает статистику по отдельным столбцам для повышения производительности запросов.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|  
|IsAutoCreateStatisticsIncremental|Автоматические статистики в одном столбце создаются в дополнительном виде везде, где это возможно.|**Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> <br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|  
|IsAutoShrink|Файлы базы данных являются кандидатами на автоматическое периодическое сжатие.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|  
|IsAutoUpdateStatistics|Оптимизатор запросов обновляет существующую статистику, если она используется в запросе и может оказаться устаревшей.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|
|IsClone|База данных является копией только схемы и статистики пользовательской базы данных.|**Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] пакетом обновления 2.<br /><br /> <br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**| 
|IsCloseCursorsOnCommitEnabled|Открытые курсоры закрываются при фиксации транзакции.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|  
|IsFulltextEnabled|В базе данных включены полнотекстовое и семантическое индексирование.|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> <br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**<br /><br /> **Примечание:** значение этого свойства не оказывает влияния. Полнотекстовый поиск всегда включен для пользовательских баз данных. Этот столбец будет удален в будущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не используйте этот столбец при работе над новыми приложениями и как можно быстрее измените приложения, в настоящее время использующие любые из этих столбцов.|  
|IsInStandBy|В режиме «в сети» база данных доступна только для чтения, при этом разрешен журнал восстановления.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|  
|IsLocalCursorsDefault|Объявления курсора по умолчанию — LOCAL.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|  
|IsMemoryOptimizedElevateToSnapshotEnabled|К таблицам с оптимизацией для памяти доступ производится с использованием изоляции SNAPSHOT, когда в TRANSACTION ISOLATION LEVEL установлен более низкий уровень изоляции — READ COMMITTED или READ UNCOMMITTED.|**Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> <br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> Базовый тип данных: **int**|  
|IsMergePublished|Таблицы базы данных могут быть опубликованы для репликации слиянием, если репликация установлена.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|  
|IsNullConcat|Объединение операнда со значением NULL дает значение NULL.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|  
|IsNumericRoundAbortEnabled|При потере точности в выражениях возникают ошибки.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|  
|IsParameterizationForced|Параметр SET PARAMETERIZATION имеет значение FORCED.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.|  
|IsQuotedIdentifiersEnabled|Двойные кавычки можно использовать в идентификаторах.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|  
|IsPublished|Таблицы базы данных могут быть опубликованы для репликации моментальных снимков или транзакций в случае, если репликация установлена.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|  
|IsRecursiveTriggersEnabled|Рекурсивное срабатывание триггеров разрешено.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|  
|IsSubscribed|База данных подписана на публикацию.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|  
|IsSyncWithBackup|База данных является опубликованной либо является базой данных распространителя и может быть восстановлена без нарушения репликации транзакций.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|  
|IsTornPageDetectionEnabled|Компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] выявляет незавершенные операции ввода-вывода, вызванные сбоями питания или другими перерывами в работе системы.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные.<br /><br /> Базовый тип данных: **int**|  
|IsXTPSupported|Указывает ли поддерживает база данных OLTP в памяти, т. е., создания и использования оптимизированных для памяти таблицы и модули, скомпилированные в собственном коде.<br /><br /> Относящиеся к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:<br /><br /> IsXTPSupported не зависит от существования любая файловая группа MEMORY_OPTIMIZED_DATA, которая необходима для создания объектов OLTP в памяти.|**Применяется к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]), [!INCLUDE[ssSDS](../../includes/sssds-md.md)].<br /><br /> **Применяется к**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запуск [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].<br /><br /> <br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = недопустимые входные данные ошибку, или неприменимо<br /><br /> Базовый тип данных: **int**|  
|LCID|Языковой стандарт (код языка) Windows для параметров сортировки.|Значение кода языка (в десятичном формате).<br /><br /> Базовый тип данных: **int**|  
|MaxSizeInBytes|Максимальный размер базы данных в байтах.|**Применяется к**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].<br /><br /> <br /><br /> 1073741824<br /><br /> 5368709120<br /><br /> 10737418240<br /><br /> 21474836480<br /><br /> 32212254720<br /><br /> 42949672960<br /><br /> 53687091200<br /><br /> NULL = база данных не запущена<br /><br /> Базовый тип данных: **bigint**|  
|Восстановление|Модель восстановления базы данных.|FULL = модель полного восстановления.<br /><br /> BULK_LOGGED = модель восстановления с неполным протоколированием.<br /><br /> SIMPLE = простая модель восстановления.<br /><br /> Базовый тип данных: **nvarchar(128)**|  
|ServiceObjective|Описывает уровень производительности базы данных в [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] или [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].|Возможен один из следующих вариантов.<br /><br /> Значение NULL: база данных не запущена<br /><br /> Общий (для выпусков Web или Business)<br /><br /> Basic<br /><br /> S0<br /><br /> S1<br /><br /> S2<br /><br /> S3<br /><br /> P1<br /><br /> P2<br /><br /> P3<br /><br /> ElasticPool<br /><br /> Системный (для базы данных master)<br /><br /> Базовый тип данных: **nvarchar(32)**|  
|ServiceObjectiveId|Идентификатор цели службы в [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].|**uniqueidentifier** , определяющий цель службы.|  
|SQLSortOrder|Идентификатор порядка сортировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], поддерживаемого в предыдущих версиях SQL Server.|0 = в базе данных используются параметры сортировки Windows.<br /><br /> >0 = идентификатор порядка сортировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> NULL = недопустимые входные данные или база данных не запущена.<br /><br /> Базовый тип данных: **tinyint**|  
|Состояние|Состояние базы данных.|ONLINE = база данных доступна для запросов.<br /><br /> **Примечание:** состоянии может быть возвращено, когда база данных открыт и не еще восстановить. Чтобы определить базы данных может принимать соединения, запросите свойство параметров сортировки **DATABASEPROPERTYEX**. База данных может принимать соединения, если параметры сортировки базы данных возвращают значение, отличное от NULL. Для базы данных Always On запросите столбцы database_state или database_state_desc sys.dm_hadr_database_replica_states.<br /><br /> OFFLINE = база данных явным образом переведена в режим «вне сети».<br /><br /> RESTORING = база данных находится в процессе восстановления.<br /><br /> RECOVERING = база данных восстанавливается и еще не готова к запросам.<br /><br /> SUSPECT = база данных не восстанавливалась.<br /><br /> EMERGENCY = база данных находится в аварийном состоянии и доступна только для чтения. Доступ ограничен членами роли sysadmin.<br /><br /> Базовый тип данных: **nvarchar(128)**|  
|Updateability|Указывает, можно ли изменять данные.|READ_ONLY = данные можно считывать, но не изменять.<br /><br /> READ_WRITE = данные можно считывать и изменять.<br /><br /> Базовый тип данных: **nvarchar(128)**|  
|UserAccess|Указывает пользователей, имеющих доступ к базе данных.|SINGLE_USER = в каждый момент времени доступ имеет только один пользователь db_owner, dbcreator или sysadmin<br /><br /> RESTRICTED_USER = только члены ролей db_owner, dbcreator и sysadmin<br /><br /> MULTI_USER = все пользователи<br /><br /> Базовый тип данных: **nvarchar(128)**|  
|Version|Внутренний номер версии того кода [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с которым была создана база данных. [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|Номер версии = база данных открыта.<br /><br /> NULL = база данных не запущена.<br /><br /> Базовый тип данных: **int**|  
  
## <a name="return-types"></a>Возвращаемые типы
**sql_variant**
  
## <a name="exceptions"></a>Исключения  
Возвращает значение NULL в случае ошибки или если участник не имеет разрешений для просмотра объекта.
  
В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователь может просматривать только метаданные защищаемых объектов, которыми он владеет или на которые ему были предоставлены разрешения. Это означает, что встроенные функции, создающие метаданные, такие как OBJECT_ID, могут вернуть значение NULL в случае, если пользователь не имеет разрешений на объект. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).
  
## <a name="remarks"></a>Замечания  
Функция DATABASEPROPERTYEX возвращает каждый раз значение только одного свойства. Для отображения значений нескольких свойств используйте [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) представления каталога.
  
## <a name="examples"></a>Примеры  
  
### <a name="a-retrieving-the-status-of-the-autoshrink-database-option"></a>A. Получение состояния параметра базы данных AUTO_SHRINK  
В следующем примере показан возврат состояния параметра AUTO_SHRINK базы данных `AdventureWorks`.
  
```sql
SELECT DATABASEPROPERTYEX('AdventureWorks2014', 'IsAutoShrink');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)] Это означает, что параметр AUTO_SHRINK отключен.
  
```sql
------------------  
0  
```  
  
### <a name="b-retrieving-the-default-collation-for-a-database"></a>Б. Получение установленных по умолчанию параметров сортировки для базы данных  
В следующем примере возвращается несколько атрибутов `AdventureWorks` базы данных.
  
```sql
SELECT   
    DATABASEPROPERTYEX('AdventureWorks2014', 'Collation') AS Collation,  
    DATABASEPROPERTYEX('AdventureWorks2014', 'Edition') AS Edition,  
    DATABASEPROPERTYEX('AdventureWorks2014', 'ServiceObjective') AS ServiceObjective,  
    DATABASEPROPERTYEX('AdventureWorks2014', 'MaxSizeInBytes') AS MaxSizeInBytes  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Collation                     Edition        ServiceObjective  MaxSizeInBytes  
----------------------------  -------------  ----------------  --------------  
SQL_Latin1_General_CP1_CI_AS  DataWarehouse  DW1000            5368709120  
```  
  
## <a name="see-also"></a>См. также:
[ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)  
[Состояния базы данных](../../relational-databases/databases/database-states.md)  
[sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
[sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
[SERVERPROPERTY (Transact-SQL)](../../t-sql/functions/serverproperty-transact-sql.md)
  
  

