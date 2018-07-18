---
title: Сведения об индексах ColumnStore | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- indexes creation, columnstore
- indexes [SQL Server], columnstore
- columnstore index
- columnstore index, described
- xVelocity, columnstore indexes
ms.assetid: f98af4a5-4523-43b1-be8d-1b03c3217839
caps.latest.revision: 50
author: mikeraymsft
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9cd8b98b2e62dbc11d62e07b9b0d7e2ac3e05c6b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211324"
---
# <a name="columnstore-indexes-described"></a>Columnstore Indexes Described
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] *Индекс columnstore в памяти* хранит данные и управляет ими с помощью хранилища данных на основе столбца и обработки запросов на основе столбца. Индексы Columnstore подходят для рабочих нагрузок хранилища данных, которые выполняют в основном массовую загрузку и запросы только для чтения. Используйте индекс columnstore для повышения **производительности запросов максимум в 10 раз** относительно традиционного хранилища, основанного на строках, и **повышения эффективности сжатия данных до 7 раз** относительно несжатых данных.  
  
> [!NOTE]  
>  Кластеризованный индекс columnstore рассматривается как стандартный для хранения таблиц фактов с большим объемом данных; ожидается, что он будет полезен в большинстве сценариев хранилища данных. Поскольку кластеризованный индекс columnstore может обновляться, рабочая нагрузка может также выполнять большое число операций вставки, обновления и удаления.  
  
## <a name="contents"></a>Содержание  
  
