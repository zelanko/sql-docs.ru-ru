---
title: "Архитектура индексов columnstore | Документация Майкрософт"
ms.custom: 
ms.date: 01/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: indexes
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96b8e884-8244-425f-b856-72a8ff6895a6
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 835e3acd76972eef01b4d286cbc1f6ecf6fac605
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="columnstore-indexes---architecture"></a>Архитектура индексов columnstore
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Здесь вы узнаете об архитектуре индексов columnstore. Ознакомившись с базовыми принципами, вы сможете приступить к изучению других руководств по индексам columnstore, в которых рассматривается их эффективное использование.

## <a name="data-storage-uses-columnstore-and-rowstore-compression"></a>Данные хранятся в форматах columnstore и rowstore
В обсуждениях индексов columnstore для обозначения формата хранения данных используются термины *rowstore* и *columnstore* .  Индексы columnstore используют оба типа хранилища.

 ![Clustered Columnstore Index](../../relational-databases/indexes/media/sql-server-pdw-columnstore-physicalstorage.gif "Clustered Columnstore Index")

- **columnstore** — это данные, логически организованные в виде таблицы, состоящей из строк и столбцов, и физически хранящиеся в формате данных в столбцах.
  
Индекс columnstore физически сохраняет большинство данных в формате columnstore. В этом формате данные представлены столбцами, которые можно сжимать и распаковывать. Не нужно распаковывать в каждой строке значения, не соответствующие запросам. Благодаря этому можно быстро просматривать целые столбцы большой таблицы. 

- **rowstore** — это данные, логически организованные в виде таблицы, состоящей из строк и столбцов, и физически хранящиеся в формате данных в столбцах. Это стандартный способ хранения реляционных данных таблиц, например индекса кучи или кластеризованного индекса сбалансированного дерева.

Индекс columnstore также физически сохраняет некоторые строки в формате rowstore, который называется deltastore. deltastore также называют разностными группами строк. Это место хранения строк, которых слишком мало для сжатия в columnstore. Каждая разностная группа строк реализована в виде кластеризованного индекса сбалансированного дерева. 

- **deltastore** — это место хранения строк, которых слишком мало для сжатия в columnstore. deltastore представляет собой rowstore. 
  
## <a name="operations-are-performed-on-rowgroups-and-column-segments"></a>Операции выполняются в сегментах групп строк и столбцов

Индексы columnstore группируют строки в управляемые элементы. Каждый из этих элементов называется группой строк. Для лучшей производительности число строк в группе строк должно быть достаточно большим, чтобы повысить скорость сжатия, и достаточно малым для использования преимуществ операций в памяти.

* **Группа строк** представляет собой группу строк, в которых индекс columnstore выполняет операции управления и сжатия. 

В группах строк индекс columnstore может выполнять следующие операции:

* сжимает группы строк в columnstore (выполняется в каждом сегменте столбца в группе строк);
* объединяет группы строк во время операции ALTER INDEX REORGANIZE;
* создает новые группы строк во время операции ALTER INDEX REBUILD;
* отправляет отчеты об исправности и фрагментации групп строк в динамических административных представлениях.

deltastore состоит из одной или нескольких групп строк, которые называются разностными группами строк. Каждая разностная группа строк является кластеризованным индексом сбалансированного дерева, где хранятся строки, которых слишком мало для сжатия в columnstore.  

* **Разностная группа строк** — это кластеризованный индекс сбалансированного дерева, в котором хранятся небольшие массовые загрузки и вставки до тех пор, пока группа строк не будет содержать 1 048 576 строк или пока индекс не перестроится.  Если разностная группа строк содержит 1 048 576 строк, она отмечается как закрытая и находится в ожидании сжатия в формат columnstore процессом перемещения кортежей. 


Каждый столбец содержит несколько собственных значений в каждой группе строк. Эти значения называются сегментами столбцов. Когда индекс columnstore сжимает группу строк, он отдельно сжимает каждый сегмент столбца. Чтобы распаковать целый столбец, индексу columnstore необходимо распаковать только один сегмент столбца из каждой группы строк.

* **Сегмент столбца** представляет собой часть значений столбца в каждой группе строк. Каждая rowgroup содержит один сегмент столбца для каждого столбца в таблице. Каждый столбец содержит один сегмент столбца в каждой группе строк. 
  
 ![Column segment](../../relational-databases/indexes/media/sql-server-pdw-columnstore-columnsegment.gif "Column segment")  
 
## <a name="small-loads-and-inserts-go-to-the-deltastore"></a>Небольшие загрузки и вставки переносятся в deltastore
Индекс columnstore улучшает сжатие и производительность columnstore за счет сжатия как минимум 102 400 строк в индекс columnstore за раз. Чтобы выполнить массовое сжатие строк, индекс columnstore накапливает небольшие загрузки и вставки в deltastore. Операции deltastore обрабатываются в фоновом режиме. Для получения правильных результатов запросов кластеризованные индексы columnstore объединяют результаты запроса от columnstore и deltastore. 

