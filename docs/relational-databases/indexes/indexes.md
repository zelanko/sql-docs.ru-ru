---
title: Индексы | Документация Майкрософт
ms.custom: ''
ms.date: 12/21/2016
ms.prod: sql
ms.prod_service: table-view-index, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index types [SQL Server]
ms.assetid: 00863b10-e77c-44c5-8ac2-bb4ac454eec6
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 899bd7aada6364449fa71e9f87839447de73dedd
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "67909675"
---
# <a name="indexes"></a>Индексы
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

## <a name="available-index-types"></a>Доступные типы индексов
В следующей таблице приведен список типов индексов, доступных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а также указаны ссылки на дополнительные сведения.  
  
|Тип индекса|Description|Дополнительные сведения|  
|----------------|-----------------|----------------------------|  
|Хэш|При использовании хэш-индекса доступ к данным осуществляется через хэш-таблицу в памяти. Хэш-индексы используют фиксированный размер памяти, который зависит от числа контейнеров.|[Рекомендации по использованию индексов в таблицах, оптимизированных для памяти](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md)<br /><br /> [Рекомендации по проектированию хэш-индексов](../../relational-databases/sql-server-index-design-guide.md#hash_index)|  
|Некластеризованный индекс, оптимизированный для памяти|Для оптимизированных для памяти некластеризованных индексов потребление памяти является функцией от количества строк и размера ключевых столбцов индекса|[Рекомендации по использованию индексов в таблицах, оптимизированных для памяти](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md)<br /><br /> [Рекомендации по проектированию некластеризованных индексов, оптимизированных для памяти](../../relational-databases/sql-server-index-design-guide.md#inmem_nonclustered_index)|  
|Кластеризованный|Кластеризованный индекс сортирует и хранит строки данных таблицы или представления в порядке, определяемом ключом кластеризованного индекса. Кластеризованный индекс реализуется в виде сбалансированного дерева, которое поддерживает быстрое получение строк по значениям ключа кластеризованного индекса.|[Описание кластеризованных и некластеризованных индексов](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)<br /><br /> [Создание кластеризованных индексов](../../relational-databases/indexes/create-clustered-indexes.md)<br /><br /> [Правила проектирования кластеризованного индекса](../../relational-databases/sql-server-index-design-guide.md#Clustered)|  
|Некластеризованный|Некластеризованный индекс можно определить в таблице или представлении вместе с кластеризованным индексом или в куче. Каждая строка некластеризованного индекса содержит некластеризованное ключевое значение и указатель на строку. Этот указатель определяет строку данных кластеризованного индекса или кучи, содержащую ключевое значение. Строки в индексе хранятся в порядке, определяемом значениями ключа индекса, но до создания кластеризованного индекса в таблице нет никакой гарантии того, что строки данных будут расположены в каком-либо определенном порядке.|[Описание кластеризованных и некластеризованных индексов](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)<br /><br /> [Создание некластеризованных индексов](../../relational-databases/indexes/create-nonclustered-indexes.md)<br /><br /> [Рекомендации по созданию некластеризованных индексов](../../relational-databases/sql-server-index-design-guide.md#Nonclustered)|  
|Уникальная идентификация|Уникальный индекс обеспечивает отсутствие повторяющихся значений ключа индекса, что, в свою очередь, приводит к тому, что каждая строка в таблице или представлении является в каком-то смысле уникальной.<br /><br /> Как кластеризованные, так и некластеризованные индексы могут быть уникальными.|[Создание уникальных индексов](../../relational-databases/indexes/create-unique-indexes.md)<br /><br /> [Правила по созданию уникальных индексов](../../relational-databases/sql-server-index-design-guide.md#Unique)|  
|columnstore|Индекс columnstore в памяти хранит данные и управляет данными с использованием основанного на столбцах хранилища данных и обработки запросов.<br /><br /> Индексы Columnstore подходят для рабочих нагрузок хранилища данных, которые выполняют в основном массовую загрузку и запросы только для чтения. Используйте индекс columnstore для повышения **производительности запросов максимум в 10 раз** относительно традиционного хранилища, основанного на строках, и **повышения эффективности сжатия данных до 7 раз** относительно несжатых данных.|[Руководство по индексам columnstore](../../relational-databases/indexes/columnstore-indexes-overview.md)<br /><br /> [Рекомендации по проектированию индексов columnstore](../../relational-databases/sql-server-index-design-guide.md#columnstore_index)|  
|Индекс с включенными столбцами|Некластеризованный индекс, дополнительно содержащий кроме ключевых столбцов еще и неключевые.|[Создание индексов с включенными столбцами](../../relational-databases/indexes/create-indexes-with-included-columns.md)|  
|Индекс на вычисляемых столбцах|Индекс на столбце, являющемся производным от одного или нескольких других столбцов или нескольких детерминированных источников.|[Индексы для вычисляемых столбцов](../../relational-databases/indexes/indexes-on-computed-columns.md)|  
|Filtered|Оптимизированный некластеризованный индекс, в особенности подходящий для покрытия запросов из хорошо определенного подмножества данных. Он использует предикат фильтра для индексирования части строк в таблице. Хорошо спроектированный отфильтрованный индекс позволяет повысить производительность запросов, снизить затраты на обслуживание и хранение индексов по сравнению с полнотабличными индексами.|[Создание отфильтрованных индексов](../../relational-databases/indexes/create-filtered-indexes.md)<br /><br /> [Рекомендации по проектированию отфильтрованных индексов](../../relational-databases/sql-server-index-design-guide.md#Filtered)|  
|пространственный индекс|Пространственный индекс обеспечивает возможность более эффективного использования определенных операций с пространственными объектами (*пространственными данными*) в столбце типа данных **geometry** . Пространственные индексы снижают количество объектов, к которым должны применяться пространственные операции, требующие больших затрат.|[Общие сведения о пространственных индексах](../../relational-databases/spatial/spatial-indexes-overview.md)|  
|XML|Вырезанное материализованное представление больших двоичных XML-объектов в столбце с типом данных **xml**.|[XML-индексы (SQL Server)](../../relational-databases/xml/xml-indexes-sql-server.md)|  
|Полнотекстовый|Специальный тип функционального индекса, основанный на токене, построенный и поддерживаемый средством полнотекстового поиска (Майкрософт) для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Он обеспечивает эффективную поддержку сложных операций поиска слов в символьных строковых данных.|[Заполнение полнотекстовых индексов](../../relational-databases/search/populate-full-text-indexes.md)|  
  
## <a name="related-content"></a>См. также  
 [Руководство по проектированию индексов SQL Server](../../relational-databases/sql-server-index-design-guide.md)      
 [Параметр SORT_IN_TEMPDB для индексов](../../relational-databases/indexes/sort-in-tempdb-option-for-indexes.md)     
 [Отключение индексов и ограничений](../../relational-databases/indexes/disable-indexes-and-constraints.md)     
 [Включение индексов и ограничений](../../relational-databases/indexes/enable-indexes-and-constraints.md)    
 [Переименование индексов](../../relational-databases/indexes/rename-indexes.md)     
 [Установка параметров индекса](../../relational-databases/indexes/set-index-options.md)     
 [Требования к месту на диске для DDL-операций индекса](../../relational-databases/indexes/disk-space-requirements-for-index-ddl-operations.md)     
 [Реорганизация и перестроение индексов](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)     
 [Указание коэффициента заполнения для индекса](../../relational-databases/indexes/specify-fill-factor-for-an-index.md)     
 [Руководство по архитектуре страниц и экстентов](../../relational-databases/pages-and-extents-architecture-guide.md)     
 [Описание кластеризованных и некластеризованных индексов](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)     
  
