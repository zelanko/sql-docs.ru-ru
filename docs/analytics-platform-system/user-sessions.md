---
title: Сеансы пользователей
description: Пользовательские сеансы в хранилище Parallel Data System системы аналитики.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: a0e5b338cc616be214ef39527551ee4a6ffd8f56
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399400"
---
# <a name="user-sessions-in-analytics-platform-system"></a>Пользовательские сеансы в системе платформы аналитики
Имя входа с соответствующими разрешениями может управлять сеансами всех имен входа на SQL Server PDW устройстве, включая выполнение следующих действий:  
  
-   Просмотр текущих сеансов на устройстве, включая активные и бездействующие сеансы.  
  
-   Просмотр активных и недавних запросов для сеанса.  
  
-   Завершить активные сеансы.  
  
Эти действия можно выполнить с помощью [монитора устройства с помощью консоли администрирования](monitor-the-appliance-by-using-the-admin-console.md) или [системных представлений](tsql-system-views.md) с помощью команд SQL, как показано ниже.  
  
Разрешения, необходимые для управления сеансами с помощью любого из этих методов, и описаны в разделе [предоставление разрешений для управления именами входа, пользователями и ролями базы данных](grant-permissions.md#grant-permissions-to-manage-logins-users-and-database-roles).  
  
## <a name="manage-sessions-by-using-the-admin-console"></a>Управление сеансами с помощью консоли администрирования  
  
### <a name="to-view-current-sessions-by-using-the-admin-console"></a>Просмотр текущих сеансов с помощью консоли администрирования  
  
1.  В верхнем меню щелкните **сеансы**.  
  
2.  В итоговом списке отображаются все последние сеансы. Чтобы просмотреть только активные или простаивающие сеансы, щелкните заголовок столбца **состояние** , чтобы отсортировать результаты по состоянию.  
  
### <a name="to-view-active-and-recent-queries-for-a-session-by-using-the-admin-console"></a>Просмотр активных и недавних запросов сеанса с помощью консоли администрирования  
  
1.  В верхнем меню щелкните **сеансы**.  
  
2.  В списке результатов щелкните идентификатор сеанса нужного сеанса.  
  
3.  В списке результирующих запросов отображаются последние запросы для сеанса. Сведения о просмотре сведений о запросе см. в разделе [наблюдение за активными запросами](monitoring-active-queries.md).  
  
### <a name="to-end-sessions-by-using-the-admin-console"></a>Завершение сеансов с помощью консоли администрирования  
  
1.  В верхнем меню щелкните **сеансы**.  
  
2.  Найдите идентификатор сеанса для сеанса, который нужно отменить.  
  
3.  Щелкните красный **крестик** слева от идентификатора сеанса, чтобы завершить сеанс. Только сеансы с состоянием "активный" или "Idle" будут иметь красный значок **X**; можно завершить только эти сеансы.  
  
## <a name="manage-sessions-by-using-system-views-and-sql-commands"></a>Управление сеансами с помощью системных представлений и команд SQL  
  
### <a name="to-view-current-sessions-by-using-system-views"></a>Просмотр текущих сеансов с помощью системных представлений  
Для создания списка текущих сеансов используйте представление [sys. dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) .  
  
Этот пример возвращает session_id, login_name и состояние для всех сеансов с состоянием "активный" или "Idle".  
  
```sql  
SELECT session_id, login_name, status FROM sys.dm_pdw_exec_sessions WHERE status='Active' OR status='Idle';  
```  
  
### <a name="to-view-active-and-recent-queries-for-a-session-by-using-system-views"></a>Просмотр активных и недавних запросов сеанса с помощью системных представлений  
Для просмотра активных и недавно завершенных запросов, связанных с сеансом, используются представления [sys. dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) и [sys. dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md) . Этот запрос возвращает список всех активных или бездействующих сеансов, а также все активные или недавние запросы, связанные с каждым ИДЕНТИФИКАТОРом сеанса.  
  
```sql  
SELECT es.session_id, es.login_name, es.status AS sessionStatus,   
er.request_id, er.status AS requestStatus, er.command   
FROM sys.dm_pdw_exec_sessions es   
LEFT OUTER JOIN sys.dm_pdw_exec_requests er   
ON (es.session_id=er.session_id)   
WHERE (es.status='Active' OR es.status='Idle') AND   
(er.status!= 'Completed' AND er.status!= 'Failed' AND er.status!= 'Cancelled');  
```  
  
### <a name="to-end-sessions-by-using-sql-commands"></a>Завершение сеансов с помощью команд SQL  
Используйте команду [Kill](../t-sql/language-elements/kill-transact-sql.md) для завершения текущего сеанса. Для завершения процесса потребуется идентификатор сеанса, который можно получить с помощью представления [sys. dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) .  
  
В этом примере выберите значения login_name, session_id и Status, чтобы найти сеанс на основе имени входа.  
  
```sql  
SELECT session_id, login_name, status FROM sys.dm_pdw_exec_sessions;  
```  
  
Сеансы с состоянием "активный" или "Idle" можно завершить с помощью команды KILL.  
  
```sql  
KILL 'SID137';  
```  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
