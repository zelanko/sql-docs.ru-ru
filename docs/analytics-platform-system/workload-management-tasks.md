---
title: Задача управления рабочими нагрузками - Analytics Platform System | Документация Майкрософт
description: Задача управления рабочими нагрузками в Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 8e538b96c482a6a16fffcfdac197e62885426b52
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52419925"
---
# <a name="workload-management-tasks-in-analytics-platform-system"></a>Задача управления рабочими нагрузками в Analytics Platform System
Задача управления рабочими нагрузками в Analytics Platform System.

## <a name="view-login-members-of-each-resource-class"></a>Просмотр членов имя входа каждого класса ресурсов
Описывает способ отображения членов каждой роли сервера класс ресурсов входа в SQL Server PDW. Используйте этот запрос, чтобы выяснить, класс ресурсов для запросов, отправленных каждого имени входа, которое.  
  
Описание класса ресурсов, см. в разделе [управления рабочими нагрузками](workload-management.md).  
  
Этот запрос отображает список членов для каждого класса ресурсов. Существуют три классы ресурсов, mediumrc, largerc и xlargerc.  
  
```sql  
SELECT l.name AS [member], r.name AS [server role]  
FROM sys.server_role_members AS rm  
JOIN sys.server_principals AS l  
  ON l.principal_id = rm.member_principal_id  
JOIN  
  sys.server_principals AS r  
  ON r.principal_id = rm.role_principal_id  
WHERE  
  ( l.[type] = 'S' OR l.[type] = 'U' OR l.[type] = 'G' )  
  AND r.[type] = 'R'  
  AND r.[name] in ('mediumrc', 'largerc', 'xlargerc');  
```  
  
Если имя входа не существует в этом списке, его запросы будут получать ресурсы по умолчанию. Если имя входа является членом более одного класса ресурсов, наибольшее класс имеет приоритет.  
  
Выделение ресурсов, перечислены в [управления рабочими нагрузками](workload-management.md).  
  
## <a name="change-the-system-resources-allocated-to-a-request"></a>Изменение системных ресурсов, выделенных на запрос
Описывается, как выяснить, какой ресурс класса, выполняется запрос SQL Server PDW, а затем изменить системные ресурсы для данного запроса. Изменение ресурсов для запроса требуется изменение членства класс ресурсов для имени входа, отправив запрос с помощью [ALTER SERVER ROLE](../t-sql/statements/alter-server-role-transact-sql.md) инструкции.  
  
### <a name="step-1-determine-the-resource-class-for-the-login-running-the-request"></a>Шаг 1. Определите класс ресурсов для имени входа, выполнение запроса.  
Этот запрос отображает имена входа, являющиеся членами членство в роли сервера ресурсов класса. Существует три класса ресурсов **mediumrc**, **largerc**, и **xlargerc**.  
  
> [!IMPORTANT]  
> Этот запрос должен быть выполнен с именем входа, входящим **CONTROL SERVER** разрешение. Если выполняемая имя входа, не **CONTROL SERVER** разрешение, этот запрос возвращает только членство в роли для текущего имени входа.  
  
```sql  
SELECT l.name AS [member], r.name AS [server role]  
FROM sys.server_role_members AS rm  
JOIN sys.server_principals AS l  
  ON l.principal_id = rm.member_principal_id  
JOIN  
  sys.server_principals AS r  
  ON r.principal_id = rm.role_principal_id  
WHERE  
  l.[type] = 'S'   
  AND r.[type] = 'R'  
  AND r.[name] in ('mediumrc', 'largerc', 'xlargerc');  
GO  
```  
  
Если нет имен входа, которые являются членами роли сервера класс ресурсов, результирующая таблица будет пустой. Таким образом, если запрос возвращает имя входа с именем Ching, затем когда Ching отправляет запрос, запрос получает по умолчанию системные ресурсы, которые меньше системных ресурсов класса ресурсов. Если имя входа является членом более одного класса ресурсов, наибольшее класс имеет приоритет.  
  
Список связанных с выделением ресурсов для каждого класса ресурсов, см. в разделе [управления рабочими нагрузками](workload-management.md).  
  
