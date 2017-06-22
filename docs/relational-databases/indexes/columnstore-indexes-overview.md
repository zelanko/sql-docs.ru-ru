---
title: "Общие сведения об индексах columnstore | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/07/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- indexes creation, columnstore
- indexes [SQL Server], columnstore
- columnstore index
- columnstore index, described
- xVelocity, columnstore indexes
ms.assetid: f98af4a5-4523-43b1-be8d-1b03c3217839
caps.latest.revision: 80
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 33a0dbca3c96a38466c560487965c8825ff5328d
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="columnstore-indexes---overview"></a>Общие сведения об индексах columnstore
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  *Индекс columnstore* — это стандарт хранения и запрашивания больших объемов данных, в которых хранятся таблицы фактов. Хранение данных и обработка запросов по индексам позволяют **до 10 раз** увеличить производительность запросов к хранилищу данных по сравнению с традиционным хранилищем, в котором данные хранятся по строкам, и уменьшить размеры данных **до 10 раз** по сравнению с несжатыми данными. Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], индексы columnstore позволяют получать оперативную аналитику и анализировать рабочую нагрузку по обработке транзакций в режиме реального времени.  
  
 Сценарии:  
  
-   [Индексы сolumnstore для хранилищ данных](~/relational-databases/indexes/columnstore-indexes-data-warehouse.md)  
  
-   [Начало работы с Columnstore для получения операционной аналитики в реальном времени](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)  
  
## <a name="what-is-a-columnstore-index"></a>Что такое индекс columnstore?  
 *columnstore index* — это технология хранения, получения данных и управления ими с помощью формата хранения данных в один столбец, называемого columnstore.  
  
### <a name="key-terms-and-concepts"></a>Основные термины и понятия  
 С индексами columnstore связаны следующие основные термины и понятия:  
  
 columnstore  
 *columnstore* — это данные, логически организованные в виде таблицы, состоящей из строк и столбцов, и физически хранящиеся в формате данных в столбцах.  
  
 rowstore  
 *rowstore* — это данные, логически организованные в виде таблицы, состоящей из строк и столбцов, и физически хранящиеся в формате данных в столбцах. Это стандартный способ хранения реляционных данных таблиц. В SQL Server rowstore — это таблица с базовым форматом хранения данных "куча", "кластеризованный индекс" или "таблица в памяти".  
  
> [!NOTE]  
>  В обсуждениях индексов columnstore для обозначения формата хранения данных используются термины *rowstore* и *columnstore* .  
  
 rowgroup  
 *Rowgroup* — это группа строк, сжимаемых в формате columnstore одновременно. Группа строк обычно содержит максимальное число строк для группы строк, 1 048 576 строк.  
  
 Чтобы добиться высокой производительности и высокого уровня сжатия, индекс columnstore разделяет таблицы в группы строк, называемые группами строк, каждая из которых затем сжимается на уровне столбцов. Число строк в группе строк должно быть достаточно большим, чтобы повысить скорость сжатия, и достаточно малым для использования преимуществ использования операций в памяти.  
  
 Сегмент столбца  
 *Сегмент столбца* — это столбец данных из группы строк.  
  
-   Каждая rowgroup содержит один сегмент столбца для каждого столбца в таблице.  
  
