---
title: Разрешения GRANT T-SQL — Parallel Data Warehouse | Документация Майкрософт
description: Разрешения GRANT T-SQL для операций базы данных в Parallel Data Warehouse.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 01ef7b199a07be8bbc2dc1dee40d9c4d5771db1b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63157502"
---
# <a name="grant-t-sql-permissions-for-parallel-data-warehouse"></a>Разрешения GRANT T-SQL для Parallel Data Warehouse
Разрешения GRANT T-SQL для операций базы данных в Parallel Data Warehouse.

## <a name="grant-permissions-to-submit-database-queries"></a>Предоставление разрешений для отправки запросов к базе данных
В этом разделе описывается, как предоставлять разрешения ролям базы данных и пользователи могли запрашивать данные на устройстве, SQL Server PDW.  
  
Инструкции, используемые для предоставления разрешений для запроса данных зависят от области доступа. Следующие инструкции SQL создайте имя входа с именем KimAbercrombie, который можно получить доступ к модуль, создать пользователя базы данных с именем KimAbercrombie в **AdventureWorksPDW2012** базы данных, создать роль базы данных с именем PDWQueryData, добавляет Использование KimAbercrombie PDWQueryData роли, а затем Показать параметры для предоставления доступа запрос, на основании ли доступ предоставляется на объект или уровень базы данных.  
  
```sql  
USE master;  
GO  
  
CREATE LOGIN KimAbercrombie WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
GO  
  
USE AdventureWorksPDW2012;  
GO  
  
CREATE USER KimAbercrombie;  
GO  
  
CREATE ROLE PDWQueryData;  
GO  
  
EXEC sp_addrolemember 'PDWQueryData', 'KimAbercrombie'  
GO  
  
-- If the permission is granted against a table or view only, use this syntax:  
GRANT SELECT ON OBJECT::AdventureWorksPDW2012..DimEmployee TO PDWQueryData;  
GO  
  
-- If the permission is granted for the database, use this syntax:  
GRANT SELECT ON DATABASE::AdventureWorksPDW2012 TO PDWQueryData;  
GO  
  
-- If KimAbercrombie is the only user that needs to access a table, use this syntax:  
GRANT SELECT ON OBJECT::AdventureWorksPDW2012..DimEmployee TO KimAbercrombie;  
GO  
```  
  
## <a name="grant-permissions-to-use-the-admin-console"></a>Предоставьте разрешения на использование консоли администрирования
В этом разделе описывается, как предоставить разрешения имен входа с помощью консоли администрирования.  
  
**Использовать консоль администратора**  
  
Чтобы использовать консоль администратора имени входа требуется на уровне сервера **VIEW SERVER STATE** разрешение. Следующая инструкция SQL предоставляет **VIEW SERVER STATE** имени входа разрешение `KimAbercrombie` таким образом, чтобы Ким можно использовать консоль администратора для мониторинга SQL Server PDW appliance.  
  
```sql  
USE master;  
GO  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
GO  
```  
  
**Завершить сеансы**  
  
Чтобы предоставить имени входа разрешения на уничтожение сеансы, предоставьте **ALTER ANY CONNECTION** разрешение следующим образом:  
  
```sql  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
## <a name="grant-permissions-to-load-data"></a>GRANT, предоставление разрешений для загрузки данных
В этом разделе описывается, как предоставить разрешения роли базы данных и пользователей базы данных для загрузки данных на PDWappliance сервера SQL.  
  
В следующем сценария показано, какие разрешения необходимы для каждого варианта загрузки. Это значение можно изменить в соответствии с вашими потребностями.  
  
```sql  
-- Create server login for the examples that follow.  
USE master;  
CREATE LOGIN BI_ETLUser WITH PASSWORD = '******';  
  
--Grant BULK Load permissions   
GRANT ADMINISTER BULK OPERATIONS TO BI_ETLUser;  
  
--Grant Staging database permissions  
USE stagedb;  
CREATE USER BI_ETLUser for login BI_ETLUser;  
EXEC sp_addrolemember 'db_datareader','BI_ETLUser';  
EXEC sp_addrolemember 'db_datawriter','BI_ETLUser';  
EXEC sp_addrolemember 'db_ddladmin','BI_ETLUser';  
  
-- The CREATE TABLE permission is required for the database hosting the temporary table.  
-- This may be the staging database (if specified) or destination database.   
-- The CREATE permission is not required if loading in fastappend mode.  
GRANT CREATE TABLE ON database::stagedb TO BI_ETLUser;  
  
