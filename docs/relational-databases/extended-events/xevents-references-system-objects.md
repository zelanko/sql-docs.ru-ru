---
title: Системные объекты, связанные с расширенными событиями (XEvents)
ms.date: 03/24/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: jukoesma
ms.technology: xevents
ms.topic: reference
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 38982119f9c4485d99263a53c73d1e1c1e4404dc
ms.sourcegitcommit: ff1bd69a8335ad656b220e78acb37dbef86bc78a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2020
ms.locfileid: "78339422"
---
# <a name="system-objects-that-support-extended-events"></a>Системные объекты, которые поддерживают расширенные события

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

В этой статье приводятся ссылки на другие статьи, касающиеся расширенных событий. В этих статьях описывается следующее:

- Системные объекты с поддержкой функции расширенных событий.
- Элементы SQL Server, в которых используются расширенные события.
- Аспекты расширенных событий, характерные для Базы данных SQL Azure в облаке.

Эти списки могут быть неполными.

## <a name="system-tables"></a>Системные таблицы

- [Таблицы расширенных событий — trace_xe_action_map](../system-tables/extended-events-tables-trace-xe-action-map.md)

- [Таблицы расширенных событий — trace_xe_event_map](../system-tables/extended-events-tables-trace-xe-event-map.md)

## <a name="system-catalog-views"></a>Представления системного каталога

- [Представления каталога расширенных событий (Transact-SQL)](../system-catalog-views/extended-events-catalog-views-transact-sql.md)

- [sys.server_event_sessions (Transact-SQL)](../system-catalog-views/sys-server-event-sessions-transact-sql.md)

- [sys.server_event_session_actions (Transact-SQL)](../system-catalog-views/sys-server-event-session-actions-transact-sql.md)

- [sys.server_event_session_events (Transact-SQL)](../system-catalog-views/sys-server-event-session-events-transact-sql.md)

- [sys.server_event_session_fields (Transact-SQL)](../system-catalog-views/sys-server-event-session-fields-transact-sql.md)

- [sys.server_event_session_targets (Transact-SQL)](../system-catalog-views/sys-server-event-session-targets-transact-sql.md)

## <a name="other-system-objects"></a>Другие системные объекты

- [Динамические административные представления расширенных событий](../system-dynamic-management-views/extended-events-dynamic-management-views.md)

## <a name="uses-of-extended-events-by-sql-server-itself"></a>Варианты использования расширенных событий в SQL Server

Этот список не является исчерпывающим.

- [Доступ к диагностическим сведениям в журнале расширенных событий](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)

- [Настройка расширенных событий для групп доступности Always On](../../database-engine/availability-groups/windows/always-on-extended-events.md)

- [Расширенные события для Stretch Database](../../sql-server/stretch-database/extended-events-for-stretch-database.md)

## <a name="azure-sql-database-and-extended-events"></a>База данных SQL Azure и расширенные события

- [Расширенные события в Базе данных SQL Azure](/azure/sql-database/sql-database-xevent-db-diff-from-svr)

- [sys.database_event_session_targets (база данных SQL Azure)](../system-catalog-views/sys-database-event-session-targets-azure-sql-database.md)

- [sys.database_event_session_fields (база данных SQL Azure)](../system-catalog-views/sys-database-event-session-fields-azure-sql-database.md)

- [sys.database_event_session_events (база данных SQL Azure)](../system-catalog-views/sys-database-event-session-events-azure-sql-database.md)

- [sys.database_event_session_actions (база данных SQL Azure)](../system-catalog-views/sys-database-event-session-actions-azure-sql-database.md)