-   Каждый сегмент столбца сжимается одновременно и сохраняется на физическом носителе.  
  
 ![Column segment](../../relational-databases/indexes/media/sql-server-pdw-columnstore-columnsegment.gif "Column segment")  
  
 кластеризованный индекс columnstore  
 *Кластеризованный индекс columnstore* — это физическое хранилище для всей таблицы.  
  
 ![Clustered Columnstore Index](../../relational-databases/indexes/media/sql-server-pdw-columnstore-physicalstorage.gif "Clustered Columnstore Index")  
  
 Чтобы снизить фрагментацию сегментов столбцов и повысить производительность, индекс columnstore может временно сохранять некоторые данные в кластеризованный индекс, который называется deltastore, и использовать для удаленных строк сбалансированное дерево идентификаторов. Операции deltastore обрабатываются в фоновом режиме. Для получения правильных результатов запросов кластеризованные индексы columnstore объединяют результаты запроса от columnstore и deltastore.  
  
 deltastore  
 *Deltastore* используется только с кластеризованными индексами columnstore и представляет собой кластеризованный индекс, который улучшает сжатие и эффективность хранения строк, пока их количество не достигнет предельного значения, а затем переносит строки в индекс columnstore.  
  
 При крупной массовой загрузке большинство строк переходят непосредственно в columnstore без промежуточного помещения в deltastore. Некоторых строк в конце массовой загрузки может оказаться слишком мало для соответствия минимальному размеру rowgroup, составляющему 102 400 строк. В этом случае последние строки переходят в deltastore вместо columnstore. Для небольших массовых загрузок с менее 102 400 строк, все строки перемещаются напрямую в deltastore.  
  
 Когда объем deltastore достигает максимального числа строк, оно закрывается. Процесс перемещения кортежей выполняет проверку на наличие закрытых групп строк. При обнаружении закрытой группы строк оно уменьшает его и сохраняет в columnstore.  
  
 некластеризованный индекс columnstore  
 *Некластеризованный индекс columnstore* и кластеризованный индекс columnstore — это одно и то же. Разница в том, что некластеризованный индекс вторичен и создается на основе таблицы индексов rowstore, а кластеризованный индекс columnstore является первичным для всей страницы.  
  
 Некластеризованный индекс содержит копию всех или части строк и столбцов в базовой таблице. Индекс определяется как один или несколько столбцов таблицы и включает дополнительное условие для фильтрации строк.  
  
 Некластеризованный индекс columnstore позволяет осуществлять оперативную аналитику в режиме реального времени, когда рабочая нагрузка OLTP выполняется с использованием базового кластеризованного индекса, а аналитика при этом проводится на основе индекса columnstore. Дополнительные сведения см. в статье [Начало работы с Columnstore для получения операционной аналитики в реальном времени](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md).  
  
 пакетное выполнение  
 *Пакетное выполнение* — это метод обработки запросов, при котором запросы обрабатывают сразу несколько строк. В запросах к индексам columnstore используется режим пакетного выполнения, что обычно повышает производительность запросов в 2–4 раза. Пакетное выполнение тесно интегрировано и оптимизировано для взаимодействия с форматом хранения columnstore. Выполнение пакета иногда называется выполнением на основе векторов или векторизированным.  
  
##  <a name="benefits"></a> Для чего нужен индекс columnstore?  
 Индекс columnstore обеспечивает высокую (обычно десятикратную) степень сжатия данных, что позволяет существенно снизить затраты на хранение данных. Кроме того, он на порядок повышает эффективность анализа по сравнению с индексом сбалансированного дерева. Это предпочтительный формат хранения данных и выполнения аналитики. Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], индексы columnstore можно использовать для аналитики рабочей нагрузки по операциям в режиме реального времени.  
  
 Почему индексы columnstore такие быстрые.  
  
-   В столбцах хранятся значения с одного и того же домена, которые часто похожи, что позволяет добиться высокой степени сжатия данных. В результате в системе не возникает или сводится к минимуму узкое место в операциях ввода-вывода и в то же время используется намного меньше памяти.  
  
-   Высокие степени сжатия повышают производительность запросов с помощью малого отпечатка в памяти. В свою очередь, может повышаться производительность запросов, так как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может выполнять больше операций с запросами и данными в памяти.  
  
-   Пакетное выполнение повышает эффективность запросов (обычно в 2–4 раза), обрабатывая сразу несколько строк.  
  
-   Часто запросы выбирают только несколько столбцов из таблицы, что сокращает общее число операций ввода-вывода для физического носителя.  
  
## <a name="when-should-i-use-a-columnstore-index"></a>Когда следует использовать индекс columnstore?  
 Рекомендации по использованию  
  
-   Используйте кластеризованный индекс columnstore для хранения таблиц фактов и больших таблиц измерений для рабочих нагрузок хранилищ данных. Это повышает эффективность запросов и сжатие данных до 10 раз. См. раздел [Columnstore Indexes for Data Warehousing](~/relational-databases/indexes/columnstore-indexes-data-warehouse.md).  
  
-   Используйте некластеризованный индекс columnstore для анализа рабочей нагрузки OLTP в режиме реального времени. См. статью [Начало работы с Columnstore для получения операционной аналитики в реальном времени](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md).  
  