-- If loading in append or fastappend mode, the INSERT permission is required on the destination table.  
GRANT INSERT ON database::stagedb TO BI_ETLUser;  
  
-- If loading in reload mode, the INSERT and DELETE permissions are required on the destination table.  
GRANT INSERT ON database::stagedb TO BI_ETLUser;  
GRANT DELETE ON database::stagedb TO BI_ETLUser;  
  
-- If loading in upsert mode, the INSERT and UPDATE permissions are required on the destination table.  
GRANT INSERT ON database::stagedb TO BI_ETLUser;  
GRANT UPDATE ON database::stagedb TO BI_ETLUser;  
  
-- Destination DB  
USE tpch_1gb;  
CREATE USER BI_ETLUser FOR LOGIN BI_ETLUser;  
EXEC sp_addrolemember 'db_datareader','BI_ETLUser';  
EXEC sp_addrolemember 'db_datawriter','BI_ETLUser';  
```  
  
## <a name="grant-permissions-to-copy-data-off-the-appliance"></a>GRANT, предоставление разрешений для копирования данных за пределами устройства
В этом разделе описывается, как для предоставления разрешений на роль пользователя или базы данных для копирования данных за пределами SQL Server PDW устройства.  
  
Для перемещения данных в другое расположение требуются **ВЫБЕРИТЕ** разрешение на таблицу, содержащую данные для перемещаемого.  
  
Если место назначения данных другой SQL Server PDW, пользователь должен иметь **CREATE TABLE** разрешение в месте назначения и **ALTER SCHEMA** разрешения на схему, которая будет содержать таблицу.  
  
## <a name="grant-permissions-to-manage-databases"></a>GRANT, предоставление разрешений для управления базами данных
В этом разделе описывается, как предоставить разрешения пользователю базы данных для управления базой данных на SQL Server PDW appliance.  
  
В некоторых случаях компании назначает manager для базы данных. Manager управляет доступом других имен входа для базы данных, а также данные и объекты в базе данных. Для управления всеми объектами, роли, и предоставить пользователям базы данных **УПРАВЛЕНИЯ** разрешение в базе данных. Следующая инструкция предоставляет **УПРАВЛЕНИЯ** разрешение на **AdventureWorksPDW2012** базы данных для пользователя `KimAbercrombie`.  
  
```sql
USE AdventureWorksPDW2012;  
GO  
GRANT CONTROL ON DATABASE:: AdventureWorksPDW2012 TO KimAbercrombie;  
```  
  
Чтобы предоставите кому-либо полномочие на управление всех баз данных на устройстве, предоставьте **ALTER ANY DATABASE** разрешение в базе данных master.  
  
## <a name="grant-permissions-to-manage-logins-users-and-database-roles"></a>Предоставление разрешений на управление именами входа, пользователей и роли базы данных
В этом разделе описывается, как предоставить разрешения для управления именами входа, пользователи базы данных и ролей базы данных.  
  
### <a name="PermsAdminConsole"></a>GRANT, предоставление разрешений для управления именами входа  
**Добавление и управление именами входа**  
  
Следующие инструкции SQL создайте имя входа с именем KimAbercrombie, который может создавать новые имена входа с помощью [CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md) инструкции и изменить существующие имена входа с помощью [ALTER LOGIN](../t-sql/statements/alter-login-transact-sql.md) инструкции.  
  
**ALTER ANY LOGIN** разрешение предоставляет возможность создания новых имен входа и удалите существующий. После создания учетной записи имени входа можно управлять по именам для входа с **ALTER ANY LOGIN** разрешение или **ALTER** разрешение для этого имени входа. Имя входа можно изменить пароль и по умолчанию базу данных для своего имени входа.  
  
```sql 
CREATE LOGIN KimAbercrombie   
WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
GO  
  
GRANT ALTER ANY LOGIN TO KimAbercrombie;  
```  
  
### <a name="grant-permissions-to-manage-login-sessions"></a>Предоставление разрешений для управления сеансами входа  
Чтобы иметь возможность просматривать все сеансы на сервере, необходимо **VIEW SERVER STATE** разрешение. Для прерывания сеансов работы других имен входа необходимо **ALTER ANY CONNECTION** разрешение. В следующем примере используется `KimAbercrombie` имени входа, созданного ранее.  
  
```sql  
-- Grant permissions to view sessions and queries  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
  
