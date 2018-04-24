---
title: Разрешения GRANT T-SQL — Parallel Data Warehouse | Документы Microsoft
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
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="grant-t-sql-permissions-for-parallel-data-warehouse"></a>Разрешения GRANT T-SQL для параллельного хранилища данных
Разрешения GRANT T-SQL для операций базы данных в Parallel Data Warehouse.

## <a name="grant-permissions-to-submit-database-queries"></a>Предоставление разрешений для отправки запросов к базе данных
В этом разделе содержатся инструкции по предоставлению разрешений ролям базы данных и пользователей для запроса данных на SQL Server PDW appliance.  
  
Инструкции, используемые для предоставления разрешений для запроса данных зависит от области доступа. Следующие инструкции SQL создать имя входа с именем KimAbercrombie, можно получить доступ к устройству, создайте пользователя базы данных с именем KimAbercrombie в **AdventureWorksPDW2012** базы данных, создать роль базы данных с именем PDWQueryData, добавляет Использование KimAbercrombie PDWQueryData роли, а затем Показать параметры для предоставления доступа запроса на основании ли доступ предоставляется на уровне объектов, или базы данных.  
  
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
В этом разделе содержатся инструкции по предоставлению разрешения имен входа, чтобы использовать консоль администратора.  
  
**Используйте консоль администрирования**  
  
Для использования консоли администрирования имени входа требуется уровень сервера **VIEW SERVER STATE** разрешение. Следующая инструкция SQL предоставляет **VIEW SERVER STATE** имени входа разрешение `KimAbercrombie` , чтобы Kim можно использовать консоль администрирования для наблюдения за SQL Server PDW appliance.  
  
```sql  
USE master;  
GO  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
GO  
```  
  
**Завершить сеансы**  
  
Чтобы предоставить имени входа разрешения на уничтожение сеансы, предоставьте **разрешение ALTER ANY CONNECTION** разрешение следующим образом:  
  
```sql  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
## <a name="grant-permissions-to-load-data"></a>Предоставление разрешений для загрузки данных
В этом разделе содержатся инструкции по предоставлению разрешения для роли базы данных и пользователи базы данных для загрузки данных на PDWappliance сервера SQL.  
  
Сценарий ниже разрешения, необходимые для каждого варианта загрузки. Это значение можно изменить в соответствии с конкретными потребностями.  
  
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
  
## <a name="grant-permissions-to-copy-data-off-the-appliance"></a>Предоставление разрешений, чтобы скопировать данные из устройства
В этом разделе содержатся инструкции по предоставлению разрешения роли пользователя или базы данных, чтобы скопировать данные из SQL Server PDW appliance.  
  
Для перемещения данных в другое место требуются **ВЫБЕРИТЕ** разрешение на таблицу, содержащую данные для перемещения.  
  
Если другой SQL Server PDW назначение для данных, пользователь должен иметь **CREATE TABLE** разрешение в месте назначения и **ALTER SCHEMA** разрешения на схему, которая будет содержать таблицу.  
  
## <a name="grant-permissions-to-manage-databases"></a>Предоставление разрешений для управления базами данных
В этом разделе содержатся инструкции по предоставлению разрешения пользователю базы данных для управления базой данных на SQL Server PDW appliance.  
  
В некоторых ситуациях компания назначает диспетчер для базы данных. Диспетчеру управление доступом, другие имена входа для базы данных, а также данные и объекты базы данных. Для управления всеми объектами, ролей, и пользователи базы данных предоставить пользователю **УПРАВЛЕНИЯ** разрешения в базе данных. Следующая инструкция предоставляет **УПРАВЛЕНИЯ** разрешение на **AdventureWorksPDW2012** базы данных для пользователя `KimAbercrombie`.  
  
```sql
USE AdventureWorksPDW2012;  
GO  
GRANT CONTROL ON DATABASE:: AdventureWorksPDW2012 TO KimAbercrombie;  
```  
  
Для предоставления кто-то разрешения для управления всех баз данных на устройстве, предоставьте **ALTER ANY DATABASE** разрешений в базе данных master.  
  
## <a name="grant-permissions-to-manage-logins-users-and-database-roles"></a>Предоставление разрешений на управление именами входа, пользователей и ролей базы данных
В этом разделе содержатся инструкции по предоставлению разрешения для управления именами входа, пользователи базы данных и ролей базы данных.  
  
### <a name="PermsAdminConsole"></a>Предоставление разрешений для управления именами входа  
**Добавление и управление именами входа**  
  
Следующие инструкции SQL создать имя входа с именем KimAbercrombie, можно создавать новые имена входа с помощью [CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md) инструкции и изменить существующие имена входа с помощью [ALTER LOGIN](../t-sql/statements/alter-login-transact-sql.md) инструкции.  
  
**ALTER ANY LOGIN** разрешение предоставляет возможность создания новых имен входа и удалите существующее. После входа уже существует, имя входа может управляться имена входа с **ALTER ANY LOGIN** разрешение или **ALTER** разрешение для этого имени входа. Пользователь может изменить пароль и по умолчанию базы данных для своего имени входа.  
  
```sql 
CREATE LOGIN KimAbercrombie   
WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
GO  
  