Переход строк в deltastore происходит в следующих случаях:
* если они вставлены с помощью инструкции INSERT INTO VALUES;
* если по завершении массовой загрузки они насчитывают меньше 102 400 строк;
* в случае обновления (каждое обновление реализуется как операция удаления или вставки).

В deltastore также хранится список идентификаторов для удаленных строк, которые были помечены как удаленные, но еще не удалены физически из columnstore. 

## <a name="when-delta-rowgroups-are-full-they-get-compressed-into-the-columnstore"></a>Когда разностные группы строк заполнены, они сжимаются в columnstore

Прежде чем сжать группу строк в columnstore, кластеризованные индексы собирают 1 048 576 строк в каждой разностной группе строк. Это повышает степень сжатия индекса columnstore. Когда число строк в разностной группе достигает 1 048 576, индекс columnstore отмечает группу строк как закрытую. Фоновый процесс, называемый *перемещением кортежей*, находит каждую закрытую группу строк и сжимает ее в columnstore. 

Чтобы перестроить или реорганизовать индекс, вы можете принудительно сжать разностную группу строк в columnstore с помощью [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md).  Обратите внимание, что если во время сжатия наблюдается нехватка памяти, индекс columnstore может уменьшить число строк в сжимаемой группе строк.

## <a name="each-table-partition-has-its-own-rowgroups-and-delta-rowgroups"></a>Каждая секция таблицы содержит собственные группы строк и разностные группы

Понятие секционирования одинаково для двух кластеризованных индексов — индекса кучи и columnstore. При секционировании таблица разделяется на небольшие группы строк в соответствии с диапазоном значений столбцов. Это часто используется для управления данными. Например, вы можете создать секцию для каждого года данных, а затем использовать переключение секций, чтобы архивировать данные для получения более экономичного хранилища. Переключение секций выполняется для индексов columnstore и упрощает перемещение секции данных в другое расположение.

Группы строк всегда определяются в пределах секции таблицы. При секционировании индекса columnstore каждая секция получает свои собственные сжатые группы строк и разностные группы строк.

### <a name="each-partition-can-have-multiple-delta-rowgroups"></a>Каждая секция может содержать несколько разностных групп строк
Каждая секция может содержать несколько разностных групп строк. Когда индексу columnstore требуется добавить данные в разностную группу строк, которая заблокирована, он попытается получить блокировку в другой разностной группе строк. Если доступные разностные группы строк отсутствуют, индекс columnstore создаст новую группу.  Например, у таблицы с 10 секциями может быть 20 и более разностных групп строк. 

  
## <a name="you-can-combine-columnstore-and-rowstore-indexes-on-the-same-table"></a>Вы можете объединить индексы columnstore и rowstore в одной таблице
Некластеризованный индекс содержит копию всех или части строк и столбцов в базовой таблице. Индекс определяется как один или несколько столбцов таблицы и включает дополнительное условие для фильтрации строк. 

Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], можно создавать обновляемый некластеризованный индекс columnstore в таблице rowstore. Индекс columnstore сохраняет копию данных, так что вам обязательно потребуется дополнительное хранилище. Тем не менее данные в индексе columnstore будут сжаты до меньшего размера, чем это требуется для таблицы rowstore.  Таким образом, вы сможете выполнять аналитику на основе индекса columnstore и транзакции на основе индекса rowstore одновременно. Хранилище столбцов обновляется при каждом изменении данных в таблице rowstore, поэтому оба индекса работают с одними и теми же данными.  
  
 Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], индекс columnstore может включать один или несколько некластеризованных индексов rowstore. Это обеспечивает эффективность поиска по таблицам на основе базового индекса columnstore. Кроме того, появляется доступ к другим возможностям. Например, можно принудительно задать ограничение PRIMARY KEY, применив к таблице rowstore ограничение UNIQUE. Поскольку неуникальное значение в таблицу rowstore не вставляется, SQL Server не может вставить значение в columnstore.  
 

## <a name="metadata"></a>Метаданные  
Используйте приведенные ниже представления метаданных, чтобы увидеть атрибуты индексов columnstore. В некоторых из этих представлений содержатся дополнительные сведения об архитектуре.

Обратите внимание, что все столбцы в индексе columnstore хранятся в метаданных как включенные столбцы. Индекс columnstore не имеет ключевых столбцов.  
  
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
  
|  


## <a name="next-steps"></a>Следующие шаги
 Руководство по разработке индексов columnstore см. в [этой статье](../../relational-databases/indexes/columnstore-indexes-design-guidance.md).

