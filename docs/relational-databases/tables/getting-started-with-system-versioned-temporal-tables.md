---
title: Начало работы c темпоральными таблицами с системным управлением версиями | Документация Майкрософт
ms.custom: ''
ms.date: 03/28/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: d431f216-82cf-4d97-825e-bb35d3d53a45
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0bf81a84acbec65334ec02d7bd358215f6a0b0ea
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68016352"
---
# <a name="getting-started-with-system-versioned-temporal-tables"></a>Приступая к работе c темпоральными таблицами с системным управлением версиями
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  В зависимости от сценария можно создать новые или изменить существующие темпоральные таблицы с системным управлением версиями, добавив темпоральные атрибуты в существующую схему таблицы.   
При изменении данных в темпоральной таблице в системе создается журнал версий, видимый для приложений и пользователей. Таким образом, при работе с темпоральной таблицей с системным управлением версиями не требуется переопределять способ изменения таблицы или запроса последнего (фактического) состояния данных.   
Кроме обычных инструкций DML и запросов, темпоральные таблицы также предоставляют удобные и простые способы получения сведений из журнала данных с помощью расширенного синтаксиса Transact-SQL.   
Каждая таблица с системным управлением версиями имеет назначенную таблицу журнала. Она полностью прозрачна для пользователей, если только они не решат оптимизировать производительность рабочей нагрузки или сократить объем хранилища, создав дополнительные индексы или выбрав различные параметры хранения.    
На схеме ниже показан типичный рабочий процесс в темпоральных таблицах с системным управлением версиями:   
![Начало работы с темпоральными таблицами](../../relational-databases/tables/media/getting-started-with-temporal.png "Начало работы с темпоральными таблицами")  
  
 В этом разделе содержится 5 подразделов:  
  
-   [Создание темпоральной таблицы с системным управлением версиями](../../relational-databases/tables/creating-a-system-versioned-temporal-table.md)  
  
-   [Изменение данных в темпоральной таблице с системным управлением версиями](../../relational-databases/tables/modifying-data-in-a-system-versioned-temporal-table.md)  
  
-   [Запрос данных в темпоральной таблице с системным управлением версиями](../../relational-databases/tables/querying-data-in-a-system-versioned-temporal-table.md)  
  
-   [Изменение схемы темпоральной таблицы с системным управлением версиями](../../relational-databases/tables/changing-the-schema-of-a-system-versioned-temporal-table.md)  
  
-   [Остановка системного управления версиями в темпоральной таблице с системным управлением версиями](../../relational-databases/tables/stopping-system-versioning-on-a-system-versioned-temporal-table.md)  
  
## <a name="see-also"></a>См. также:  
 [Темпоральные таблицы](../../relational-databases/tables/temporal-tables.md)   
 [Проверка согласованности системной темпоральной таблицы](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [Секционирование с помощью темпоральных таблиц](../../relational-databases/tables/partitioning-with-temporal-tables.md)   
 [Рекомендации и ограничения для темпоральной таблицы](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)   
 [Безопасность темпоральных таблиц](../../relational-databases/tables/temporal-table-security.md)   
 [Управление хранением данных журнала в темпоральных таблицах с системным управлением версиями](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Темпоральные таблицы с системным управлением версиями и таблицы, оптимизированные для памяти](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Представления и функции метаданных для временной таблицы](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  