GRANT ALTER ANY LOGIN TO KimAbercrombie;  
```  
  
### <a name="grant-permissions-to-manage-login-sessions"></a>Предоставление разрешений для управления сеансы входа в систему  
Чтобы иметь возможность просмотра всех сеансов на сервере, необходимо **VIEW SERVER STATE** разрешение. Для прерывания сеансов работы других имен входа необходимо наличие **разрешение ALTER ANY CONNECTION** разрешение. В следующем примере используется `KimAbercrombie` входа, созданного ранее.  
  
```sql  
-- Grant permissions to view sessions and queries  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
  
-- Grant permission to end sessions  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
### <a name="grant-permission-to-manage-database-users"></a>Предоставить разрешение на управление пользователями баз данных  
Создание и удаление пользователей базы данных требует **ALTER ANY USER** разрешение. Для управления существующим пользователям требуются **ALTER ANY USER** разрешение или **ALTER** этим пользователем разрешение. В следующем примере используется `KimAbercrombie` входа, созданного ранее.  
  
```sql  
-- Create a user  
USE AdventureWorksPDW2012;  
GO  
CREATE USER KimAbercrombie;  
  
-- Grant permissions to create and drop users   
GRANT ALTER ANY USER TO KimAbercrombie;  
```  
  
### <a name="grant-permisson-to-manage-database-roles"></a>Предоставление разрешений на управление ролями базы данных  
Создание и удаление ролей базы данных, определяемых пользователем требует **ALTER ANY ROLE** разрешение. В следующем примере используется `KimAbercrombie` входа в систему и использовать созданную ранее.  
  
```sql  
USE AdventureWorksPDW2012;  
GO  
-- Grant permissions to create and drop roles  
GRANT ALTER ANY ROLE TO KimAbercrombie;  
```  
  
### <a name="login-user-and-role-permission-charts"></a>Имя входа, пользователей и роли разрешение диаграммы  
Следующие графики могут показаться сложными, но они показывают, как высокий уровень разрешений (например, УПРАВЛЕНИЯ) включают более детализированные разрешения, которые могут быть предоставлены отдельно (такие как ALTER). Рекомендуется всегда предоставлять минимально необходимыми разрешения области для выполнения необходимых задач. Чтобы сделать это, предоставьте более конкретные разрешения вместо разрешений верхнего уровня.  
  
**Разрешения на вход:**  
  
![Разрешения для входа в систему безопасности APS](./media/grant-permissions/APS_security_login_perms.png "APS_security_login_perms")  
  
**Разрешения пользователя:**  
  
![Пользовательские разрешения безопасности APS](./media/grant-permissions/APS_security_user_perms.png "APS_security_user_perms")  
  
**Разрешения роли:**  
  
![Разрешения роли безопасности APS](./media/grant-permissions/APS_security_role_perms.png "APS_security_role_perms")  
  
<!-- MISSING LINKS
For a list of all permissions, see [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md).  
  
-->

## <a name="grant-permissions-to-monitor-the-appliance"></a>Предоставление разрешений для мониторинга устройства
SQL Server PDW appliance можно отслеживать с помощью системных представлений SQL Server PDW или консоли администрирования. Имена входа требуются уровень сервера **VIEW SERVER STATE** разрешение для отслеживания устройства. Имена входа требуют **разрешение ALTER ANY CONNECTION** разрешения завершить соединения с помощью консоли администрирования или **KILL** команды. Сведения о разрешениях, необходимых для использования консоли администрирования см. в разделе [GRANT, предоставление разрешений для использования консоли администрирования &#40;SQL Server PDW&#41;](#grant-permissions-to-use-the-admin-console).  
  
### <a name="PermsAdminConsole"></a>Предоставить разрешение для отслеживания устройства с помощью системных представлений  
Следующие инструкции SQL Создание имени входа `monitor_login` и предоставляет **VIEW SERVER STATE** право `monitor_login` входа.  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_login WITH PASSWORD='Password4321';  
GRANT VIEW SERVER STATE TO monitor_login;  
GO  
```  
  
### <a name="grant-permission-to-monitor-the-appliance-by-using-system-views-and-to-terminate-connections"></a>Предоставить разрешение для отслеживания устройства с помощью системных представлений и завершать соединения  
Следующие инструкции SQL Создание имени входа `monitor_and_terminate_login` и предоставляет **VIEW SERVER STATE** и **разрешение ALTER ANY CONNECTION** разрешения для `monitor_and_terminate_login` входа.  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_and_terminate_login WITH PASSWORD='Password1234';   
GRANT VIEW SERVER STATE TO monitor_and_terminate_login;   
GRANT ALTER ANY CONNECTION TO monitor_and_terminate_login;  
GO  
```  
  
Для создания учетных записей администратора см. [предопределенных ролей сервера](pdw-permissions.md#fixed-server-roles).  
  
## <a name="see-also"></a>См. также:
[СОЗДАНИЕ ИМЕНИ ВХОДА](../t-sql/statements/create-login-transact-sql.md)  
[СОЗДАНИЕ ПОЛЬЗОВАТЕЛЯ](../t-sql/statements/create-user-transact-sql.md)  
[СОЗДАНИЕ РОЛИ](../t-sql/statements/create-role-transact-sql.md)  
[Нагрузки](load-overview.md)  