-   [Основы](#basics)  
  
-   [Загрузка данных](#dataload)  
  
-   [Советы по повышению производительности](#performance)  
  
-   [Связанные задачи и разделы](#related)  
  
##  <a name="basics"></a> Основы  
 *columnstore index* — это технология хранения, получения данных и управления ими с помощью формата хранения данных в один столбец, называемого columnstore. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает как кластеризованные и некластеризованные индексы columnstore. В обоих используется одна и та же технология columnstore в памяти, но имеются некоторые различия в целях и в поддерживаемых функциях.  
  
###  <a name="benefits"></a> Преимущества  
 Индексы columnstore подходят для главным образом для запросов только для чтения, которые используют для анализа большие наборы данных. Часто эти запросы используются для рабочих нагрузок хранилищ данных. Индексы columnstore обеспечивают значительное повышение производительности для запросов с полным сканированием таблицы и неоптимально подходят для запросов, которые выполняют поиск конкретного значения.  
  
 Преимущества использования индекса columnstore.  
  
-   Столбцы часто содержат схожие данные, что приводит к высокой степени сжатия.  
  
-   Высокие степени сжатия повышают производительность запросов с помощью малого отпечатка в памяти. В свою очередь, может повышаться производительность запросов, так как [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может выполнять больше операций с запросами и данными в памяти.  
  
-   Новый механизм выполнения запроса, который называется пакетным выполнением. Появление этого режима в SQL Server позволило значительно снизить загрузку ЦП. Выполнение пакета тесно интегрировано и оптимизировано для взаимодействия с форматом хранения columnstore. Выполнение пакета иногда называется выполнением на основе векторов или векторизированным.  
  
-   Часто запросы выбирают только несколько столбцов из таблицы, что сокращает общее число операций ввода-вывода для физического носителя.  
  
### <a name="columnstore-versions"></a>Версии columnstore  
 SQL Server 2012, SQL Server 2012 Parallel Data Warehouse и SQL Server 2014 используют индексы columnstore для ускорения выполнения общих запросов хранилищ данных. В SQL Server 2012 реализованы две новые функции: некластеризованный индекс columnstore и поддержка выполнения запросов на основе вектора, которые используются для обработки данных в единицах, называемых «пакеты». SQL Server 2014 поддерживает функции SQL Server 2012, а также обновленные кластеризованные индексы columnstore.  
  
### <a name="key-characteristics"></a>Ключевые характеристики  
  
||  
|-|  
|**Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].|  
  
 В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], кластеризованный индекс columnstore:  
  
-   Доступен в выпусках Enterprise, Developer и Evaluation.  
  
-   Обновляется.  
  
-   Это основной метод хранения для всей таблицы.  
  
-   Не имеет ключевых столбцов. Все столбцы являются включенными.  
  
-   Является единственным индексом для таблицы. Не поддается объединению с другими индексами.  
  
-   Можно настроить для использования columnstore или архивного сжатия columnstore.  
  
-   Физически не хранит столбцы в отсортированном порядке. Вместо этого хранит данные для повышения сжатия и производительности.  
  
||  
|-|  
|**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].|  
  
 В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], некластеризованный индекс columnstore:  
  
-   Поддерживается индексация подмножества столбцов в кластеризованном индексе или куче. Например, его можно использовать для индексации часто используемых столбцов.  
  
-   Требует дополнительного места для хранения копии столбцов в индексе.  
  
-   Обновляется путем перестроения индекса или входящего и исходящего переключения секций. Не обновляется с помощью операций DML — вставка, обновление и удаление.  
  
-   Может быть совмещен с другими индексами из таблицы.  
  
-   Можно настроить для использования columnstore или архивного сжатия columnstore.  
  
-   Физически не хранит столбцы в отсортированном порядке. Вместо этого хранит данные для повышения сжатия и производительности. Предварительная сортировка данных перед созданием индекса columnstore не является обязательной, но повышает уровень сжатия columnstore.  
  
###  <a name="Concepts"></a> Основные понятия и термины  
 Следующие основные концепции и понятия связаны с индексами columnstore.  
  
 индекс columnstore  
 *columnstore index* — это технология хранения, получения данных и управления ими с помощью формата хранения данных в один столбец, называемого columnstore. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает как кластеризованные и некластеризованные индексы columnstore. В обоих используется одна и та же технология columnstore в памяти, но имеются некоторые различия в целях и в поддерживаемых функциях.  
  
 columnstore  
 *columnstore* — это данные, логически организованные в виде таблицы, состоящей из строк и столбцов, и физически хранящиеся в формате данных в столбцах.  
  
 rowstore  
 *rowstore* — это данные, логически организованные в виде таблицы, состоящей из строк и столбцов, и физически хранящиеся в формате данных в столбцах. Это стандартный способ хранения реляционных данных таблиц.  
  
 группы строк и сегменты столбцов  
 Чтобы добиться высокой производительности и высокого уровня сжатия, индекс columnstore разделяет таблицы в группы строк, называемые группами строк, каждая из которых затем сжимается на уровне столбцов. Число строк в группе строк должно быть достаточно большим, чтобы повысить скорость сжатия, и достаточно малым для использования преимуществ использования операций в памяти.  
  
 группа строк  
 Объект *rowgroup* — это группа строк, сжимаемых в формате columnstore одновременно.  
  
 Сегмент столбца  
 *Сегмент столбца* — это столбец данных из группы строк.  
  
-   Группа строк обычно содержит максимальное число строк для группы строк, 1 048 576 строк.  
  
-   Каждая rowgroup содержит один сегмент столбца для каждого столбца в таблице.  
  
-   Каждый сегмент столбца сжимается одновременно и сохраняется на физическом носителе.  
  
 ![Column segment](../../database-engine/media/sql-server-pdw-columnstore-columnsegment.gif "Column segment")  
  
 некластеризованный индекс columnstore  
 Объект *некластеризованный индекс columnstore* является только для чтения индекс, созданный в существующей кластеризованного индекса или кучи таблицы. Он содержит копию подмножества столбцов вплоть до включения всех столбцов в таблице. Таблица доступна только для чтения, если она содержит некластеризованный индекс columnstore.  
  
 Некластеризованный индекс columnstore дает возможность использования индекса columnstore для выполнения запросов анализа, выполняемых одновременно с операциями только для чтения в исходной таблице.  
  
 ![Некластеризованный индекс columnstore](../../database-engine/media/sql-server-pdw-columnstore-physicalstorage-nonclustered.gif "некластеризованный индекс columnstore")  
  
 кластеризованный индекс columnstore  
 Объект *кластеризованный индекс columnstore* — физическое хранилище для всей таблицы и единственный индекс для таблицы. Кластеризованный индекс можно обновлять. Можно выполнять операции вставки, удаления и обновления индекса, а также выполнять массовую загрузку данных в индекс.  
  
 ![Clustered Columnstore Index](../../database-engine/media/sql-server-pdw-columnstore-physicalstorage.gif "Clustered Columnstore Index")  
  
 Чтобы снизить фрагментацию сегментов столбцов и повысить производительность, индекс columnstore может некоторые данные сохранить временно в таблице, которая называется deltastore, и использовать сбалансированное дерево идентификаторов для удаленных строк. Операции deltastore обрабатываются в фоновом режиме. Для получения правильных результатов запросов кластеризованные индексы columnstore объединяют результаты запроса от columnstore и deltastore.  
  
 deltastore  
 Кластеризованный индекс columnstore только с индексами, *deltastore* является таблицей rowstore, в которой хранятся строки, пока число строк не достаточно большим, чтобы быть перемещены в columnstore. Deltastore используется с кластеризованными индексами columnstore для повышения производительности при загрузке и других операциях DML.  
  
 При крупной массовой загрузке большинство строк переходят непосредственно в columnstore без промежуточного помещения в deltastore. Некоторых строк в конце массовой загрузки может оказаться слишком мало для соответствия минимальному размеру rowgroup, составляющему 102 400 строк. В этом случае последние строки переходят в deltastore вместо columnstore. Для небольших массовых загрузок с менее 102 400 строк, все строки перемещаются напрямую в deltastore.  
  
 Когда объем deltastore достигает максимального числа строк, оно закрывается. Процесс перемещения кортежей выполняет проверку на наличие закрытых групп строк. При обнаружении закрытой группы строк оно уменьшает его и сохраняет в columnstore.  
  
##  <a name="dataload"></a> Загрузка данных  
  
###  <a name="dataload_nci"></a> Загрузка данных в некластеризованном индексе Columnstore  
 Чтобы загрузить данные в некластеризованный индекс columnstore, сначала данные загружаются в стандартную таблицу rowstore сохраненную в виде кучи или кластеризованного индекса и создайте некластеризованный индекс columnstore с [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql).  
  
 ![Загрузка данных в индекс columnstore](../../database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "загрузка данных в индекс columnstore")  
  
 Таблица с некластеризованным индексом columnstore доступна только для чтения до тех пор, пока индекс не будет удален или отключен. Обновить таблицу и некластеризованный индекс columnstore можно путем входящего и исходящего переключения секций. Можно также отключить индекс, обновить таблицу и перестроить индекс.  
  
 Дополнительные сведения см. в разделе [Using Nonclustered Columnstore Indexes](indexes.md)  
  
###  <a name="dataload_cci"></a> Загрузка данных в кластеризованный индекс Columnstore  
 ![Загрузка в кластеризованный индекс columnstore](../../database-engine/media/sql-server-pdw-columnstore-loadprocess.gif "Загрузка в кластеризованный индекс columnstore")  
  
 Как видно на диаграмме, чтобы загрузить данные в кластеризованный индекс columnstore, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:  
  
1.  Вставляет rowgroup максимального размера непосредственно в columnstore. По мере загрузки данных компонент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] назначает строки данных в порядке FIFO в открытую группу строк.  
  