### <a name="step-2-run-the-request-under-a-login-with-different-resource-class-membership"></a>Этап 2. Запустите запрос в имени входа с членство в классе другому ресурсу  
Для выполнения запроса с либо больше или меньше системных ресурсов двумя способами:  
  
-   Запустите запрос под другим именем входа, которая является членом класса больше или меньше ресурсов.  
  
-   Добавьте необходимые имя входа в одну из ролей класс ресурсов. Выберите этот параметр с осторожностью. изменения класса ресурсов для имени входа изменится на системном уровне ресурсов для всех запросов, отправленных имени входа.  
  
Предположим, что Ching является членом роли сервера largerc. В следующем примере показано, как добавление Ching имени входа к роли сервера xlargerc.  
  
```sql  
ALTER SERVER ROLE xlargerc ADD MEMBER Ching;  
```  
  
Ching теперь является членом largerc и xlargerc ролей сервера. Когда Ching отправляет запросы, запросы будут получать системных ресурсов xlargerc.  
  
В следующем примере перемещается Ching mediumrc роли сервера.  Чтобы изменить новую роль, имя входа должен быть удален из ролей сервера largerc и xlargerc и добавляются к роли сервера mediumrc.  
  
```sql  
-- Move login Ching back to using medium system resources for requests.  
ALTER SERVER ROLE xlargerc DROP MEMBER Ching;  
ALTER SERVER ROLE largerc DROP MEMBER Ching;  
ALTER SERVER ROLE mediumrc ADD MEMBER Ching;  
```  
  
Ching теперь является членом роли сервера mediumrc.  В следующем примере изменяется Ching ресурсы системы по умолчанию для запросов.  
  
```sql  
-- Move login Ching to use the default system resources for requests.  
ALTER SERVER ROLE mediumrc DROP MEMBER Ching;  
```  
  
Дополнительные сведения об изменении членства в роли класса ресурсов см. в разделе [ALTER SERVER ROLE](../t-sql/statements/alter-server-role-transact-sql.md).  

## <a name="change-a-login-to-the-default-system-resources-for-its-requests"></a>Изменение имени входа к системным ресурсам по умолчанию для запросов
В этой статье описывается изменение выделения ресурсов системы, назначенные имени входа SQL Server PDW для суммы по умолчанию. 
  
Описание класса ресурсов, см. в разделе [управления рабочими нагрузками](workload-management.md)  
  
Когда имя входа не является членом любой роли сервера класс ресурсов, запросы, отправленные для входа будут возникать объем системных ресурсов по умолчанию.  
  
Предположим, что имя входа Мэтт в настоящее время является членом всех ролей сервера класс ресурсов и желает вернуться к необходимости запросы получать только ресурсы по умолчанию.  В следующем примере присваивается ресурсы по умолчанию на Мэтта запросы, удалив его участие из всех ролей сервера класс три ресурса.  
  
```sql  
--Give the requests submitted by Matt the default system resources   
--by dropping Matt from all resource class server roles.  
ALTER SERVER ROLE XLargeRC DROP MEMBER Matt;  
ALTER SERVER ROLE LargeRC DROP MEMBER Matt;  
ALTER SERVER ROLE MediumRC DROP MEMBER Matt;  
```  
  
## <a name="display-the-number-of-concurrency-slots-needed-for-a-waiting-request"></a>Отображать число слотов необходимые для ожидания запросов
Описывает способ узнать, сколько запрос, который ожидает выполнения в SQL Server PDW необходимы слотов параллелизма.  
  
Дополнительные сведения см. в разделе [управления рабочими нагрузками](workload-management.md).  
  
Запрос может ожидать слишком долго не выполнен. Одним из способов для устранения неполадок запроса — наблюдайте за числом слотов выдачи, необходимые для запроса.  Следующий пример показывает число слотов, необходимые для каждого ожидающего запроса.  
  
```sql  
--Display the number of concurrency slots required   
--for each request that is waiting to run.  
SELECT request_id, concurrency_slots_used AS [Slots Needed], resource_class AS [Resource Class]  
FROM sys.dm_pdw_resource_waits;  
```  
  
  
## <a name="see-also"></a>См. также  
[Управление рабочими нагрузками](workload-management.md)  
  
