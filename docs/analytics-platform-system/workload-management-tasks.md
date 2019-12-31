---
title: Задачи управления рабочей нагрузкой
description: Задачи управления рабочей нагрузкой в системе платформы аналитики.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 88d95eb0a2e0805930cb5f01f5af05b8fc6b3f2e
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399415"
---
# <a name="workload-management-tasks-in-analytics-platform-system"></a>Задачи управления рабочей нагрузкой в системе платформы аналитики
Задачи управления рабочей нагрузкой в системе платформы аналитики.

## <a name="view-login-members-of-each-resource-class"></a>Просмотр элементов имени входа для каждого класса ресурсов
Описывает, как отобразить элементы имени входа каждой роли сервера класса ресурсов в SQL Server PDW. Используйте этот запрос, чтобы определить класс ресурсов, допустимых для запросов, отправляемых каждым именем входа.  
  
Описание класса ресурсов см. в разделе [Управление рабочей нагрузкой](workload-management.md).  
  
Этот запрос отображает список членства для каждого класса ресурсов. Существует три класса ресурсов: mediumrc, largerc и xlargerc.  
  
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
  
Если имя входа отсутствует в этом списке, его запросы получат ресурсы по умолчанию. Если имя входа является членом более чем одного класса ресурсов, приоритет имеет самый крупный класс.  
  
Выделение ресурсов отображается в списке [Управление рабочей нагрузкой](workload-management.md).  
  
## <a name="change-the-system-resources-allocated-to-a-request"></a>Изменение системных ресурсов, выделенных запросу
В этой статье описывается, как определить класс ресурсов, в котором выполняется запрос SQL Server PDW, а затем изменить системные ресурсы для этого запроса. Чтобы изменить ресурсы для запроса, необходимо изменить членство в классе ресурсов для имени входа, отправляющего запрос, с помощью инструкции [ALTER Server Role](../t-sql/statements/alter-server-role-transact-sql.md) .  
  
### <a name="step-1-determine-the-resource-class-for-the-login-running-the-request"></a>Шаг 1. определение класса ресурсов для имени входа, выполняющего запрос.  
В этом запросе отображаются имена входа, являющиеся членами членства роли сервера класса ресурсов. Существует три класса ресурсов: **mediumrc**, **largerc**и **xlargerc**.  
  
> [!IMPORTANT]  
> Этот запрос должен выполняться именем входа, имеющим разрешение **Control Server** . При выполнении с именем входа без разрешения **Control Server** этот запрос возвращает только членство в роли для текущего имени входа.  
  
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
  
Если имена входа, являющиеся членами роли сервера класса ресурсов, отсутствуют, результирующая таблица будет пустой. В этом случае, если запрос возвращает имя входа с именем Дзынь, то когда Дзынь отправляет запрос, запрос получит системные ресурсы по умолчанию, которые меньше системных ресурсов класса ресурсов. Если имя входа является членом более чем одного класса ресурсов, приоритет имеет самый крупный класс.  
  
Список выделения ресурсов для каждого класса ресурсов см. в разделе [Управление рабочей нагрузкой](workload-management.md).  
  
### <a name="step-2-run-the-request-under-a-login-with-different-resource-class-membership"></a>Шаг 2. выполнение запроса под именем входа с другим членством в классе ресурсов  
Существует два способа выполнения запроса с большими или меньшими системными ресурсами:  
  
-   Выполните запрос с другим именем входа, которое является членом класса ресурсов большего или меньшего размера.  
  
-   Добавьте необходимое имя входа в одну из ролей класса ресурсов. Выбирайте этот параметр с осторожностью. изменение класса ресурсов для имени входа приведет к изменению уровня системных ресурсов для всех запросов, отправленных именем входа.  
  
Предположим, Дзынь является членом роли сервера largerc. В следующем примере показано, как добавить имя входа Дзынь к роли сервера xlargerc.  
  
```sql  
ALTER SERVER ROLE xlargerc ADD MEMBER Ching;  
```  
  
Дзынь теперь является членом ролей сервера largerc и xlargerc. Когда Дзынь отправляет запросы, запросы получат системные ресурсы xlargerc.  
  
В следующем примере Дзынь перемещается обратно в роль сервера mediumrc.  Чтобы перейти на новую роль, имя входа должно быть удалено из xlargerc и ролей сервера largerc и Добавлено в роль сервера mediumrc.  
  
```sql  
-- Move login Ching back to using medium system resources for requests.  
ALTER SERVER ROLE xlargerc DROP MEMBER Ching;  
ALTER SERVER ROLE largerc DROP MEMBER Ching;  
ALTER SERVER ROLE mediumrc ADD MEMBER Ching;  
```  
  
Дзынь теперь является членом роли сервера mediumrc.  В следующем примере показано, как изменить Дзынь на системные ресурсы по умолчанию для запросов.  
  
```sql  
-- Move login Ching to use the default system resources for requests.  
ALTER SERVER ROLE mediumrc DROP MEMBER Ching;  
```  
  
Дополнительные сведения об изменении членства в ролях класса ресурсов см. в разделе [ALTER Server Role](../t-sql/statements/alter-server-role-transact-sql.md).  

## <a name="change-a-login-to-the-default-system-resources-for-its-requests"></a>Изменение имени входа на системные ресурсы по умолчанию для своих запросов
Описывает, как изменить количество выделений системных ресурсов, назначенных SQL Server PDW имени входа, на значения по умолчанию. 
  
Описание класса ресурсов см. в разделе [Управление рабочей нагрузкой](workload-management.md) .  
  
Если имя входа не является членом какой-либо роли сервера класса ресурсов, то запросы, отправленные именем входа, будут принимать по умолчанию объем системных ресурсов.  
  
Предположим, что имя входа Мэтт в данный момент является членом всех ролей сервера класса ресурсов и хочет вернуться к получению запросов, получающих только ресурсы по умолчанию.  В следующем примере ресурсы по умолчанию назначаются для запросов Мэтт путем удаления его членства из всех трех ролей сервера класса ресурсов.  
  
```sql  
--Give the requests submitted by Matt the default system resources   
--by dropping Matt from all resource class server roles.  
ALTER SERVER ROLE XLargeRC DROP MEMBER Matt;  
ALTER SERVER ROLE LargeRC DROP MEMBER Matt;  
ALTER SERVER ROLE MediumRC DROP MEMBER Matt;  
```  
  
## <a name="display-the-number-of-concurrency-slots-needed-for-a-waiting-request"></a>Отображение числа слотов выдачи, необходимых для ожидающего запроса
Описывает, как определить количество слотов выдачи, необходимое для запроса, ожидающего выполнения в SQL Server PDW.  
  
Дополнительные сведения см. в разделе [Управление рабочей нагрузкой](workload-management.md).  
  
Запрос может ожидать слишком долго без выполнения. Одним из способов устранения неполадок в запросе является просмотр количества слотов выдачи, необходимых запросу.  В следующем примере показано количество слотов параллелизма, необходимое для каждого ожидающего запроса.  
  
```sql  
--Display the number of concurrency slots required   
--for each request that is waiting to run.  
SELECT request_id, concurrency_slots_used AS [Slots Needed], resource_class AS [Resource Class]  
FROM sys.dm_pdw_resource_waits;  
```  
  
  
## <a name="see-also"></a>См. также  
[Управление рабочей нагрузкой](workload-management.md)  
  
