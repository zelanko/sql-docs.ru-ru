---
title: Изменение оптимизированных для памяти таблиц | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 690b70b7-5be1-4014-af97-54e531997839
author: rothja
ms.author: jroth
ms.openlocfilehash: e6e28e6d1bb923fb226e7df7964853685f23178b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050377"
---
# <a name="altering-memory-optimized-tables"></a>Изменение таблиц с оптимизацией для памяти
  Выполнение операций ALTER для оптимизированных для памяти таблиц не поддерживается. Сюда входят такие операции, как изменение bucket_count, добавление или удаление индекса, добавление или удаление столбца. В этом разделе представлены рекомендации о том, как обновить оптимизированные для памяти таблицы.  
  
## <a name="updating-the-definition-of-a-memory-optimized-table"></a>Обновление определения таблицы, оптимизированной для памяти  
 Для обновления определения оптимизированной для памяти таблицы требуется создать новую таблицу с обновленным определением, скопировать в нее данные и начать ее использовать. Если таблица была доступна не только для чтения, то необходимо остановить рабочую нагрузку на таблицу, чтобы не допустить изменений в таблице, пока выполняется копирование данных.  
  
 В следующей процедуре описаны шаги, необходимые для обновления таблицы. В этом примере обновление добавляет индекс. Эта процедура сохраняет имя таблицы и требует выполнения двух операций копирования данных: один раз во временную таблицу и один раз в новую таблицу. Изменение bucket_count индекса, добавление или удаление столбца выполняются таким же образом.  
  
1.  Остановите рабочую нагрузку на таблицу.  
  
2.  Создайте скрипт для таблицы и добавьте в него новый индекс.  
  
3.  Создайте скрипт для привязанных к схеме объектов (в основном скомпилированных в собственном коде хранимых процедур), ссылающихся на T и их разрешения.  
  
     Привязанные к схеме объекты, ссылающиеся на таблицу, можно найти с помощью следующего запроса:  
  
    ```sql  
    declare @t nvarchar(255) = N'<table name>'  
  
    select r.referencing_schema_name, r.referencing_entity_name  
    from sys.dm_sql_referencing_entities (@t, 'OBJECT') as r join sys.sql_modules m on r.referencing_id=m.object_id  
    where r.is_caller_dependent = 0 and m.is_schema_bound=1;  
    ```  
  
     Разрешения хранимой процедуры можно включить в скрипт, используя следующий код [!INCLUDE[tsql](../../includes/tsql-md.md)]:  
  
    ```sql  
    declare @sp nvarchar(255) = N'<procedure name>'  
    declare @permissions nvarchar(max) = N''  
  
    select @permissions += dp.state_desc + N' ' + dp.permission_name + N' ON ' +   
       quotename(schema_name(o.schema_id)) + N'.' + quotename(o.name) + N' TO ' +  
       quotename(u.name) + N'; ' + char(13)  
    from sys.database_permissions as dp  
  
    join sys.database_principals as u  
       on u.principal_id = dp.grantee_principal_id  
  
    join sys.objects as o  
       on o.object_id = dp.major_id  
    where dp.class = 1 /* object */  
       and dp.minor_id = 0 and o.object_id=object_id(@sp);  
  
    select @permissions  
    ```  
  
4.  Создайте копию таблицы и скопируйте данные из исходной таблицы в копию. Копию можно создать с помощью следующей [!INCLUDE[tsql](../../includes/tsql-md.md)] <sup>1</sup>.  
  
    ```sql  
    select * into dbo.T_copy from dbo.T  
    ```  
  
     Если объем доступной памяти достаточно, `T_copy` может быть оптимизированной для памяти таблицей, что ускоряет копирование данных.<sup> 2</sup>  
  
5.  Удалите привязанные к схеме объекты, ссылающиеся на исходную таблицу.  
  
6.  Удалите исходную таблицу.  
  
7.  Создайте новую таблицу (`T`) со скриптом, содержащим новый индекс.  
  
8.  Скопируйте данные из `T_copy` в `T`.  
  
9. Повторно создайте ссылочные объекты, привязанные к схеме, и примените разрешения.  
  
