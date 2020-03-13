---
title: Предоставление разрешений T-SQL
description: Предоставьте разрешения T-SQL для операций базы данных в Parallel Data Warehouse.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 6bbe78979c393490a52e1051fe158ae138f93dcc
ms.sourcegitcommit: 4baa8d3c13dd290068885aea914845ede58aa840
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79289702"
---
# <a name="grant-t-sql-permissions-for-parallel-data-warehouse"></a>Предоставление разрешений T-SQL для параллельного хранилища данных
Предоставьте разрешения T-SQL для операций базы данных в Parallel Data Warehouse.

## <a name="grant-permissions-to-submit-database-queries"></a>Предоставление разрешений на отправку запросов к базе данных
В этом разделе описано, как предоставить разрешения ролям базы данных и пользователям запрашивать данные на SQL Server PDW устройстве.  
  
Инструкции, используемые для предоставления разрешений на запрос данных, зависят от требуемой области доступа. Следующие инструкции SQL создают имя входа с именем Кимаберкромбие, которое может получить доступ к устройству, создание пользователя базы данных с именем Кимаберкромбие в базе данных **AdventureWorksPDW2012** , создание роли базы данных с именем пдвкуеридата, Добавление параметра Use кимаберкромбие к роли пдвкуеридата, а также отображение параметров для предоставления доступа к запросам в зависимости от того, предоставлен ли доступ на объект или на уровне базы данных.  
  
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
  
## <a name="grant-permissions-to-use-the-admin-console"></a>Предоставление разрешений на использование консоли администрирования
В этом разделе описывается предоставление разрешений на использование консоли администрирования для имен входа.  
  
**Использование консоли администрирования**  
  
Для использования консоли администрирования для имени входа требуется разрешение на **Просмотр состояния сервера** на уровне сервера. Следующая инструкция SQL предоставляет разрешение **View Server State** для имени входа, чтобы `KimAbercrombie` пользователь Kim мог использовать консоль администрирования для наблюдения за устройством SQL Server PDW.  
  
```sql  
USE master;  
GO  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
GO  
```  
  
**Уничтожить сеансы**  
  
Чтобы предоставить имени входа разрешение на уничтожение сеансов, предоставьте разрешение **ALTER ANY Connection** следующим образом:  
  
```sql  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
## <a name="grant-permissions-to-load-data"></a>Предоставление разрешений на загрузку данных
В этом разделе описано, как предоставить разрешения ролям базы данных и пользователям базы данных для загрузки данных в SQL Server Пдвапплианце.  
  
Следующий скрипт показывает, какие разрешения требуются для каждого параметра загрузки. Его можно изменить в соответствии с конкретными потребностями.  
  
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
  
## <a name="grant-permissions-to-copy-data-off-the-appliance"></a>Предоставление разрешений на Копирование данных устройства
В этом разделе описывается предоставление разрешений пользователю или роли базы данных для копирования данных с устройства SQL Server PDW.  
  
Для перемещения данных в другое расположение необходимо разрешение **SELECT** на таблицу, содержащую перемещаемые данные.  
  
Если целевым объектом для данных является другой SQL Server PDW, пользователь должен иметь разрешение **CREATE TABLE** на назначение и разрешение **ALTER SCHEMA** на схему, которая будет содержать таблицу.  
  
## <a name="grant-permissions-to-manage-databases"></a>Предоставление разрешений на управление базами данных
В этом разделе описывается предоставление разрешений пользователю базы данных для управления базой данных на SQL Server PDW устройстве.  
  
В некоторых ситуациях компания назначает руководителя для базы данных. Диспетчер управляет доступом к базе данных с другими именами входа, а также к данным и объектам в базе данных. Для управления всеми объектами, ролями и пользователями в базе данных предоставьте пользователю разрешение **Control** в базе данных. Следующая инструкция предоставляет пользователю `KimAbercrombie`разрешение **Control** для базы данных **AdventureWorksPDW2012** .  
  
```sql
USE AdventureWorksPDW2012;  
GO  
GRANT CONTROL ON DATABASE:: AdventureWorksPDW2012 TO KimAbercrombie;  
```  
  
Чтобы предоставить кому-либо разрешение на управление всеми базами данных на устройстве, предоставьте разрешение **ALTER ANY DATABASE** в базе данных master.  
  
## <a name="grant-permissions-to-manage-logins-users-and-database-roles"></a>Предоставление разрешений на управление именами входа, пользователями и ролями базы данных
В этом разделе описано, как предоставить разрешения на управление именами входа, пользователями базы данных и ролями базы данных.  
  
### <a name="PermsAdminConsole"></a>Предоставление разрешений на управление именами входа  
**Добавление имен для входа или управление ими**  
  
Приведенные ниже инструкции SQL создают имя входа с именем Кимаберкромбие, которое может создавать новые имена входа с помощью инструкции [CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md) и ALTER existing, используя инструкцию [ALTER LOGIN](../t-sql/statements/alter-login-transact-sql.md) .  
  
Разрешение **ALTER ANY LOGIN** предоставляет возможность создавать новые имена входа и удалять существующие. После того как имя входа существует, имя входа может управляться именами входа с разрешением **ALTER ANY LOGIN** или разрешением **ALTER** для этого имени входа. Имя входа может изменить пароль и базу данных по умолчанию для собственного имени входа.  
  
```sql 
CREATE LOGIN KimAbercrombie   
WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
GO  
  