### <a name="how-do-i-choose-between-a-rowstore-index-and-a-columnstore-index"></a>Как сделать выбор между индексами rowstore и columnstore?  
 Индексы rowstore лучше всего работают с запросами, направленными на поиск данных или определенного значения, а также с запросами небольшого диапазона данных. Используйте индексы rowstore с рабочими нагрузками по транзакциям, поскольку последние чаще требуют поиска по таблицам, а не сканирования таблиц.  
  
 Индексы columnstore обеспечивают значительное повышение производительности при выполнении аналитических запросов, которые сканируют большие объемы данных (в частности, большие таблицы).  Используйте индексы columnstore с рабочими нагрузками по хранению и аналитике данных (в частности, с таблицами фактов), поскольку они чаще требуют полного сканирования таблиц, а не поиска по таблицам.  
  
### <a name="can-i-combine-rowstore-and-columnstore-on-the-same-table"></a>Можно ли использовать индексы rowstore и columnstore в одной и той же таблице?  
 Да. Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], можно создавать обновляемый некластеризованный индекс columnstore в таблице rowstore. В индексе columnstore хранится копия выбранных столбцов, которые сжимаются в среднем в 10 раз и не требуют дополнительного пространства. Таким образом, вы сможете выполнять аналитику на основе индекса columnstore и транзакции на основе индекса rowstore одновременно. Хранилище столбцов обновляется при каждом изменении данных в таблице rowstore, поэтому оба индекса работают с одними и теми же данными.  
  
 Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], индекс columnstore может включать один или несколько некластеризованных индексов rowstore. Это обеспечивает эффективность поиска по таблицам на основе базового индекса columnstore. Кроме того, появляется доступ к другим возможностям. Например, можно принудительно задать ограничение PRIMARY KEY, применив к таблице rowstore ограничение UNIQUE. Поскольку неуникальное значение в таблицу rowstore не вставляется, SQL Server не может вставить значение в columnstore.  
  
## <a name="metadata"></a>Метаданные  
 Все столбцы в индексе columnstore хранятся в метаданных как включенные столбцы. Индекс columnstore не имеет ключевых столбцов.  
  