10. Запустите рабочую нагрузку на `T`.  
  
 <sup>1</sup> Примечание, которое `T_copy` сохраняется на диске в этом примере. Если имеется резервная копия `T`, то `T_copy` может быть временной или недолговечной таблицей.  
  
 <sup>2</sup> должен быть достаточный объем памяти для `T_copy` . Память не освобождается сразу же после `DROP TABLE`. Если `T_copy` оптимизирована для памяти, должно быть достаточно памяти для двух дополнительных копий `T`. Если `T_copy` является таблицей, находящейся на диске, то свободной памяти должно быть достаточно только для одной дополнительной копии `T` из-за необходимости отработки сборщика мусора после удаления старой версии `T`.  
  
## <a name="changing-schema-powershell"></a>Изменение схемы (PowerShell)  
 Следующие скрипты PowerShell подготавливают и формируют изменения схемы, создавая скрипты для таблицы и соответствующих разрешений.  
  
```powershell
prepare_schema_change.ps1 <serverName> <databaseName> <schemaName> <tableName>
```
  
 Данный скрипт принимает в качестве аргумента таблицу, включает в скрипт объект и его разрешения, а также ссылочные, привязанные к схеме объекты и их разрешения в текущей папке. Всего формируются 7 скриптов для обновления схемы входной таблицы:  
  
-   копирование данных во временную таблицу (куча);  
  
-   удаление привязанных к схеме объектов, которые ссылаются на таблицу;  
  
-   Удалите таблицу.  
  
-   воссоздание таблицы с новой схемой и повторное применение разрешений;  
  
-   копирование данных из временной таблицы в воссозданную таблицу;  
  
-   повторное создание привязанных к схеме объектов, ссылающихся на таблицу, и их разрешений;  
  
-   удаление временной таблицы.  
  
 Скрипт для шага 4 необходимо обновить в целях отражения нужных изменений схемы. Если произошли какие-либо изменения в столбцах таблицы, то скрипты для шагов 5 (копирование данных из временной таблицы) и 6 (повторное создание хранимых процедур) необходимо обновить соответствующим образом.  
  
