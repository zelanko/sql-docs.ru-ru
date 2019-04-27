---
title: Использование кластеризованных индексов Columnstore | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 5af6b91c-724f-45ac-aff1-7555014914f4
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1e65c3e277eb9a3e5e3703525b9c1ac06b423c96
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62773745"
---
# <a name="using-clustered-columnstore-indexes"></a>Использование кластеризованных индексов columnstore
  Задачи при использовании кластеризованных индексов columnstore в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Общие сведения об индексах columnstore см. в разделе [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md).  
  
 Дополнительные сведения о кластеризованных индексах columnstore см. в разделе [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md).  
  
## <a name="contents"></a>Содержание  
  
-   [Создайте кластеризованный индекс Columnstore](#create)  
  
-   [Удаление кластеризованного индекса Columnstore](#drop)  
  
-   [Загрузка данных в кластеризованный индекс Columnstore](#load)  
  
-   [Изменение данных в кластеризованном индексе Columnstore](#change)  
  
-   [Перестроение кластеризованного индекса Columnstore](#rebuild)  
  
-   [Реорганизация кластеризованного индекса Columnstore](#reorganize)  
  
##  <a name="create"></a> Создайте кластеризованный индекс Columnstore  
 Чтобы создать кластеризованный индекс columnstore, сначала создайте таблицу rowstore как кучу или кластеризованный индекс и воспользуйтесь [создать КЛАСТЕРИЗОВАННЫЙ индекс COLUMNSTORE &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-columnstore-index-transact-sql) инструкцию, чтобы преобразовать таблицу кластеризованный Индекс ColumnStore. Если кластеризованный индекс columnstore должен иметь то же имя, что и кластеризованный индекс, используйте параметр DROP_EXISTING.  
  
 В этом примере создается таблица как куча, затем преобразуется в кластеризованный индекс с именем columnstore cci_Simple. В результате таблица rowstore становится таблицей columnstore.  
  
```  
CREATE TABLE T1(  
    ProductKey [int] NOT NULL,   
    OrderDateKey [int] NOT NULL,   
    DueDateKey [int] NOT NULL,   
    ShipDateKey [int] NOT NULL);  
GO  
CREATE CLUSTERED COLUMNSTORE INDEX cci_T1 ON T1;  
GO  
```  
  
 Дополнительные примеры см. в разделе "Примеры" в [CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql).  
  
##  <a name="drop"></a> Удаление кластеризованного индекса Columnstore  
 Используйте [DROP INDEX &#40;Transact-SQL&#41; ](/sql/t-sql/statements/drop-index-transact-sql) инструкцию, чтобы удалить кластеризованный индекс columnstore. Эта операция удаляет индекс columnstore и преобразует таблицу columnstore в кучу rowstore.  
  
##  <a name="load"></a> Загрузка данных в кластеризованный индекс Columnstore  
 Можно добавлять данные к существующим кластеризованным индексам columnstore с помощью любого из стандартных методов загрузки.  Например массовой загрузки bcp средства, службы Integration Services и INSERT... SELECT могут загружать данные в кластеризованный индекс columnstore.  
  
 Кластеризованные индексы columnstore используют deltastore, чтобы исключить фрагментацию сегментов столбца в columnstore.  
  
### <a name="loading-into-a-partitioned-table"></a>Загрузка в секционированную таблицу  
 Для секционированных данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] сначала назначает каждую строку секции, а затем выполняет операции columnstore для данных в секции. Каждая секция имеет собственную rowgroups и как минимум одно deltastore.  
  
### <a name="deltastore-loading-scenarios"></a>Сценарии загрузки Deltastore  
 Строки накапливаются в каждом deltastore до тех пор, пока число строк не достигнет максимального количества строк, допустимого для rowgroup. Когда deltastore будет содержать максимальное количество строк на rowgroup, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] пометит rowgroup как «ЗАКРЫТО». Фоновый процесс, называется «кортежей», находит CLOSED rowgroup и перемещает в columnstore, где группа строк сжимается в сегменты и сегменты столбцов сохраняются в columnstore.  
  
 Для каждого кластеризованного индекса columnstore может быть несколько deltastore.  
  
-   Если deltastore блокировано, компонент [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] пытается получить блокировку на другом deltastore. Если доступных deltastore нет, компонент [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] создает новое deltastore.  
  
-   Для секционированной таблицы может быть одно или несколько deltastore для каждой секции.  
  
 Только для кластеризованных индексов columnstore в следующих сценариях показывается, когда загруженные строки перейдут непосредственно в columnstore, а когда в deltastore.  
  
 В примере каждая rowgroup может иметь 102 400-1 048 576 строк на rowgroup.  
  
|Строки для массовой загрузки|Строки, добавленные в Columnstore|Строки, добавленные в Deltastore|  
|-----------------------|-----------------------------------|----------------------------------|  
|102,000|0|102,000|  
|145,000|145,000<br /><br /> Размер группы строк: 145,000|0|  
|1,048,577|1 048 576<br /><br /> Размер группы строк: 1 048 576.|1|  
|2,252,152|2,252,152<br /><br /> Размеры групп строк: 1 048 576, 1 048 576, 155 000.|0|  
  
 В следующем примере показаны результаты загрузки 1 048 577 строк в секцию. Результаты показывают наличие одной СЖАТОЙ rowgroup в columnstore (в виде сжатых сегментов столбцов) и 1 строки в deltastore.  
  
```  
SELECT * FROM sys.column_store_row_groups  
```  
  
 ![Группа строк и разностная группа строк для пакетной загрузки](../../2014/database-engine/media/sql-server-pdw-columnstore-batchload.gif "Группа строк и разностная группа строк для пакетной загрузки")  
  

  
##  <a name="change"></a> Изменение данных в кластеризованном индексе Columnstore  
 Кластеризованные индексы columnstore поддерживают операции DML вставки, обновления и удаления.  
  
 Используйте [вставить &#40;Transact-SQL&#41; ](/sql/t-sql/statements/insert-transact-sql) вставить строку. Строка будет добавлена в deltastore.  
  
 Используйте синтаксис [DELETE (Transact-SQL)](/sql/t-sql/statements/delete-transact-sql) для удаления строки.  
  
-   Если строка находится в columnstore, компонент [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] помечает строку как логически удаленную, но не возвращает физическое хранилище для строки до тех пор, пока индекс не будет перестроен.  
  
-   Если строка содержится в deltastore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] логически и физически удаляет ее.  
  
 Используйте синтаксис [UPDATE (Transact-SQL)](/sql/t-sql/queries/update-transact-sql) для обновления строки.  
  
-   Если строка содержится в columnstore, компонент [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] помечает строку как логически удаленную, а затем вставляет обновленную строку в deltastore.  
  
-   Если строка находится в deltastore, компонент [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] обновляет строку в deltastore.  
  
##  <a name="rebuild"></a> Перестроение кластеризованного индекса Columnstore  
 Используйте [CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-columnstore-index-transact-sql) или [ALTER INDEX &#40;Transact-SQL&#41; ](/sql/t-sql/statements/alter-index-transact-sql) для полного перестроения существующего кластеризованного индекса. Кроме того, можно использовать инструкцию ALTER INDEX... REBUILD, чтобы перестроить конкретную секцию.  
  
### <a name="rebuild-process"></a>Процесс перестроения  
 Перестроение кластеризованного индекса columnstore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:  
  
-   Приобретает монопольную блокировку на таблице или секции на то время, как происходит перестроение.  Во время перестроения данные находятся в автономном режиме и недоступны.  
  
-   Дефрагментирует таблицу columnstore, физически удаляя строки, которые были логически удалены из таблиц; удаленные байты освобождают место на физическом носителе.  
  
-   Объединяет данные rowstore в deltastore с данными в columnstore перед перестроением индекса. После завершения перестроения все данные хранятся в формате columnstore, а deltastore пустует.  
  
-   Повторно сжимает все данные в columnstore. Во время перестроения существуют две копии индекса columnstore. После завершения перестроения [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] удаляет исходный индекс columnstore.  
  
### <a name="recommendations-for-rebuilding-a-clustered-columnstore-index"></a>Рекомендации по перестраиванию кластеризованного индекса Columnstore  
 Перестраивание кластеризованного индекса columnstore полезно для устранения фрагментации и перемещения всех строк в columnstore. Предлагаются следующие рекомендации.  
  
-   Перестраивайте секцию, а не всю таблицу.  
  
    1.  Если индекс большой, то перестроение всей таблицы занимает много времени и на диске должно хватать места для сохранения дополнительной копии во время перестроения. Обычно бывает необходимо перестроить только недавно использованную секцию.  
  
    2.  Для секционированных таблиц нет необходимости перестраивать весь индекс columnstore, поскольку фрагментация вероятна только в секциях, которые были недавно изменены. Таблицы фактов и большие таблицы измерений обычно бывают секционированы для выполнения операций резервного копирования и управления с фрагментами данных таблицы.  
  
-   Перестраивайте секцию после масштабных операций DML.  
  
     Перестроение секции дефрагментирует ее и уменьшит занимаемое место на диске. Перестроение удалит все строки из columnstore, помеченные для удаления, и переместит все строки из deltastore в columnstore.  
  
-   Перестраивайте секцию после загрузки данных.  
  
     Это гарантирует, что все данные будут храниться в columnstore. Если одновременно выполняется несколько загрузок, то в каждой секции может образоваться несколько deltastore. Перестроение переместит все строки из deltastore в columnstore.  
  
##  <a name="reorganize"></a> Реорганизация кластеризованного индекса Columnstore  
 Реорганизация кластеризованный индекса columnstore перемещает все ЗАКРЫТЫЕ rowgroups в columnstore. Для реорганизации, использовать [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)с параметром REORGANIZE.  
  
 Реорганизация не требуется для перемещения ЗАКРЫТЫХ rowgroup в columnstore. Процесс перемещения кортежей в конечном счете находит все группы строк CLOSED и перемещает их. Но процесс перемещения кортежей является однопотоковым и может не перемещать группы строк достаточно быстро применительно к конкретной рабочей нагрузке.  
  
### <a name="recommendations-for-reorganizing"></a>Рекомендации по реорганизации  
 Когда реорганизовать кластеризованный индекс columnstore:  
  
-   Реорганизуйте кластеризованный индекс columnstore после одной или нескольких загрузок данных для получения выигрыша в производительности запросов как можно быстрее. Реорганизация изначально потребует дополнительных ресурсов ЦП для сжатия данных, что может снизить общую производительность системы. Однако после сжатия данных производительность запросов может возрасти.  
  
  