2.  Для каждой группы строк после достижения максимального размера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:  
  
    1.  Отмечает rowgroup как CLOSED.  
  
    2.  Обходит deltastore.  
  
    3.  Сжимает каждый сегмент столбца в rowgroup сжатием columnstore.  
  
    4.  Физически сохраняет каждый сжатый сегмент столбца в columnstore.  
  
3.  Вставляет оставшиеся строки в columnstore или deltastore следующим образом.  
  
    1.  Если число строк удовлетворяет требованию к минимальному числу строк для rowgroup, строки добавляются к columnstore.  
  
    2.  Если число строк меньше минимального числа строк для rowgroup, строки добавляются к deltastore.  
  
 Дополнительные сведения о задачах и процессах deltastore см. в разделе [Using Clustered Columnstore Indexes](../../database-engine/using-clustered-columnstore-indexes.md)  
  
##  <a name="performance"></a> Советы по повышению производительности  
  
### <a name="plan-for-enough-memory-to-create-columnstore-indexes-in-parallel"></a>Планирование достаточного объема памяти для параллельного создания индексов columnstore  
 Создание индекса columnstore по умолчанию является параллельно выполняемой операцией, если ресурсы памяти неограниченны. При создании индекса параллельно требуется больше памяти, чем при последовательном создании индекса. При достаточном объеме памяти создание индекса columnstore выполняется в 1,5 раза дольше, чем создание сбалансированного дерева для тех же столбцов.  
  
 Объем памяти, необходимый для создания индекса columnstore, зависит от количества столбцов, числа столбцов строкового типа, степени параллелизма (DOP) и характеристик данных. Например, если в таблице есть менее миллиона строк, то SQL Server будет использовать всего один поток для создания индекса columnstore.  
  
 Если в таблице более миллиона строк, но SQL Server не может получить объем памяти, достаточный для создания индекса с помощью MAXDOP, то SQL Server автоматически уменьшит MAXDOP в соответствии с наличием памяти.  В некоторых случаях необходимо уменьшить DOP до одного для создания индекса в условиях нехватки памяти.  
  