```powershell
# Prepare for schema changes by scripting out the table, as well as associated permissions
# Usage: prepare_schema_change.ps1 server_name db_name schema_name table_name  
# stop execution once an error occurs  
$ErrorActionPreference="Stop"  
  
if($args.Count -le 3)  
{  
   throw "Usage prepare_schema_change.ps1 server_name db_name schema_name table_name"  
}  
  
$servername = $args[0]  
$database = $args[1]  
$schema = $args[2]  
$object = $args[3]  
  
$object_heap = "$object$(Get-Random)"  
  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.SMO") | Out-Null  
  
$server =  New-Object ("Microsoft.SqlServer.Management.SMO.Server") ($servername)  
$scripter = New-Object ("Microsoft.SqlServer.Management.SMO.Scripter") ($server)  
  
## initialize table variable  
$tableUrn = $server.Databases[$database].Tables[$object, $schema]  
if($tableUrn.Count -eq 0)  
{  
   throw "Table or database not found"  
}  
  
## initialize scripting object  
$scriptingOptions = New-Object ("Microsoft.SqlServer.Management.SMO.ScriptingOptions")
$scriptingOptions.Permissions = $True  
$scriptingOptions.ScriptDrops = $True  
  
$scripter.Options = $scriptingOptions;  
  
Write-Host "(1) Scripting SELECT INTO $object_heap for table [$object] to 1_copy_to_heap_for_$schema`_$object.sql"  
Echo "SELECT * INTO $schema.$object_heap FROM $schema.$object WITH (SNAPSHOT)" | Out-File "1_copy_to_heap_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(2) Scripting DROP for procs schema-bound to [$object] 2_drop_procs_$schema`_$object.sql"  
## query referencing schema-bound objects  
$dt = $server.Databases[$database].ExecuteWithResults("select r.referencing_schema_name, r.referencing_entity_name  
from sys.dm_sql_referencing_entities ('$schema.$object', 'OBJECT') as r join sys.sql_modules m on r.referencing_id=m.object_id  
where r.is_caller_dependent = 0 and m.is_schema_bound=1;")  
  
## initialize out file  
Echo "" | Out-File "2_drop_procs_$schema`_$object.sql"  
## loop through schema-bound objects  
ForEach ($t In $dt.Tables)  
{    
   ForEach ($r In $t.Rows)  
   {    
      ## script object   
      $so =  $server.Databases[$database].StoredProcedures[$r[1], $r[0]]  
      $scripter.Script($so) | Out-File -Append "2_drop_procs_$schema`_$object.sql"  
   }  
}  
Write-Host "--done--"  
Write-Host ""  
Write-Host "(3) Scripting DROP table for [$object] to 3_drop_table_$schema`_$object.sql"
$scripter.Script($tableUrn) | Out-File "3_drop_table_$schema`_$object.sql";
Write-Host "--done--"  
Write-Host ""  
  
## now script creates  
$scriptingOptions.ScriptDrops = $False  
  
Write-Host "(4) Scripting CREATE table and permissions for [$object] to !please_edit_4_create_table_$schema`_$object.sql"  
Write-Host "***** rename this script to 4_create_table.sql after completing the updates to the schema"
$scripter.Script($tableUrn) | Out-File "!please_edit_4_create_table_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(5) Scripting INSERT INTO table from heap and UPDATE STATISTICS for [$object] to 5_copy_from_heap_$schema`_$object.sql"  
Write-Host "[update this script if columns are added to or removed from the table]"  
Echo "INSERT INTO [$schema].[$object] SELECT * FROM [$schema].[$object_heap]; UPDATE STATISTICS [$schema].[$object] WITH FULLSCAN, NORECOMPUTE" | Out-File "5_copy_from_heap_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(6) Scripting CREATE PROC and permissions for procedures schema-bound to [$object] to 6_create_procs_$schema`_$object.sql"  
Write-Host "[update the procedure definitions if columns are renamed or removed]"  
## initialize out file  
Echo "" | Out-File "6_create_procs_$schema`_$object.sql"  
## loop through schema-bound objects  
ForEach ($t In $dt.Tables)  
{    
   ForEach ($r In $t.Rows)  
   {    
      ## script the schema-bound object  
      $so =  $server.Databases[$database].StoredProcedures[$r[1], $r[0]]  
      ForEach($s In $scripter.Script($so))  
        {  
            Echo $s | Out-File -Append "6_create_procs_$schema`_$object.sql"  
            Echo "GO" | Out-File -Append "6_create_procs_$schema`_$object.sql"  
        }  
   }  
}  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(7) Scripting DROP $object_heap to 7_drop_heap_$schema`_$object.sql"  
Echo "DROP TABLE $schema.$object_heap" | Out-File "7_drop_heap_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
```  
  
 Следующий скрипт PowerShell выполняет изменения схемы, которые были указаны в предыдущем примере. Данный скрипт принимает в качестве аргумента таблицу и выполняет скрипты изменения схемы, созданные для этой таблицы и связанных хранимых процедур.  
  
 Использование: execute_schema_change.ps1 *server_name * * db_name `schema_name` table_name*  
  
```powershell
# stop execution once an error occurs  
$ErrorActionPreference="Stop"  
  
if($args.Count -le 3)  
{  
   throw "Usage execute_schema_change.ps1 server_name db_name schema_name table_name"  
}  
  
$servername = $args[0]  
$database = $args[1]  
$schema = $args[2]  
$object = $args[3]  
  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.SMO") | Out-Null  
  
$server =  New-Object ("Microsoft.SqlServer.Management.SMO.Server") ($servername)  
$database = $server.Databases[$database]  
$table = $database.Tables[$object, $schema]  
if($table.Count -eq 0)  
{  
   throw "Table or database not found"  
}  
  
$1 = Get-Item "1_copy_to_heap_$schema`_$object.sql"  
$2 = Get-Item "2_drop_procs_$schema`_$object.sql"  
$3 = Get-Item "3_drop_table_$schema`_$object.sql"  
$4 = Get-Item "4_create_table_$schema`_$object.sql"  
$5 = Get-Item "5_copy_from_heap_$schema`_$object.sql"  
$6 = Get-Item "6_create_procs_$schema`_$object.sql"  
$7 = Get-Item "7_drop_heap_$schema`_$object.sql"  
  
Write-Host "(1) Running SELECT INTO heap for table [$object] from 1_copy_to_heap_for_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $1.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(2) Running DROP for procs schema-bound from [$object] 2_drop_procs_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $2.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(3) Running DROP table for [$object] to 4_drop_table_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $3.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(4) Running CREATE table and permissions for [$object] from 4_create_table_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $4.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(5) Running INSERT INTO table from heap for [$object] and UPDATE STATISTICS from 5_copy_from_heap_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $5.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(6) Running CREATE PROC and permissions for procedures schema-bound to [$object] from 6_create_procs_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $6.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(7) Running DROP heap from 7_drop_heap_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $7.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
```  
  
## <a name="see-also"></a>См. также:  
 [Таблицы, оптимизированные для памяти](memory-optimized-tables.md)  
