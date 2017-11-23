---
title: "Пользовательские сеансы (SQL Server PDW)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0425cef2-de4d-4f42-91c5-cb1cd4bb1265
caps.latest.revision: "15"
ms.openlocfilehash: 11c9325b6a16f92ca4d39438fef2a829af3c14b3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="user-sessions"></a>Сеансы пользователей
Имя входа с помощью соответствующих разрешений для управления сеансами всех имен входа в SQL Server PDW appliance, включая выполнение следующих действий.  
  
-   Просмотр текущих сеансов на устройстве, включая активных или неактивных сеансов.  
  
-   Просмотр активных и последние запросы для сеанса.  
  
-   Завершение активных сеансов.  
  
Эти действия могут выполняться с помощью [отслеживать устройства с помощью консоли администрирования](monitor-the-appliance-by-using-the-admin-console.md) или [системных представлений](tsql-system-views.md) команд SQL, как показано ниже.  
  
Те же разрешения, необходимые для управления сеансами с помощью любого метода и описаны в [предоставление разрешений для управления именами входа, пользователей и ролей базы данных](grant-permissions.md#grant-permissions-to-manage-logins-users-and-database-roles).  
  
## <a name="manage-sessions-by-using-the-admin-console"></a>Управление сеансами с помощью консоли администрирования  
  
### <a name="to-view-current-sessions-by-using-the-admin-console"></a>Чтобы просмотреть текущие сеансы с помощью консоли администрирования  
  
1.  В верхнем меню щелкните **сеансы**.  
  
2.  Этот список отображает все последние сеансы. Чтобы просмотреть только сеансы «Активно» или «Idle», щелкните **состояние** заголовок столбца для сортировки результатов по состоянию.  
  
### <a name="to-view-active-and-recent-queries-for-a-session-by-using-the-admin-console"></a>Чтобы просмотреть активные и последние запросы для сеанса с помощью консоли администрирования  
  
1.  В верхнем меню щелкните **сеансы**.  
  
2.  В списке результатов щелкните нужный сеанса идентификатор сеанса.  
  
3.  Полученный список запросов показывает последние запросы для данного сеанса. Сведения о просмотре сведения о запросе см. в разделе [мониторинга активных запросов](monitoring-active-queries.md).  
  
### <a name="to-end-sessions-by-using-the-admin-console"></a>Чтобы завершить сеансы с помощью консоли администрирования  
  
1.  В верхнем меню щелкните **сеансы**.  
  
2.  Найти идентификатор сеанса для сеанса для отмены.  
  
3.  Щелкните красный значок **X** слева от идентификатор сеанса для завершения сеанса. Только сеансы с состоянием «Активно» или «Простой» будет иметь красный **X**; только эти сеансы может быть завершен.  
  
## <a name="manage-sessions-by-using-system-views-and-sql-commands"></a>Управление сеансами с помощью команд SQL и системных представлений  
  
### <a name="to-view-current-sessions-by-using-system-views"></a>Чтобы просмотреть текущие сеансы с помощью системных представлений  
Используйте [sys.dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) создать список текущих сеансов.  
  
В этом примере возвращает session_id, login_name и состояние для всех сеансов с состоянием «Active» или «Бездействие».  
  
```sql  
SELECT session_id, login_name, status FROM sys.dm_pdw_exec_sessions WHERE status='Active' OR status='Idle';  
```  
  
### <a name="to-view-active-and-recent-queries-for-a-session-by-using-system-views"></a>Чтобы просмотреть активные и последние запросы для сеанса с помощью системных представлений  
Чтобы просмотреть активные и недавно завершенные запросы, связанные с сеансом, используйте [sys.dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) и [sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md) представления. Этот запрос возвращает список всех активных или неактивных сеансов, а также любое активное или последних запросов, связанных с идентификатора каждого сеанса.  
  
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
Используйте [KILL](../t-sql/language-elements/kill-transact-sql.md) команду, чтобы завершить текущий сеанс. Требуется идентификатор сеанса для завершение процесса, который можно получить с помощью [sys.dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) представления.  
  
В этом примере выберите login_name, session_id и значения состояния, чтобы найти сеанс, основываясь на имени входа.  
  
```sql  
SELECT session_id, login_name, status FROM sys.dm_pdw_exec_sessions;  
```  
  
С помощью команды KILL можно завершать сеансы со статусом «Активно» или «Idle».  
  
```sql  
KILL 'SID137';  
```  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