##  <a name="related"></a> Связанные задачи и разделы  
  
### <a name="nonclustered-columnstore-indexes"></a>Некластеризованные индексы columnstore  
 Общие задачи, см. в разделе [Using Nonclustered Columnstore Indexes](../../database-engine/using-nonclustered-columnstore-indexes.md).  
  
-   [CREATE COLUMNSTORE INDEX (Transact-SQL)](/sql/t-sql/statements/create-columnstore-index-transact-sql)  
  
-   [ALTER INDEX &#40;Transact-SQL&#41; ](/sql/t-sql/statements/alter-index-transact-sql) с параметром REBUILD.  
  
-   [DROP INDEX (Transact-SQL)](/sql/t-sql/statements/drop-index-transact-sql)  
  
### <a name="clustered-columnstore-indexes"></a>Кластеризованные индексы columnstore  
 Общие задачи, см. в разделе [Using Clustered Columnstore Indexes](../../database-engine/using-clustered-columnstore-indexes.md).  
  
-   [СОЗДАТЬ КЛАСТЕРИЗОВАННЫЙ индекс COLUMNSTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)  
  
-   [ALTER INDEX &#40;Transact-SQL&#41; ](/sql/t-sql/statements/alter-index-transact-sql) с параметром REBUILD или REORGANIZE.  
  
-   [DROP INDEX (Transact-SQL)](/sql/t-sql/statements/drop-index-transact-sql)  
  
-   [INSERT (Transact-SQL)](/sql/t-sql/statements/insert-transact-sql)  
  
-   [UPDATE (Transact-SQL)](/sql/t-sql/queries/update-transact-sql)  
  
-   [DELETE (Transact-SQL)](/sql/t-sql/statements/delete-transact-sql)  
  
### <a name="metadata"></a>Метаданные  
 Все столбцы в индексе columnstore хранятся в метаданных как включенные столбцы. Индекс columnstore не имеет ключевых столбцов.  
  
-   [sys.indexes (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)  
  
-   [sys.index_columns (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-index-columns-transact-sql)  
  
-   [sys.partitions (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-partitions-transact-sql)  
  
-   [sys.column_store_segments (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-column-store-segments-transact-sql)  
  
-   [sys.column_store_dictionaries &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql)  
  
-   [sys.column_store_row_groups &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql)  
  
  
