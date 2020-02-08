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
ms.openlocfilehash: 725dbc3306f9ad9616b5cbeca2d96249dca1c4a8
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "74165781"
---
# <a name="getting-started-with-system-versioned-temporal-tables"></a>Приступая к работе c темпоральными таблицами с системным управлением версиями

[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

В зависимости от сценария можно создать новые или изменить существующие темпоральные таблицы с системным управлением версиями, добавив темпоральные атрибуты в существующую схему таблицы. При изменении данных в темпоральной таблице в системе создается журнал версий, видимый для приложений и пользователей. Таким образом, при работе с темпоральной таблицей с системным управлением версиями не требуется переопределять способ изменения таблицы или запроса последнего (фактического) состояния данных.

Кроме обычных инструкций DML и запросов, темпоральные таблицы также предоставляют удобные и простые способы получения сведений из журнала данных с помощью расширенного синтаксиса Transact-SQL. Каждая таблица с системным управлением версиями имеет назначенную таблицу журнала. Она полностью прозрачна для пользователей, если только они не решат оптимизировать производительность рабочей нагрузки или сократить объем хранилища, создав дополнительные индексы или выбрав различные параметры хранения.

На схеме ниже показан типичный рабочий процесс в темпоральных таблицах с системным управлением версиями: ![Начало работы с темпоральными таблицами](../../relational-databases/tables/media/getting-started-with-temporal.png "Начало работы с темпоральными таблицами")

В этом разделе содержится 5 подразделов:

- [Создание темпоральной таблицы с системным управлением версиями](../../relational-databases/tables/creating-a-system-versioned-temporal-table.md)
- [Изменение данных в темпоральной таблице с системным управлением версиями](../../relational-databases/tables/modifying-data-in-a-system-versioned-temporal-table.md)
- [Запрос данных в темпоральной таблице с системным управлением версиями](../../relational-databases/tables/querying-data-in-a-system-versioned-temporal-table.md)
- [Изменение схемы темпоральной таблицы с системным управлением версиями](../../relational-databases/tables/changing-the-schema-of-a-system-versioned-temporal-table.md)
- [Остановка системного управления версиями в темпоральной таблице с системным управлением версиями](../../relational-databases/tables/stopping-system-versioning-on-a-system-versioned-temporal-table.md)

## <a name="next-steps"></a>Дальнейшие действия

- [Темпоральные таблицы](../../relational-databases/tables/temporal-tables.md)
- [Проверка согласованности системной темпоральной таблицы](../../relational-databases/tables/temporal-table-system-consistency-checks.md)
- [Секционирование с помощью темпоральных таблиц](../../relational-databases/tables/partitioning-with-temporal-tables.md)
- [Рекомендации и ограничения для темпоральной таблицы](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)
- [Безопасность темпоральной таблицы](../../relational-databases/tables/temporal-table-security.md)
- [Управление хранением данных журнала в темпоральных таблицах с системным управлением версиями](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)
- [Темпоральные таблицы с системным управлением версиями и таблицы, оптимизированные для памяти](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)
- [Представления и функции метаданных для временной таблицы](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)
