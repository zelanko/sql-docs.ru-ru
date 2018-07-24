---
title: CREATE SERVER AUDIT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 01/22/2018
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CREATE_SERVER_AUDIT_TSQL
- SERVER AUDIT
- SERVER_AUDIT_TSQL
- CREATE SERVER AUDIT
dev_langs:
- TSQL
helpviewer_keywords:
- server audit [SQL Server]
- CREATE SERVER AUDIT statement
- audits [SQL Server], creating
ms.assetid: 1c321680-562e-41f1-8eb1-e7fa5ae45cc5
caps.latest.revision: 44
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 968ea430a01bddf25ccf0e477da2096b4019c7cf
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38050772"
---
# <a name="create-server-audit-transact-sql"></a>CREATE SERVER AUDIT (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Создает объект аудита сервера с помощью компонента аудита [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в статье [Подсистема аудита SQL Server (ядро СУБД)](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CREATE SERVER AUDIT audit_name  
{  
    TO { [ FILE (<file_options> [ , ...n ] ) ] | APPLICATION_LOG | SECURITY_LOG }  
    [ WITH ( <audit_options> [ , ...n ] ) ]   
    [ WHERE <predicate_expression> ]  
}  
[ ; ]  
  
<file_options>::=  
{  
        FILEPATH = 'os_file_path'  
    [ , MAXSIZE = { max_size { MB | GB | TB } | UNLIMITED } ]  
    [ , { MAX_ROLLOVER_FILES = { integer | UNLIMITED } } | { MAX_FILES = integer } ]  
    [ , RESERVE_DISK_SPACE = { ON | OFF } ]   
}  
  
<audit_options>::=  
{  
    [   QUEUE_DELAY = integer ]  
    [ , ON_FAILURE = { CONTINUE | SHUTDOWN | FAIL_OPERATION } ]  
    [ , AUDIT_GUID = uniqueidentifier ]  
}  
  
<predicate_expression>::=  
{  
    [NOT ] <predicate_factor>   
    [ { AND | OR } [NOT ] { <predicate_factor> } ]   
    [,...n ]  
}  
  
<predicate_factor>::=   
    event_field_name { = | < > | ! = | > | > = | < | < = } { number | ' string ' }  
