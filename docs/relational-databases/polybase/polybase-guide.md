---
title: Что такое PolyBase? | Документы Майкрософт
ms.date: 06/10/2019
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: polybase
ms.topic: overview
f1_keywords:
- PolyBase
- PolyBase, guide
helpviewer_keywords:
- PolyBase
- PolyBase, overview
- Hadoop import
- Hadoop export
- Hadoop export, PolyBase overview
- Hadoop import, PolyBase overview
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=sqlallproducts-allversions||>=aps-pdw-2016||=azure-sqldw-latest'
ms.openlocfilehash: 4cea1e73dc2bc19add94a24c7a4f504c4d9e1224
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66836341"
---
# <a name="what-is-polybase"></a>Что такое PolyBase?

[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]

<!--SQL Server 2016/2017-->
::: moniker range="= sql-server-2016 || = sql-server-2017 || >= aps-pdw-2016 || = azure-sqldw-latest"

PolyBase позволяет экземпляру SQL Server 2016 обрабатывать запросы Transact-SQL на считывание данных из Hadoop. Этот запрос можно также использовать для доступа к реляционным таблицам в SQL Server. PolyBase также позволяет применять этот запрос для объединения данных из Hadoop и SQL Server. В SQL Server подключение к Hadoop обеспечивают [внешние таблицы](../../t-sql/statements/create-external-table-transact-sql.md) или [внешний источник данных](../../t-sql/statements/create-external-data-source-transact-sql.md).

![Логическая схема использования PolyBase](../../relational-databases/polybase/media/polybase-logical.png "логическая схема использования PolyBase")

PolyBase отправляет некоторые вычисления на узел Hadoop, чтобы оптимизировать общий запрос. Но PolyBase обеспечивает внешний доступ не только к Hadoop. Поддерживаются и другие неструктурированные нереляционные таблицы, например текстовые файлы с разделителями.

> [!TIP]
> В SQL Server 2019 CTP 2.0 представлены новые соединители для PolyBase, включая SQL Server, Oracle, Teradata и MongoDB. Дополнительные сведения см. в [документации по PolyBase для SQL Server 2019 CTP 2.0](polybase-guide.md?view=sql-server-ver15).

::: moniker-end
<!--SQL Server 2019-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

PolyBase позволяет экземпляру SQL Server обрабатывать запросы Transact-SQL, которые считывают данные из внешних источников. SQL Server 2016 и более поздних версий может получать доступ к внешним данным в Hadoop и хранилище BLOB-объектов Azure. Начиная с SQL Server 2019 CTP 2.0 PolyBase можно использовать для доступа к внешним данным в [SQL Server](polybase-configure-sql-server.md), [Oracle](polybase-configure-oracle.md), [Teradata](polybase-configure-teradata.md) и [MongoDB](polybase-configure-mongodb.md).

Те же запросы, которые обращаются к внешним данным, могут работать с реляционными таблицами в вашем экземпляре SQL Server. Это позволяет объединять данные из внешних источников с важными реляционными данными в вашей базе данных. В SQL Server подключение к Hadoop обеспечивают [внешние таблицы](../../t-sql/statements/create-external-table-transact-sql.md) или [внешний источник данных](../../t-sql/statements/create-external-data-source-transact-sql.md).

PolyBase отправляет некоторые вычисления на узел Hadoop, чтобы оптимизировать общий запрос. Но PolyBase обеспечивает внешний доступ не только к Hadoop. Поддерживаются и другие неструктурированные нереляционные таблицы, например текстовые файлы с разделителями.

::: moniker-end

### <a name="supported-sql-products-and-services"></a>Поддерживаемые продукты и службы SQL

PolyBase предоставляет одинаковые функции для следующих продуктов SQL от корпорации Майкрософт:

- SQL Server 2016 и более поздние версии (только Windows);
- Analytics Platform System (прежнее название — Parallel Data Warehouse);
- Хранилище данных SQL Azure

### <a name="azure-integration"></a>Интеграция с Azure

Запросы T-SQL на основе PolyBase также можно использовать для импорта данных из хранилища BLOB-объектов Azure и экспорта данных в него. Кроме того, PolyBase позволяет Хранилищу данных SQL Azure импортировать данные из хранилища BLOB-объектов Azure и Azure Data Lake Store, а также экспортировать в них данные.

## <a name="why-use-polybase"></a>Зачем нужна технология PolyBase

