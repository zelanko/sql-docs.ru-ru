---
title: sys.sysindexes (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysindexes
- sysindexes_TSQL
- sys.sysindexes
- sys.sysindexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysindexes system table
- sys.sysindexes compatibility view
ms.assetid: f483d89c-35c4-4a08-8f8b-737fd80d13f5
author: rothja
ms.author: jroth
ms.openlocfilehash: 560b5ab5d85c7f2a69fb5062a6eacc6e5c85ee1d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68053443"
---
# <a name="syssysindexes-transact-sql"></a>sys.sysindexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого индекса и таблицы в текущей базе данных. XML-индексы в этом представлении не поддерживаются, Секционированные таблицы и индексы поддерживаются не полностью в этом представлении; Используйте [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) вместо этого представление каталога.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор таблицы, которой принадлежит данный индекс.|  
|**status**|**int**|Сведения о состоянии системы.<br /><br /> [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**first**|**binary(6)**|Указатель на первую или корневую страницу.<br /><br /> Не используется, если **indid** = 0.<br /><br /> NULL = индекс секционируется, если **indid** > 1.<br /><br /> NULL = таблица секционируется, если **indid** равен 0 или 1.|  
|**Если столбец indid равен**|**smallint**|Идентификатор индекса:<br /><br /> 0 = куча;<br /><br /> 1 = кластеризованный индекс;<br /><br /> > 1 = некластеризованный индекс|  
|**Корневой**|**binary(6)**|Для **indid** > = 1, **корневой** является указателем на корневую страницу.<br /><br /> Не используется, если **indid** = 0.<br /><br /> NULL = индекс секционируется, если **indid** > 1.<br /><br /> NULL = таблица секционируется, если **indid** равен 0 или 1.|  
|**minlen**|**smallint**|Минимальный размер строки.|  
|**keycnt**|**smallint**|Количество ключей.|  
|**groupid**|**smallint**|Идентификатор файловой группы, в которой был создан объект.<br /><br /> NULL = индекс секционируется, если **indid** > 1.<br /><br /> NULL = таблица секционируется, если **indid** равен 0 или 1.|  
|**dpages**|**int**|Для **indid** = 0 или **indid** = 1, **dpages** является счетчиком использованных страниц данных.<br /><br /> Для **indid** > 1, **dpages** является счетчиком использованных страниц индекса.<br /><br /> 0 = индекс секционируется, если **indid** > 1.<br /><br /> 0 = таблица секционируется, если **indid** равен 0 или 1.<br /><br /> Не дает точных результатов при возникновении переполнения строки.|  
|**Зарезервировано**|**int**|Для **indid** = 0 или **indid** = 1, **зарезервированные** является счетчиком страниц, выделенных для всех индексов и таблиц данных.<br /><br /> Для **indid** > 1, **зарезервированные** является счетчиком страниц, выделенных для индекса.<br /><br /> 0 = индекс секционируется, если **indid** > 1.<br /><br /> 0 = таблица секционируется, если **indid** равен 0 или 1.<br /><br /> Не дает точных результатов при возникновении переполнения строки.|  
|**используется**|**int**|Для **indid** = 0 или **indid** = 1, **используется** является счетчиком общего количества страниц, используемый для всех индексов и таблиц данных.<br /><br /> Для **indid** > 1, **используется** является счетчиком страниц, используемых для индекса.<br /><br /> 0 = индекс секционируется, если **indid** > 1.<br /><br /> 0 = таблица секционируется, если **indid** равен 0 или 1.<br /><br /> Не дает точных результатов при возникновении переполнения строки.|  
|**rowcnt**|**bigint**|Счетчик строк уровня данных на основе **indid** = 0 и **indid** = 1.<br /><br /> 0 = индекс секционируется, если **indid** > 1.<br /><br /> 0 = таблица секционируется, если **indid** равен 0 или 1.|  
|**rowmodctr**|**int**|Подсчитывает общее количество вставленных, удаленных или обновленных строк, начиная с момента последнего обновления статистики для таблицы.<br /><br /> 0 = индекс секционируется, если **indid** > 1.<br /><br /> 0 = таблица секционируется, если **indid** равен 0 или 1.<br /><br /> В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях **rowmodctr** не полностью совместим с более ранними версиями. Дополнительные сведения см. в подразделе "Примечания".|  
|**reserved3**|**int**|Возвращает 0.<br /><br /> [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**reserved4**|**int**|Возвращает 0.<br /><br /> [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xmaxlen**|**smallint**|Максимальный размер строки.|  
|**maxirow**|**smallint**|Максимальный размер неконечных индексных строк.<br /><br /> В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях **maxirow** не полностью совместим с более ранними версиями.|  
|**OrigFillFactor**|**tinyint**|Оригинальное значение коэффициента заполнения, используемого при создании индекса. Это значение не поддерживается. Однако оно может быть полезным при повторном создании индекса, если забыто значение используемого коэффициента заполнения.|  
|**StatVersion**|**tinyint**|Возвращает 0.<br /><br /> [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**reserved2**|**int**|Возвращает 0.<br /><br /> [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**FirstIAM**|**binary(6)**|NULL = индекс секционирован.<br /><br /> [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**impid**|**smallint**|Флаг реализации индекса.<br /><br /> Возвращает 0.<br /><br /> [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**lockflags**|**smallint**|Используется для ограничения рассматриваемой гранулярности блокировки для индекса. Например, для минимизации стоимости блокировки уровень блокировки таблицы подстановки, находящейся в режиме только для чтения, может быть установлен только на уровне таблицы.|  
|**pgmodctr**|**int**|Возвращает 0.<br /><br /> [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**Ключи**|**varbinary(816)**|Список идентификаторов столбцов, составляющих ключ индекса.<br /><br /> Возвращает значение NULL.<br /><br /> Чтобы отобразить ключевые столбцы индекса, используйте [sys.sysindexkeys](../../relational-databases/system-compatibility-views/sys-sysindexkeys-transact-sql.md).|  
|**name**|**sysname**|Имя индекса или статистики. Возвращает значение NULL, если **indid** = 0. Измените приложение, чтобы оно выполняло поиск кучи с именем NULL.|  
|**statblob**|**image**|Статистический большой двоичный объект (BLOB).<br /><br /> Возвращает значение NULL.|  
|**MaxLen**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**rows**|**int**|Счетчик строк уровня данных на основе **indid** = 0 и **indid** = 1, и значение повторяется для **indid** > 1.|  
  
## <a name="remarks"></a>Примечания  
 Столбцы, определенные как зарезервированные, не должны использоваться.  
  
 Столбцы **dpages**, **зарезервированные**, и **используется** не будут давать точные результаты, если таблица или индекс содержит данные в распределения ROW_OVERFLOW. Кроме того, счетчики страниц для каждого индекса отслеживаются отдельно и не суммируются для базовой таблицы. Для просмотра счетчиков страниц используйте [sys.allocation_units](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md) или [sys.partitions](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md) представления каталога, или [sys.dm_db_partition_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql.md) динамическое административное представление.  
  
 В SQL Server 2000 и более ранних версиях компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] поддерживал счетчики изменения на уровне строк. Теперь эти счетчики поддерживаются на уровне столбца. Таким образом **rowmodctr** столбец вычисляется и выдает результаты, которые похожи на результаты в более ранних версиях, но не являются точными.  
  
 Если вы используете значение в **rowmodctr** для определения времени обновления статистики, рассмотрите следующие решения:  
  
-   Не делать ничего. Новый **rowmodctr** значение зачастую может помочь определить, когда нужно обновить статистику, поскольку поведение достаточно близок к результаты более ранних версий.  
  
-   Использовать параметр AUTO_UPDATE_STATISTICS. Дополнительные сведения см. [статистики](../../relational-databases/statistics/statistics.md).  
  
-   Использовать временное ограничение для определения времени обновления статистики. Например, каждый час, каждый день или каждую неделю.  
  
-   Использовать данные уровня приложения для определения времени обновления статистики. Например, каждый раз максимальное значение **удостоверений** столбца меняется с более чем 10 000 или выполняется каждый раз при выполнении операции массовой вставки.  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Сопоставление системных таблиц с системными представлениями &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
  
  