```  
  
## <a name="arguments"></a>Аргументы  
 TO { FILE | APPLICATION_LOG | SECURITY_LOG }  
 Определяет расположение целевого объекта аудита. Возможными параметрами являются двоичный файл, журнал приложений Windows или журнал безопасности Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может выполнить запись в журнал безопасности Windows без настройки дополнительных параметров Windows. Дополнительные сведения см. в статье [Запись событий подсистемы аудита SQL Server в журнал безопасности](../../relational-databases/security/auditing/write-sql-server-audit-events-to-the-security-log.md).  
  
 FILEPATH ='*os_file_path*'  
 Путь к журналу аудита. Имя файла формируется на основе имени аудита и его идентификатора GUID.  
  
 MAXSIZE = { *max_size }*  
 Задает максимальный размер, до которого может увеличиваться файл аудита. Значение *max_size* должно быть целым числом, за которым следует MB, GB, TB или UNLIMITED. Минимальный размер для *max_size* составляет 2 МБ, а максимальный — 2 147 483 647 ТБ. Если указано значение UNLIMITED, увеличение размера файла будет происходить до заполнения диска. (0 также указывает на отсутствие ограничения.) Если указано значение менее 2 МБ, возникает ошибка MSG_MAXSIZE_TOO_SMALL. Значение по умолчанию — UNLIMITED.  
  
 MAX_ROLLOVER_FILES =*{ integer* | UNLIMITED }  
 Указывает максимальное количество файлов, хранимых в файловой системе помимо текущего. Значением *MAX_ROLLOVER_FILES* должно быть целое число или UNLIMITED. Значение по умолчанию — UNLIMITED. Этот параметр проверяется при каждом перезапуске аудита (это может происходить во время перезапуска экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] или после выключения и повторного включения аудита) или когда становится необходим новый файл, поскольку достигается предел MAXSIZE. Если при вычислении параметра *MAX_ROLLOVER_FILES* количество файлов превышает значение *MAX_ROLLOVER_FILES*, удаляется самый старый файл. Поэтому если параметр *MAX_ROLLOVER_FILES* имеет значение 0, то каждый раз, когда проверяется значение *MAX_ROLLOVER_FILES*, создается новый файл. При проверке значения *MAX_ROLLOVER_FILES* автоматически удаляется только один файл, поэтому если значение параметра *MAX_ROLLOVER_FILES* уменьшается, то количество файлов не будет сокращаться, если старые файлы не удалить вручную. Максимальное число файлов, которое можно указать, составляет 2 147 483 647.  
  
 MAX_FILES =*integer*  
 **Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Задает максимальное число файлов аудита, которые могут быть созданы. При достижении предела переключение на первый файл не производится. При достижении предела MAX_FILES любое действие, которое вызывает создание дополнительных событий аудита, завершается ошибкой.  
  
 RESERVE_DISK_SPACE = { ON | OFF }  
 Этот параметр заранее размещает на диске файл в соответствии со значением MAXSIZE. Применяется, только если MAXSIZE не имеет значения UNLIMITED. Значение по умолчанию — OFF.  
  
 QUEUE_DELAY =*integer*  
 Определяет задержку в миллисекундах, после которой продолжается выполнение действий аудита. Значение 0 соответствует синхронной доставке. Минимальное значение задаваемой задержки запроса составляет 1000 (1 секунда), и это значение используется по умолчанию. Максимальное значение составляет 2 147 483 647 (2 147 483,647 секунд или 24 дня, 20 часов, 31 минута и 23,647 секунд). Если указано недопустимое значение, происходит ошибка MSG_INVALID_QUEUE_DELAY.  
  
 ON_FAILURE = { CONTINUE | SHUTDOWN | FAIL_OPERATION }  
 Указывает, будет ли экземпляр, выполняющий запись в целевой объект, вызывать ошибку, продолжать работу или останавливать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если целевой объект не может выполнить запись в журнал аудита. Значение по умолчанию — CONTINUE.  
  
 CONTINUE  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работа продолжается. Записи аудита не сохраняются. Аудит продолжает попытки регистрации событий и возобновляется после устранения причины сбоя. Выбор варианта "Продолжить" разрешает непроверенные действия, которые могут нарушать политики безопасности. Используйте этот параметр, когда продолжение операции компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] является более важным, чем сохранение полного аудита.  
  
SHUTDOWN  
Приводит к принудительному завершению работы экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удается записать данные в целевой объект аудита по любой причине. Имя входа, выполняющее инструкцию `CREATE SERVER AUDIT`, должно иметь разрешение `SHUTDOWN` в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Поведение завершения работы сохраняется даже в том случае, если имя входа, выполняющее инструкцию, позднее отменяет разрешение `SHUTDOWN`. Если у пользователя нет этого разрешения, выполнение инструкции завершится ошибкой и аудит не будет создан. Используйте этот параметр, когда сбой аудита может нанести ущерб безопасности или целостности системы. Дополнительные сведения см. в разделе [SHUTDOWN](../../t-sql/language-elements/shutdown-transact-sql.md).  
  
 FAIL_OPERATION  
 Действия с базой данных завершаются ошибкой, если они вызывают события аудита. Действия, которые не вызывают события аудита, можно продолжить, но события аудита возникать не будут. Аудит продолжает попытки регистрации событий и возобновляется после устранения причины сбоя. Используйте этот параметр, если обеспечение полного аудита более важно, чем полный доступ к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].

 AUDIT_GUID =*uniqueidentifier*  
 Чтобы поддерживать такие сценарии, как зеркальное отображение базы данных, аудиту необходим конкретный идентификатор GUID, который совпадает с идентификатором GUID, найденным в зеркальной базе данных. Этот идентификатор GUID не может быть изменен после создания аудита.  
  
 predicate_expression  
 **Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Задает выражение предиката, используемое для определения необходимости обработки события. Выражения предиката ограничены 3000 символами, что является пределом для строковых аргументов.  
  
 event_field_name  
 **Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Имя поля события, которое идентифицирует источник предиката. Поля аудита описаны в разделе [sys.fn_get_audit_file (Transact-SQL)](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md). Фильтровать можно все поля, за исключением `file_name`, `audit_file_offset` и `event_time`.  

> [!NOTE]  
>  Хотя поля `action_id` и `class_type` имеют тип **varchar** в sys.fn_get_audit_file, их можно использовать только с числами, когда они служат источником предикатов для фильтрации. Чтобы получить список значений для использования с `class_type`, выполните следующий запрос:  
> ```sql
> SELECT spt.[name], spt.[number]
> FROM   [master].[dbo].[spt_values] spt
> WHERE  spt.[type] = N'EOD'
> ORDER BY spt.[name];
> ```


 number  
 **Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Любой числовой тип, включая **decimal**. Ограничения: недостаток доступной физической памяти или слишком большое число, которое невозможно представить 64-разрядным целым.  
  
 ' string '  
 **Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Для предикатного сравнения требуется строка в Юникоде или ANSI. Для функций предикатного сравнения не выполняется неявное преобразование строкового типа. Передача неверного типа приводит к ошибке.  
  
## <a name="remarks"></a>Remarks  
 После создания аудит сервера находится в отключенном состоянии.  
  
 Инструкция CREATE SERVER AUDIT относится к области транзакции. Если выполняется откат транзакции, происходит также откат этой инструкции.  
  
## <a name="permissions"></a>Разрешения  
 Чтобы создать, изменить или удалить аудит сервера, участникам требуется разрешение ALTER ANY SERVER AUDIT или CONTROL SERVER.  
  
 Если данные аудита сохраняются в файл, то для предотвращения подмены можно ограничить доступ к файлу.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-server-audit-with-a-file-target"></a>A. Создание аудита сервера с целевым файлом  
 В следующем примере создается аудит сервера с именем `HIPPA_Audit`, не имеющий параметров, для которого целевым является двоичный файл.  
  
```sql  
CREATE SERVER AUDIT HIPAA_Audit  
    TO FILE ( FILEPATH ='\\SQLPROD_1\Audit\' );  
```  
  
### <a name="b-creating-a-server-audit-with-a-windows-application-log-target-with-options"></a>Б. Создание аудита сервера для журнала приложений Windows с параметрами  
 В следующем примере создается аудит сервера с именем `HIPPA_Audit` и журналом приложений Windows в качестве цели. Очередь записывается каждую секунду и останавливает ядро [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при ошибке.  
  
```sql  
CREATE SERVER AUDIT HIPAA_Audit  
    TO APPLICATION_LOG  
    WITH ( QUEUE_DELAY = 1000,  ON_FAILURE = SHUTDOWN);  
```  
  
###  <a name="ExampleWhere"></a> В. Создание аудита сервера, содержащего предложение WHERE  
 В следующем примере создается база данных, схема и две таблицы. Таблица с именем `DataSchema.SensitiveData` содержит конфиденциальные данные, и доступ к ней должен регистрироваться в аудите. Таблица с именем `DataSchema.GeneralData` не содержит конфиденциальных данных. Спецификация аудита базы данных осуществляет аудит доступа ко всем объектам в схеме `DataSchema`. Аудит сервера создается с предложением WHERE, которое ограничивает аудит сервера таблицей `SensitiveData`. Аудит сервера предполагает наличие папки аудита в `C:\SQLAudit`.  
  
```sql  
CREATE DATABASE TestDB;  
GO  
USE TestDB;  
GO  
CREATE SCHEMA DataSchema;  
GO  
CREATE TABLE DataSchema.GeneralData (ID int PRIMARY KEY, DataField varchar(50) NOT NULL);  
GO  
CREATE TABLE DataSchema.SensitiveData (ID int PRIMARY KEY, DataField varchar(50) NOT NULL);  
GO  
-- Create the server audit in the master database  
USE master;  
GO  
CREATE SERVER AUDIT AuditDataAccess  
    TO FILE ( FILEPATH ='C:\SQLAudit\' )  
    WHERE object_name = 'SensitiveData' ;  
GO  
ALTER SERVER AUDIT AuditDataAccess WITH (STATE = ON);  
GO  
-- Create the database audit specification in the TestDB database  
USE TestDB;  
GO  
CREATE DATABASE AUDIT SPECIFICATION [FilterForSensitiveData]  
FOR SERVER AUDIT [AuditDataAccess]   
ADD (SELECT ON SCHEMA::[DataSchema] BY [public])  
WITH (STATE = ON);  
GO  
-- Trigger the audit event by selecting from tables  
SELECT ID, DataField FROM DataSchema.GeneralData;  
SELECT ID, DataField FROM DataSchema.SensitiveData;  
GO  
-- Check the audit for the filtered content  
SELECT * FROM fn_get_audit_file('C:\SQLAudit\AuditDataAccess_*.sqlaudit',default,default);  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER SERVER AUDIT (Transact-SQL)](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT (Transact-SQL)](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [CREATE SERVER AUDIT SPECIFICATION (Transact-SQL)](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION (Transact-SQL)](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION (Transact-SQL)](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [CREATE DATABASE AUDIT SPECIFICATION (Transact-SQL)](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION (Transact-SQL)](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [DROP DATABASE AUDIT SPECIFICATION (Transact-SQL)](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION (Transact-SQL)](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.fn_get_audit_file (Transact-SQL)](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys.server_audits (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys.server_file_audits (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.server_audit_specification_details (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys.database_audit_specifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_actions (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [sys.dm_audit_class_type_map (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Создание аудита сервера и спецификации аудита сервера](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
