---
title: Руководство по PolyBase | Документация Майкрософт
ms.date: 05/31/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: polybase
ms.tgt_pltfrm: ''
ms.topic: quickstart
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
ms.openlocfilehash: c31f9538f3429ff4ae1182ee0cd974996cc705a6
ms.sourcegitcommit: 82bb56269faf3fb5dd1420418e32a0a6476780cc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/05/2018
ms.locfileid: "43694727"
---
# <a name="polybase-guide"></a>Руководство по PolyBase

[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]

PolyBase позволяет экземпляру SQL Server 2016 обрабатывать запросы Transact-SQL на считывание данных из Hadoop. Этот запрос можно также использовать для доступа к реляционным таблицам в SQL Server. PolyBase также позволяет применять этот запрос для объединения данных из Hadoop и SQL Server. В SQL Server подключение к Hadoop обеспечивают [внешние таблицы](../../t-sql/statements/create-external-table-transact-sql.md) или [внешний источник данных](../../t-sql/statements/create-external-data-source-transact-sql.md).

PolyBase предоставляет одинаковые функции для следующих продуктов SQL от корпорации Майкрософт:

- SQL Server 2016 и последующие версии;
- Analytics Platform System (прежнее название — Parallel Data Warehouse);
- хранилище данных SQL Azure.

PolyBase отправляет некоторые вычисления на узел Hadoop, чтобы оптимизировать общий запрос. Но PolyBase обеспечивает внешний доступ не только к Hadoop. Поддерживаются и другие неструктурированные нереляционные таблицы, например текстовые файлы с разделителями.

#### <a name="data-import-and-export"></a>Импорт и экспорт данных

Запросы T-SQL на основе PolyBase также можно использовать для импорта данных из хранилища BLOB-объектов Azure и экспорта данных в него. Кроме того, PolyBase позволяет Хранилищу данных SQL Azure импортировать данные из хранилища BLOB-объектов Azure и Azure Data Lake Store, а также экспортировать в них данные.

Инструкции по работе с PolyBase см. в статье [Приступая к работе с PolyBase](../../relational-databases/polybase/get-started-with-polybase.md).
  
![Логическая схема использования PolyBase](../../relational-databases/polybase/media/polybase-logical.png "логическая схема использования PolyBase")

## <a name="why-use-polybase"></a>Зачем нужна технология PolyBase

Раньше было гораздо сложнее объединить данные SQL Server с внешними данными. Для этого применялось два неэффективных способа:

- передать часть данных, чтобы все данные были в том или ином формате;
- запросить данные из двух источников, а затем написать пользовательскую логику запроса для объединения и интеграции данных на уровне клиента.

В PolyBase вместо таких неэффективных способов объединения данных применяется T-SQL.

Проще говоря, PolyBase не требует установки дополнительного программного обеспечения в среде Hadoop. При запросе внешних данных используется такой же синтаксис T-SQL, как и при запросе таблицы базы данных. Все вспомогательные действия, реализуемые PolyBase, выполняются прозрачно. Автору запроса не требуется знать, как работает Hadoop.

PolyBase может:

- **Запрашивать данные, хранящиеся в Hadoop, из SQL Server или PDW.** Пользователи хранят данные в более экономичных распределенных и масштабируемых системах, таких как Hadoop. PolyBase позволяет легко запрашивать данные с помощью T-SQL.

- **Запрашивать данные, хранящиеся в хранилище BLOB-объектов Azure.** Данные для использования службами Azure удобно хранить в хранилище BLOB-объектов Azure.  PolyBase позволяет легко обращаться к данным с помощью T-SQL.

- **Импорт данных из Hadoop, хранилища BLOB-объектов Azure или Azure Data Lake Store.** Используйте скорость технологии Microsoft SQL columnstore и возможности анализа, импортируя данные из Hadoop, хранилища BLOB-объектов Azure или Azure Data Lake Store в реляционные таблицы. Нет необходимости в отдельном средстве ETL или импорта.

- **Экспортировать данные в Hadoop, хранилище BLOB-объектов Azure или Azure Data Lake Store.** Архивация данных в Hadoop, хранилище BLOB-объектов Azure или Azure Data Lake Store позволяет создать экономичное хранилище и обеспечить его подключение к сети для удобного доступа к данным.

- **Интегрироваться со средствами бизнес-аналитики.** Можно использовать PolyBase со средствами бизнес-аналитики и стеком технологий анализа Майкрософт, а также применять любые сторонние средства, совместимые с SQL Server.

## <a name="performance"></a>Производительность

- **Принудительная отправка вычислений в Hadoop.** Оптимизатор запросов принимает решение принудительно отправить вычисления в Hadoop, если это улучшит производительность запросов.  Для принятия такого решения он использует статистику из внешних таблиц. При включении вычислений создаются задания MapReduce и применяются распределенные вычислительные ресурсы Hadoop.

- **Масштабирование вычислительных ресурсов.** Для повышения производительности запросов можно использовать [группы горизонтального масштабирования PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md)в SQL Server. Это обеспечивает параллельную передачу данных между экземплярами SQL Server и узлами Hadoop, а также добавляет вычислительные ресурсы для работы с внешними данными.

## <a name="polybase-guide-topics"></a>Статьи руководства по PolyBase

Это руководство содержит статьи, которые помогут вам использовать PolyBase более эффективно.

|||
|-|-|
|**Раздел**|**Описание**|
|[Приступая к работе с PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)|Основные шаги по установке и настройке PolyBase. В статье рассказывается, как создавать внешние объекты, указывающие на данные в Hadoop или хранилище BLOB-объектов Azure, и приводятся примеры запросов.|
|[Сводка функций PolyBase по версиям](../../relational-databases/polybase/polybase-versioned-feature-summary.md)|В статье описываются компоненты PolyBase, которые поддерживаются в SQL Server, базе данных SQL и хранилище данных SQL.|
|[группы горизонтального масштабирования PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md)|Параллельное масштабирование между SQL Server и Hadoop с использованием групп горизонтального масштабирования SQL Server.|
|[Установка PolyBase](../../relational-databases/polybase/polybase-installation.md)|Ссылки и инструкции по установке PolyBase с помощью мастера установки или средства командной строки.|
|[Конфигурация PolyBase](../../relational-databases/polybase/polybase-configuration.md)|Настройка параметров SQL Server для PolyBase.  Например, настройка включения вычислений и средств безопасности Kerberos.|
|[Объекты T-SQL PolyBase](../../relational-databases/polybase/polybase-t-sql-objects.md)|Создание объектов T-SQL, которые PolyBase использует для определения внешних данных и доступа к этим данным.|
|[PolyBase Queries](../../relational-databases/polybase/polybase-queries.md)|Используйте инструкции T-SQL для запроса, импорта или экспорта внешних данных.|
|[Устранение неполадок c PolyBase](../../relational-databases/polybase/polybase-troubleshooting.md)|Методы управления запросами PolyBase. Используйте динамические административные представления (DMV) для отслеживания запросов PolyBase и узнайте, как считать план запросов PolyBase для поиска узких мест производительности.|
| &nbsp; | &nbsp; |
  
