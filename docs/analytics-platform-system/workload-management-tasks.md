---
title: Задачи управления рабочей нагрузки - система платформы аналитики | Документы Microsoft
description: Задачи управления рабочей нагрузки в Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 16206cb5cefd68b19e1640592b903890808b5a31
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31538794"
---
# <a name="workload-management-tasks-in-analytics-platform-system"></a>Задачи управления рабочей нагрузки в система платформы аналитики
Задачи управления рабочей нагрузки в Analytics Platform System.

## <a name="view-login-members-of-each-resource-class"></a>Просмотр членов имя входа каждого класса ресурсов
Описывает способ отображения членов каждой роли сервера ресурсов класса входа в SQL Server PDW. Используйте этот запрос, чтобы определить класс ресурсов для запросов, отправленных каждого имени входа.  
  
Описания класса ресурсов см. в разделе [управления рабочей нагрузкой](workload-management.md).  
  
Этот запрос отображает список членов для каждого класса ресурсов. Существует три классов ресурсов, mediumrc, largerc и xlargerc.  
  
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
  
Если имя входа не существует в этом списке, его запросы получит ресурсов по умолчанию. Если имя входа является членом более чем одним классом ресурсов, наибольшее класс имеет более высокий приоритет.  
  
Выделение ресурсов, перечислены в [управления рабочей нагрузкой](workload-management.md).  
  
## <a name="change-the-system-resources-allocated-to-a-request"></a>Изменение системных ресурсов, выделенных на запрос
Описывает, как определить, какой ресурс класса, выполняется запрос SQL Server PDW, а затем изменить системные ресурсы для этого запроса. Изменение ресурсов для запроса, необходимо изменить членство Отправка запроса с помощью имени входа в классе ресурса [ALTER SERVER ROLE](../t-sql/statements/alter-server-role-transact-sql.md) инструкции.  
  
### <a name="step-1-determine-the-resource-class-for-the-login-running-the-request"></a>Шаг 1: Определение класса ресурса для имени входа, выполнение запроса.  
Этот запрос отображает имена входа, являющиеся членами членство в роли сервера ресурсов класса. Имеется три класса ресурсов **mediumrc**, **largerc**, и **xlargerc**.  
  
> [!IMPORTANT]  
> Этот запрос должен быть выполнен с именем входа, входящим **CONTROL SERVER** разрешение. Если выполняется по имени входа без **CONTROL SERVER** разрешений, этот запрос возвращает только членство в ролях для текущего имени входа.  
  
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
  
Если нет имен входа, являющиеся членами роли сервера класс ресурсов, результирующая таблица будет пустой. Таким образом Если запрос возвращает имя входа с именем Чинг, затем при Чинг отправляется запрос, запрос получит системных ресурсов по умолчанию, которые меньше системных ресурсов класса ресурсов. Если имя входа является членом более чем одним классом ресурсов, наибольшее класс имеет более высокий приоритет.  
  
Список выделений ресурсов для каждого класса ресурсов, в разделе [управления рабочей нагрузкой](workload-management.md).  
  
### <a name="step-2-run-the-request-under-a-login-with-different-resource-class-membership"></a>Шаг 2: Запуск запроса с именем пользователя с членством другого ресурса класса  
Для выполнения запроса с либо больше или меньше системных ресурсов двумя способами.  
  
-   Запустите запрос в другое имя пользователя, которая является членом класса, который больше или меньше ресурсов.  
  
-   Добавьте необходимые входа в одну из ролей класса ресурсов. Выберите этот параметр с осторожностью. Изменение класс ресурсов для имени входа, приведет к изменению уровня ресурсов системы для всех запросов, отправленных имени входа.  
  
Предположим, что Чинг является членом роли сервера largerc. Следующий пример демонстрирует добавление Чинг входа к роли сервера xlargerc.  
  
```sql  
ALTER SERVER ROLE xlargerc ADD MEMBER Ching;  
```  
  
Чинг теперь является членом largerc и xlargerc серверных ролей. Когда Чинг отправляет запросы, запросы получают xlargerc системных ресурсов.  
  
В следующем примере перемещается Чинг mediumrc серверной роли.  Чтобы изменить новую роль, имя входа должен быть удален из xlargerc и largerc ролей сервера и добавляются к роли сервера mediumrc.  
  
```sql  
-- Move login Ching back to using medium system resources for requests.  
ALTER SERVER ROLE xlargerc DROP MEMBER Ching;  
ALTER SERVER ROLE largerc DROP MEMBER Ching;  
ALTER SERVER ROLE mediumrc ADD MEMBER Ching;  
```  
  
Чинг является членом роли сервера mediumrc.  В следующем примере изменяется Чинг иметь системных ресурсов по умолчанию для запросов.  
  
```sql  
-- Move login Ching to use the default system resources for requests.  
ALTER SERVER ROLE mediumrc DROP MEMBER Ching;  
```  
  
Дополнительные сведения об изменении членство в роли ресурсов класса см. в разделе [ALTER SERVER ROLE](../t-sql/statements/alter-server-role-transact-sql.md).  

## <a name="change-a-login-to-the-default-system-resources-for-its-requests"></a>Измените имя входа на системных ресурсов по умолчанию для запросов
Описывает, как изменять параметры распределения ресурсов системы, назначенные имени входа SQL Server PDW суммы по умолчанию. 
  
Описания класса ресурсов см. в разделе [управления рабочей нагрузкой](workload-management.md)  
  
Если имя для входа не является членом любой роли сервера ресурсов класса, запросов, отправленных имени входа будет получать объем системных ресурсов по умолчанию.  
  
Предположим, что имя входа, Мэтт в данный момент является членом всех ролей сервера класс ресурсов и хочет чтобы вернуться к необходимости запросы на получение только ресурсов по умолчанию.  В следующем примере присваивается ресурсов по умолчанию для запросов Мэтт путем перетаскивания его членство ролей сервера, все три ресурсов класса.  
  
```sql  
--Give the requests submitted by Matt the default system resources   
--by dropping Matt from all resource class server roles.  
ALTER SERVER ROLE XLargeRC DROP MEMBER Matt;  
ALTER SERVER ROLE LargeRC DROP MEMBER Matt;  
ALTER SERVER ROLE MediumRC DROP MEMBER Matt;  
```  
  
## <a name="display-the-number-of-concurrency-slots-needed-for-a-waiting-request"></a>Отображать число слотов параллелизма необходимые для ожидания запроса
Описывает способ выяснить количество параллелизма с помощью запросов, ожидающих выполнения в SQL Server PDW необходимы слотов.  
  
Дополнительные сведения см. в разделе [управления рабочей нагрузкой](workload-management.md).  
  
Запрос может ожидания слишком долго не выполнен. Один из способов решения проблем с запросом является рассмотрим общее число слотов параллелизма, необходимые для запроса.  Следующий пример показывает общее число слотов параллелизма, необходимые для каждого ожидающего запроса.  
  
```sql  
--Display the number of concurrency slots required   
--for each request that is waiting to run.  
SELECT request_id, concurrency_slots_used AS [Slots Needed], resource_class AS [Resource Class]  
FROM sys.dm_pdw_resource_waits;  
```  
  
  
## <a name="see-also"></a>См. также  
[Управление рабочими нагрузками](workload-management.md)  
  