GRANT ALTER ANY LOGIN TO KimAbercrombie;  
```  
  
### <a name="grant-permissions-to-manage-login-sessions"></a>Предоставление разрешений на управление сеансами входа  
Чтобы иметь возможность просматривать все сеансы на сервере, требуется разрешение **View Server State** . Для завершения сеансов других имен входа требуется разрешение **ALTER ANY Connection** . В следующем примере используется имя `KimAbercrombie` входа, созданное ранее.  
  
```sql  
-- Grant permissions to view sessions and queries  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
  
-- Grant permission to end sessions  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
### <a name="grant-permission-to-manage-database-users"></a>Предоставление разрешения на управление пользователями базы данных  
Для создания и удаления пользователей базы данных требуется разрешение **ALTER ANY USER** . Для управления существующими пользователями требуется разрешение **ALTER ANY USER** или разрешение **ALTER** для этого пользователя. В следующем примере используется имя `KimAbercrombie` входа, созданное ранее.  
  
```sql  
-- Create a user  
USE AdventureWorksPDW2012;  
GO  
CREATE USER KimAbercrombie;  
  
-- Grant permissions to create and drop users   
GRANT ALTER ANY USER TO KimAbercrombie;  
```  
  
### <a name="grant-permisson-to-manage-database-roles"></a>Предоставление разрешение для управления ролями базы данных  
Для создания и удаления пользовательских ролей базы данных требуется разрешение **ALTER ANY ROLE** . В следующем примере используется имя `KimAbercrombie` входа и использование, созданное ранее.  
  
```sql  
USE AdventureWorksPDW2012;  
GO  
-- Grant permissions to create and drop roles  
GRANT ALTER ANY ROLE TO KimAbercrombie;  
```  
  
### <a name="login-user-and-role-permission-charts"></a>Диаграммы разрешений для входа, пользователей и ролей  
Приведенные ниже диаграммы могут быть запутанными, но они показывают, как более высокие разрешения на ручки (например, элемент управления) включают более детализированные разрешения, которые могут быть предоставлены отдельно (например, ALTER). Рекомендуется всегда предоставлять минимально необходимое количество разрешений для выполнения необходимых задач. Для этого предоставьте более конкретные разрешения вместо разрешений верхнего уровня.  
  
**Разрешения для входа:**  
  
![Разрешения APS для безопасного входа](./media/grant-permissions/APS_security_login_perms.png "APS_security_login_perms")  
  
**Разрешения пользователя:**  
  
![Пользовательские разрешения безопасности APS](./media/grant-permissions/APS_security_user_perms.png "APS_security_user_perms")  
  
**Разрешения роли:**  
  
![Разрешения роли безопасности APS](./media/grant-permissions/APS_security_role_perms.png "APS_security_role_perms")  
  
<!-- MISSING LINKS
For a list of all permissions, see [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md).  
  
-->

## <a name="grant-permissions-to-monitor-the-appliance"></a>Предоставление разрешений для мониторинга устройства
Устройство SQL Server PDW можно отслеживать с помощью консоли администрирования или системных представлений SQL Server PDW. Для входа требуется разрешение на **Просмотр состояния сервера** на уровне сервера для мониторинга устройства. Для имен входа требуется разрешение **ALTER ANY Connection** для завершения подключений с помощью консоли администрирования или команды **Kill** . Сведения о разрешениях, необходимых для использования консоли администрирования, см. [в разделе Предоставление разрешений на использование консоли администрирования &#40;SQL Server PDW&#41;](#grant-permissions-to-use-the-admin-console).  
  
### <a name="PermsAdminConsole"></a>Предоставление разрешения на мониторинг устройства с помощью системных представлений  
Следующие инструкции SQL создают имя входа `monitor_login` и предоставляют разрешение **View Server State** для `monitor_login` имени входа.  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_login WITH PASSWORD='Password4321';  
GRANT VIEW SERVER STATE TO monitor_login;  
GO  
```  
  
### <a name="grant-permission-to-monitor-the-appliance-by-using-system-views-and-to-terminate-connections"></a>Предоставление разрешения на мониторинг устройства с помощью системных представлений и прерывание подключений  
Следующие инструкции SQL создают `monitor_and_terminate_login` имя входа и предоставляют разрешения на **Просмотр состояния сервера** и **изменение любых подключений** к `monitor_and_terminate_login` имени входа.  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_and_terminate_login WITH PASSWORD='Password1234';   
GRANT VIEW SERVER STATE TO monitor_and_terminate_login;   
GRANT ALTER ANY CONNECTION TO monitor_and_terminate_login;  
GO  
```  
  
Сведения о создании имен входа администратора см. в разделе Предопределенные [роли сервера](pdw-permissions.md#fixed-server-roles).  
  
## <a name="see-also"></a>См. также раздел
[CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md)  
[СОЗДАНИЕ ПОЛЬЗОВАТЕЛЯ](../t-sql/statements/create-user-transact-sql.md)  
[CREATE ROLE](../t-sql/statements/create-role-transact-sql.md)  
[Загрузить](load-overview.md)  