-- Grant permission to end sessions  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
### <a name="grant-permission-to-manage-database-users"></a>Предоставьте разрешение на управление пользователями баз данных  
Создание и удаление пользователей базы данных требует **ALTER ANY USER** разрешение. Для управления существующим пользователям требуется **ALTER ANY USER** разрешение или **ALTER** этим пользователем разрешение. В следующем примере используется `KimAbercrombie` имени входа, созданного ранее.  
  
```sql  
-- Create a user  
USE AdventureWorksPDW2012;  
GO  
CREATE USER KimAbercrombie;  
  
-- Grant permissions to create and drop users   
GRANT ALTER ANY USER TO KimAbercrombie;  
```  
  
### <a name="grant-permisson-to-manage-database-roles"></a>Предоставление разрешений на управление ролями базы данных  
Создание и удаление определяемых пользователем ролей базы данных требует **разрешение ALTER ANY ROLE** разрешение. В следующем примере используется `KimAbercrombie` имя входа и использования, созданные ранее.  
  
```sql  
USE AdventureWorksPDW2012;  
GO  
-- Grant permissions to create and drop roles  
GRANT ALTER ANY ROLE TO KimAbercrombie;  
```  
  
### <a name="login-user-and-role-permission-charts"></a>Имя входа, пользователей и роли разрешение диаграммы  
Следующие графики сбивает с толку, но в них показано, как более высоких разрешений бегунка (например, элемент УПРАВЛЕНИЯ) включают более детализированные разрешения, которые могут предоставляться отдельно (например, ALTER). Рекомендуется всегда предоставлять наименьший объем разрешений области для выполнения необходимых задач. Чтобы сделать это, предоставьте более конкретные разрешения, вместо разрешений верхнего уровня.  
  
**Разрешения входа:**  
  
![Разрешения безопасности APS](./media/grant-permissions/APS_security_login_perms.png "APS_security_login_perms")  
  
**Разрешения пользователя:**  
  
![Пользовательские разрешения безопасности APS](./media/grant-permissions/APS_security_user_perms.png "APS_security_user_perms")  
  
**Разрешения роли:**  
  
![Разрешения роли безопасности APS](./media/grant-permissions/APS_security_role_perms.png "APS_security_role_perms")  
  
<!-- MISSING LINKS
For a list of all permissions, see [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md).  
  
-->

## <a name="grant-permissions-to-monitor-the-appliance"></a>Предоставление разрешений для мониторинга устройства
SQL Server PDW appliance можно отслеживать с помощью системных представлений SQL Server PDW или консоли администрирования. Входах на уровне сервера **VIEW SERVER STATE** разрешение на мониторинг устройства. Имена входа требуют **ALTER ANY CONNECTION** разрешение, чтобы завершать соединения с помощью консоли администрирования или **KILL** команды. Сведения о разрешениях, необходимых для использования консоли администрирования, см. в разделе [GRANT, предоставление разрешений для использования консоли администрирования &#40;SQL Server PDW&#41;](#grant-permissions-to-use-the-admin-console).  
  
### <a name="PermsAdminConsole"></a>Предоставьте разрешение на мониторинг устройства с помощью системных представлений  
Следующие инструкции SQL создайте имя входа с именем `monitor_login` и предоставляет **VIEW SERVER STATE** разрешение на `monitor_login` имени входа.  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_login WITH PASSWORD='Password4321';  
GRANT VIEW SERVER STATE TO monitor_login;  
GO  
```  
  
### <a name="grant-permission-to-monitor-the-appliance-by-using-system-views-and-to-terminate-connections"></a>Предоставьте разрешение на мониторинг устройства с помощью системных представлений и завершать соединения  
Следующие инструкции SQL создайте имя входа с именем `monitor_and_terminate_login` и предоставляет **VIEW SERVER STATE** и **ALTER ANY CONNECTION** право `monitor_and_terminate_login` имени входа.  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_and_terminate_login WITH PASSWORD='Password1234';   
GRANT VIEW SERVER STATE TO monitor_and_terminate_login;   
GRANT ALTER ANY CONNECTION TO monitor_and_terminate_login;  
GO  
```  
  
Чтобы создать имена для входа администратора, см. в разделе [предопределенных ролей сервера](pdw-permissions.md#fixed-server-roles).  
  
## <a name="see-also"></a>См. также
[CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md)  
[СОЗДАНИЕ ПОЛЬЗОВАТЕЛЯ](../t-sql/statements/create-user-transact-sql.md)  
[СОЗДАНИЕ РОЛИ](../t-sql/statements/create-role-transact-sql.md)  
[Загрузить](load-overview.md)  
