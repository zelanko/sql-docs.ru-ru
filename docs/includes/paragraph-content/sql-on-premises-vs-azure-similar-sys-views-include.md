---
ms.openlocfilehash: 6fd7bb2b8be38becc87c4dc8cb353594459a8dd6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68220174"
---

<!--
### Code examples for Azure cloud differ slightly from on-premises
  Or.....
### Code examples can differ for Azure SQL Database
-->

В некоторые примеры кода Transact-SQL, написанные для локального сервера SQL Server, необходимо внести небольшие изменения, чтобы они выполнялись в службе "База данных SQL Azure" в облаке. Одна категория таких примеров кода включает системные представления, чьи префиксы имен немного различаются в двух системах баз данных:

- **server\_** &nbsp; - &nbsp; _префикс для локальной системы_
- **database\_** &nbsp; - &nbsp; _префикс для службы "База данных SQL Azure" в облаке_

Для иллюстрации в приведенной ниже таблице перечислены и сравниваются два подмножества системных представлений. Для краткости подмножества ограничены именами представлений, которые также содержат строку `_event`. Подмножества имеют разные префиксы имен, так как они относятся к двум разным системам баз данных.

| Имя в локальной системе версии 2017 | Имя в облачной службе |
| :------------------------- | :---------------------- |
| server_event_notifications<br />server_event_session_actions<br />server_event_session_events<br />server_event_session_fields<br />server_event_session_targets<br />server_event_sessions<br />server_events<br />server_trigger_events | database_event_session_actions<br />database_event_session_events<br />database_event_session_fields<br />database_event_session_targets<br />database_event_sessions |
| &nbsp; | &nbsp; |

Списки в таблице выше актуальны на июнь 2019 г. Однако содержимое таблицы может устареть, так как оно не обновляется. Чтобы получить точные списки, выполните приведенную ниже инструкцию T-SQL SELECT. Выполните инструкцию SELECT два раза: по одному разу для каждой системы баз данных.

```sql
SELECT name
    FROM sys.all_objects
    WHERE
        (name LIKE 'database\_%' { ESCAPE '\' } OR
         name LIKE 'server\_%' { ESCAPE '\' })
        AND name LIKE '%\_event%' { ESCAPE '\' }
        AND type = 'V'
    ORDER BY name;
```

<!--
The creation of this docs/includes/ file was prompted by Issue 2211 (https://github.com/MicrosoftDocs/sql-docs/issues/2211).
Initial PR was PR 10427 (https://github.com/MicrosoftDocs/sql-docs-pr/pull/10427).
The complaint was that a specific T-SQL code block failed on Azure SQL Database.

GeneMi  ,  2019/05/28
-->