-   [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
  
-   [sys.index_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
-   [sys.partitions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)  
  
-   [sys.internal_partitions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-internal-partitions-transact-sql.md)  
  
-   [sys.column_store_segments (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
-   [sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)  
  
-   [sys.column_store_row_groups (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md)  
  
-   [sys.dm_db_column_store_row_group_operational_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-operational-stats-transact-sql.md)  
  
-   [sys.dm_db_column_store_row_group_physical_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-physical-stats-transact-sql.md)  
  
-   [sys.dm_column_store_object_pool (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-column-store-object-pool-transact-sql.md)  
  
-   [sys.dm_db_column_store_row_group_operational_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-operational-stats-transact-sql.md)  
  
-   [sys.dm_db_index_operational_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)  
  
-   [sys.dm_db_index_physical_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)  
  
## <a name="related-tasks"></a>Связанные задачи  
 Для всех реляционных таблиц, не заданных как кластеризованный индекс columnstore, в качестве базового формата данных используется индекс rowstore. Инструкция CREATE TABLE создает таблицу rowstore, если не задан параметр WITH CLUSTERED COLUMNSTORE INDEX.  
  
 При создании таблицы с помощью инструкции CREATE TABLE можно создать таблицу с индексом columnstore, указав параметр WITH CLUSTERED COLUMNSTORE INDEX. Чтобы конвертировать таблицу rowstore в columnstore, используйте операцию CREATE COLUMNSTORE INDEX. См. примеры.  
  
|Задача|Справочные разделы|Примечания|  
|----------|----------------------|-----------|  
|Создание таблицы как кластеризованного индекса columnstore|[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)|Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], таблицы можно создавать как кластеризованный индекс columnstore. Для этого не нужно создавать таблицу rowstore, а затем конвертировать ее в columnstore.|  
|Создание таблицы в памяти с индексом columnstore.|[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)|Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], таблицы, оптимизированные для памяти, можно создавать с индексом columnstore. Индекс columnstore можно добавить и после создания таблицы, используя синтаксис ALTER TABLE ADD INDEX.|  
|Преобразование таблицы rowstore в таблицу columnstore|[CREATE COLUMNSTORE INDEX (Transact-SQL)](../../t-sql/statements/create-columnstore-index-transact-sql.md)|Преобразуйте существующую кучу или сбалансированное дерево в columnstore. В примерах показано, как обрабатывать существующие индексы, а также имя индекса, которое нужно использовать в процессе преобразования.|  
|Преобразование таблицы columnstore в rowstore|[CREATE COLUMNSTORE INDEX (Transact-SQL)](../../t-sql/statements/create-columnstore-index-transact-sql.md)|Обычно этого не требуется, однако бывают ситуации, когда такое преобразование необходимо. В примерах показано, как преобразовать columnstore в кучу или кластеризованный индекс.|  
|Создание индекса columnstore в таблице rowstore|[CREATE COLUMNSTORE INDEX (Transact-SQL)](../../t-sql/statements/create-columnstore-index-transact-sql.md)|Таблица rowstore может включать один индекс columnstore.  Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], индекс columnstore может иметь отфильтрованное условие. В примерах показан основной синтаксис.|  
|Создание высокопроизводительных индексов для оперативной аналитики|[Начало работы с Columnstore для получения операционной аналитики в реальном времени](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)|Описывает процесс создания дополнительных индексов columnstore и сбалансированного дерева, которые позволят использовать индексы сбалансированного дерева в запросах OLTP и индексы columnstore в запросах аналитики.|  
|Создание высокопроизводительных индексов сolumnstore для хранилищ данных|[Индексы сolumnstore для хранилищ данных](~/relational-databases/indexes/columnstore-indexes-data-warehouse.md)|Описывает использование индексов сбалансированного дерева в таблицах columnstore для создания высокопроизводительных запросов к хранилищу данных.|  
|Использование индекса сбалансированного дерева для принудительного применения ограничения PRIMARY KEY в таблице columnstore|[Индексы сolumnstore для хранилищ данных](~/relational-databases/indexes/columnstore-indexes-data-warehouse.md)|Показывает, как объединить индексы сбалансированного дерева и columnstore для принудительного применения ограничений PRIMARY KEY для индекса columnstore.|  
|Удаление индекса columnstore.|[DROP INDEX (Transact-SQL)](../../t-sql/statements/drop-index-transact-sql.md)|Для удаления индекса columnstore используется стандартный синтаксис DROP INDEX с индексом сбалансированного дерева. При удалении кластеризованного индекса columnstore таблица columnstore преобразуется в кучу.|  
|Удаление строки из индекса columnstore|[DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md)|Используйте синтаксис [DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md) для удаления строки.<br /><br /> Строка**columnstore** : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] помечает строку как логически удаленную, но не возвращает физическое хранилище для строки до тех пор, пока индекс не будет перестроен.<br /><br /> Строка**deltastore** : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] логически и физически удаляет строку.|  
|Обновление строки в индексе columnstore|[UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)|Используйте синтаксис [UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md) для обновления строки.<br /><br /> Строка**columnstore** :  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] помечает строку как логически удаленную, а затем вставляет обновленную строку в deltastore.<br /><br /> Строка**deltastore** : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обновляет строку в deltastore.|  
|Загрузка данных в индекс columnstore|[Загрузка данных индексов ColumnStore](~/relational-databases/indexes/columnstore-indexes-data-loading-guidance.md)||  
|Принудительное перемещение всех строк из deltastore в columnstore|[ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md) ... REBUILD<br /><br /> [Дефрагментация индексов columnstore](~/relational-databases/indexes/columnstore-indexes-defragmentation.md)|Инструкция ALTER INDEX с параметром REBUILD перемещает все строки в columnstore.|  
|Дефрагментация индекса columnstore|[ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md)|ALTER INDEX … REORGANIZE дефрагментирует индексы columnstore в оперативном режиме.|  
|Слияние таблиц с индексами columnstore.|[MERGE (Transact-SQL)](../../t-sql/statements/merge-transact-sql.md)||  
  
## <a name="see-also"></a>См. также:  
 [Загрузка данных индексов ColumnStore](~/relational-databases/indexes/columnstore-indexes-data-loading-guidance.md)   
 [Сводка функций индексов columnstore по версиям](~/relational-databases/indexes/columnstore-indexes-what-s-new.md)   
 [Производительность запросов индексов columnstore](~/relational-databases/indexes/columnstore-indexes-query-performance.md)   
 [Начало работы с Columnstore для получения операционной аналитики в реальном времени](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)   
 [Индексы сolumnstore для хранилищ данных](~/relational-databases/indexes/columnstore-indexes-data-warehouse.md)   
 [Дефрагментация индексов columnstore](~/relational-databases/indexes/columnstore-indexes-defragmentation.md)  
  
  






