---
title: Сеансы пользователей в Analytics Platform System | Документация по Microsoft»
description: Сеансы пользователей в Analytics Platform System Parallel Data Warehouse.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 33bf052e27640ee08784927351579378bffbec2b
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52419225"
---
# <a name="user-sessions-in-analytics-platform-system"></a>Сеансы пользователей в Analytics Platform System
Имя входа с соответствующими разрешениями для управления сеансами, все имена для входа в SQL Server PDW устройстве, включая выполнение этих действий.  
  
-   Просмотр текущих сеансов на устройстве, включая активные и бездействующих сеансов.  
  
-   Просмотрите активные и Недавние запросы для сеанса.  
  
-   Конец активных сеансов.  
  
Эти действия могут выполняться с помощью [мониторинг устройства с помощью консоли администрирования](monitor-the-appliance-by-using-the-admin-console.md) или [системные представления](tsql-system-views.md) через команды SQL, как показано ниже.  
  
Разрешения, необходимые для управления сеансами с помощью любого из этих методов совпадают и описаны в [предоставить разрешения на управление именами входа, пользователей и ролей базы данных](grant-permissions.md#grant-permissions-to-manage-logins-users-and-database-roles).  
  
## <a name="manage-sessions-by-using-the-admin-console"></a>Управление сеансами с помощью консоли администрирования  
  
### <a name="to-view-current-sessions-by-using-the-admin-console"></a>Чтобы просмотреть текущие сеансы с помощью консоли администрирования  
  
1.  В верхнем меню щелкните **сеансы**.  
  
2.  Полученный список отображает все последние сеансы. Чтобы просмотреть только сеансы «Активный» "или" состояние «неактивно», щелкните **состояние** заголовок столбца для сортировки результатов по состоянию.  
  
### <a name="to-view-active-and-recent-queries-for-a-session-by-using-the-admin-console"></a>Чтобы просмотреть активные и Недавние запросы для сеанса с помощью консоли администрирования  
  
1.  В верхнем меню щелкните **сеансы**.  
  
2.  В списке результатов щелкните нужный сеанса идентификатор сеанса.  
  
3.  Полученный список запросов показывает последние запросы для сеанса. Сведения о просмотре сведения о запросе, см. в разделе [мониторинг активных запросов](monitoring-active-queries.md).  
  
### <a name="to-end-sessions-by-using-the-admin-console"></a>Чтобы завершить сеансы с помощью консоли администрирования  
  
1.  В верхнем меню щелкните **сеансы**.  
  
2.  Найти идентификатор сеанса для сеанса для отмены.  
  
3.  Щелкните красный **X** слева от идентификатор сеанса для завершения сеанса. Только сеансы с состоянием «Активно» или «Простой» будет иметь красный **X**; только эти сеансы может быть завершен.  
  
## <a name="manage-sessions-by-using-system-views-and-sql-commands"></a>Управление сеансами с помощью системных представлений и команд SQL  
  
### <a name="to-view-current-sessions-by-using-system-views"></a>Чтобы просмотреть текущие сеансы с помощью системных представлений  
Используйте [sys.dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) для создания списка текущих сеансов.  
  
В этом примере возвращает session_id, login_name и состояние для всех сеансов с состоянием «Активное» или «Бездействие».  
  
```sql  
SELECT session_id, login_name, status FROM sys.dm_pdw_exec_sessions WHERE status='Active' OR status='Idle';  
```  
  
### <a name="to-view-active-and-recent-queries-for-a-session-by-using-system-views"></a>Чтобы просмотреть активные и Недавние запросы для сеанса с помощью системных представлений  
Чтобы просмотреть активные и недавно завершенные запросы, связанные с сеансом, использовании [sys.dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) и [sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md) представления. Этот запрос возвращает список всех активных или неактивных сеансов, а также активных или последние запросы, связанные с идентификатором каждого сеанса.  
  
```sql  
SELECT es.session_id, es.login_name, es.status AS sessionStatus,   
er.request_id, er.status AS requestStatus, er.command   
FROM sys.dm_pdw_exec_sessions es   
LEFT OUTER JOIN sys.dm_pdw_exec_requests er   
ON (es.session_id=er.session_id)   
WHERE (es.status='Active' OR es.status='Idle') AND   
(er.status!= 'Completed' AND er.status!= 'Failed' AND er.status!= 'Cancelled');  
```  
  
### <a name="to-end-sessions-by-using-sql-commands"></a>Чтобы завершить сеансы с помощью команд SQL  
Используйте [KILL](../t-sql/language-elements/kill-transact-sql.md) команду, чтобы завершить текущий сеанс. Вам потребуется идентификатор сеанса для процесса для завершения, который можно получить с помощью [sys.dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) представления.  
  
В этом примере выберите login_name, session_id и значения состояния, чтобы найти сеанс, основываясь на имени входа.  
  
```sql  
SELECT session_id, login_name, status FROM sys.dm_pdw_exec_sessions;  
```  
  
Сеансы с состоянием «Активный» "или" состояние «неактивно» может быть завершен с помощью команды KILL.  
  
```sql  
KILL 'SID137';  
```  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