Раньше было гораздо сложнее объединить данные SQL Server с внешними данными. Для этого применялось два неэффективных способа:

- передать часть данных, чтобы все данные были в том или ином формате;
- запросить данные из двух источников, а затем написать пользовательскую логику запроса для объединения и интеграции данных на уровне клиента.

В PolyBase вместо таких неэффективных способов объединения данных применяется T-SQL.

Проще говоря, PolyBase не требует установки дополнительного программного обеспечения в среде Hadoop. При запросе внешних данных используется такой же синтаксис T-SQL, как и при запросе таблицы базы данных. Все вспомогательные действия, реализуемые PolyBase, выполняются прозрачно. Автору запроса не требуется знать, как работает Hadoop.

### <a name="polybase-uses"></a>Варианты использования PolyBase

PolyBase поддерживает перечисленные ниже сценарии в SQL Server.

- **Запрашивать данные, хранящиеся в Hadoop, из SQL Server или PDW.** Пользователи хранят данные в более экономичных распределенных и масштабируемых системах, таких как Hadoop. PolyBase позволяет легко запрашивать данные с помощью T-SQL.

- **Запрашивать данные, хранящиеся в хранилище BLOB-объектов Azure.** Данные для использования службами Azure удобно хранить в хранилище BLOB-объектов Azure.  PolyBase позволяет легко обращаться к данным с помощью T-SQL.

- **Импорт данных из Hadoop, хранилища BLOB-объектов Azure или Azure Data Lake Store.** Используйте скорость технологии Microsoft SQL columnstore и возможности анализа, импортируя данные из Hadoop, хранилища BLOB-объектов Azure или Azure Data Lake Store в реляционные таблицы. Нет необходимости в отдельном средстве ETL или импорта.

- **Экспортировать данные в Hadoop, хранилище BLOB-объектов Azure или Azure Data Lake Store.** Архивация данных в Hadoop, хранилище BLOB-объектов Azure или Azure Data Lake Store позволяет создать экономичное хранилище и обеспечить его подключение к сети для удобного доступа к данным.

- **Интегрироваться со средствами бизнес-аналитики.** Можно использовать PolyBase со средствами бизнес-аналитики и стеком технологий анализа Майкрософт, а также применять любые сторонние средства, совместимые с SQL Server.

## <a name="performance"></a>Производительность

- **Принудительная отправка вычислений в Hadoop.** Оптимизатор запросов принимает решение принудительно отправить вычисления в Hadoop, если это улучшит производительность запросов.  Для принятия такого решения он использует статистику из внешних таблиц. При включении вычислений создаются задания MapReduce и применяются распределенные вычислительные ресурсы Hadoop.

- **Масштабирование вычислительных ресурсов.** Для повышения производительности запросов можно использовать [группы горизонтального масштабирования PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md)в SQL Server. Это обеспечивает параллельную передачу данных между экземплярами SQL Server и узлами Hadoop, а также добавляет вычислительные ресурсы для работы с внешними данными.

<!--SQL Server 2016/2017-->
::: moniker range="=sql-server-2016||=sql-server-2017"

## <a name="next-steps"></a>Следующие шаги

Прежде чем использовать PolyBase, необходимо [установить компонент PolyBase](polybase-installation.md). Затем ознакомьтесь со следующими руководствами по настройке в зависимости от источника данных:

- [Hadoop](polybase-configure-hadoop.md)
- [Хранилище BLOB-объектов Azure](polybase-configure-azure-blob-storage.md)

::: moniker-end
<!--SQL Server 2019-->
::: moniker range=">= sql-server-linux-ver15||>= sql-server-ver15||=sqlallproducts-allversions"

## <a name="next-steps"></a>Следующие шаги

Прежде чем использовать PolyBase, необходимо [установить компонент PolyBase](polybase-installation.md). Затем ознакомьтесь со следующими руководствами по настройке в зависимости от источника данных:
- [Hadoop](polybase-configure-hadoop.md)
- [Хранилище BLOB-объектов Azure](polybase-configure-azure-blob-storage.md)
- [SQL Server](polybase-configure-sql-server.md)
- [Oracle;](polybase-configure-oracle.md)
- [Teradata](polybase-configure-teradata.md)
- [MongoDB](polybase-configure-mongodb.md)
- [Универсальные типы ODBC](../../relational-databases/polybase/polybase-installation.md)

::: moniker-end
