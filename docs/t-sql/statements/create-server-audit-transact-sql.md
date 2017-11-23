---
title: "Создание АУДИТА сервера (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_SERVER_AUDIT_TSQL
- SERVER AUDIT
- SERVER_AUDIT_TSQL
- CREATE SERVER AUDIT
dev_langs: TSQL
helpviewer_keywords:
- server audit [SQL Server]
- CREATE SERVER AUDIT statement
- audits [SQL Server], creating
ms.assetid: 1c321680-562e-41f1-8eb1-e7fa5ae45cc5
caps.latest.revision: "44"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 436cca29066a1fc9e296dca2c66f1503189102a2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="create-server-audit-transact-sql"></a>CREATE SERVER AUDIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает объект аудита сервера с помощью компонента аудита [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в статье [Подсистема аудита SQL Server (компонент Database Engine)](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
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
  
 FILEPATH = "*os_file_path*"  
 Путь к журналу аудита. Имя файла формируется на основе имени аудита и его идентификатора GUID.  
  
 Параметр MAXSIZE = { *max_size}*  
 Задает максимальный размер, до которого может увеличиваться файл аудита. *Max_size* значение должно быть целым, МБ, ГБ, ТБ и без ограничений. Минимальный размер, который можно указать для *max_size* 2 МБ, максимальное — 2 147 483 647 ТБ. Если указано значение UNLIMITED, увеличение размера файла будет происходить до заполнения диска. (0 также указывает на отсутствие ограничения.) Указав значение менее 2 МБ вызывает ошибка MSG_MAXSIZE_TOO_SMALL. Значение по умолчанию — UNLIMITED.  
  
 MAX_ROLLOVER_FILES =*{целое* | НЕОГРАНИЧЕННОЕ}  
 Указывает максимальное количество файлов, хранимых в файловой системе помимо текущего. *MAX_ROLLOVER_FILES* значение должно быть целым числом или без ограничений. Значение по умолчанию — UNLIMITED. Этот параметр проверяется при каждом перезапуске аудита (это может происходить при экземпляр [!INCLUDE[ssDE](../../includes/ssde-md.md)] перезагрузки или при включении аудита и включите снова) или при необходимости создается новый файл, так как достигнуто параметр MAXSIZE. Когда *MAX_ROLLOVER_FILES* вычисляется, если число файлов превышает *MAX_ROLLOVER_FILES* задание, удаляется самый старый файл. В результате, когда параметр *MAX_ROLLOVER_FILES* равно 0, новый файл создается каждый раз *MAX_ROLLOVER_FILES* оценивается параметр. Только один файл будет автоматически удалены при *MAX_ROLLOVER_FILES* параметр оценивается, поэтому если значение *MAX_ROLLOVER_FILES* — уменьшается, количество файлов не сокращаться, если старые файлы, удалить вручную. Максимальное число файлов, которое можно указать, составляет 2 147 483 647.  
  
 MAX_FILES =*целое число со знаком*  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Задает максимальное число файлов аудита, которые могут быть созданы. При достижении предела переключение на первый файл не производится. При достижении предела MAX_FILES любое действие, которое вызывает дополнительных событий аудита формироваться, завершается с ошибкой.  
  
 RESERVE_DISK_SPACE = { ON | OFF }  
 Этот параметр заранее размещает на диске файл в соответствии со значением MAXSIZE. Применяется, только если MAXSIZE не имеет значения UNLIMITED. Значение по умолчанию — OFF.  
  
 QUEUE_DELAY =*целое число со знаком*  
 Определяет задержку в миллисекундах, после которой продолжается выполнение действий аудита. Значение 0 соответствует синхронной доставке. Минимальное значение задаваемой задержки запроса составляет 1000 (1 секунда), и это значение используется по умолчанию. Максимальное значение составляет 2 147 483 647 (2 147 483,647 секунд или 24 дня, 20 часов, 31 минута и 23,647 секунд). Если указано недопустимое значение, возникает ошибка MSG_INVALID_QUEUE_DELAY.  
  
 ON_FAILURE = {ПРОДОЛЖИТЬ | ЗАВЕРШЕНИЕ РАБОТЫ | FAIL_OPERATION}  
 Указывает, будет ли экземпляр, выполняющий запись в целевой объект, вызывать ошибку, продолжать работу или останавливать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если целевой объект не может выполнить запись в журнал аудита. Значение по умолчанию — CONTINUE.  
  
 CONTINUE  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работа продолжается. Записи аудита не сохраняются. Аудит продолжает попытки регистрации событий и возобновляется, если причина сбоя будет устранена. Выбрав вариант продолжения можно разрешить непроверенные действия, которые могут нарушать политики безопасности. Используйте этот параметр, когда продолжение операции компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] является более важным, чем сохранение полного аудита.  
  
SHUTDOWN  
Вызывает экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершить работу, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удалось записать данные в цель аудита по любой причине. Пользователь, который запустил `CREATE SERVER AUDIT` оператора должен быть `SHUTDOWN` разрешения внутри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. С завершением работы сохраняется даже в том случае, если `SHUTDOWN` позже отменено разрешение от выполнения входа. Если пользователь не имеет этого разрешения, то инструкция завершается с ошибками и аудита не быть создается. Используйте этот параметр, когда сбой аудита может нанести ущерб безопасности или целостности системы. Дополнительные сведения см. в разделе [завершение работы](../../t-sql/language-elements/shutdown-transact-sql.md).  
  
 FAIL_OPERATION  
 Действия с базой данных завершаются ошибкой, если они вызывают события аудита. Действия, которые не вызывают события аудита, можно продолжить, но могут быть отсутствуют события аудита. Аудит продолжает попытки регистрации событий и возобновляется, если причина сбоя будет устранена. Используйте этот параметр, если обеспечение полного аудита более важно, чем полный доступ к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].

 AUDIT_GUID =*uniqueidentifier*  
 Чтобы поддерживать такие сценарии, как зеркальное отображение базы данных, аудиту необходим конкретный идентификатор GUID, который совпадает с идентификатором GUID, найденным в зеркальной базе данных. Этот идентификатор GUID не может быть изменен после создания аудита.  
  
 predicate_expression  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Задает выражение предиката, используемое для определения необходимости обработки события. Выражения предиката ограничены 3000 символами, что является пределом для строковых аргументов.  
  
 event_field_name  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Имя поля события, которое идентифицирует источник предиката. Поля аудита описаны в [sys.fn_get_audit_file &#40; Transact-SQL &#41; ](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md). Аудиту могут быть подвержены все поля, за исключением `file_name` и `audit_file_offset`.  
  
 number  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 — Включая любого числового типа **десятичное**. Ограничения: недостаток доступной физической памяти или слишком большое число, которое невозможно представить 64-разрядным целым.  
  
 ' string '  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Для предикатного сравнения требуется строка в Юникоде или ANSI. Для функций предикатного сравнения не выполняется неявное преобразование строкового типа. Передача неверного типа приводит к ошибке.  
  
## <a name="remarks"></a>Замечания  
 После создания аудит сервера находится в отключенном состоянии.  
  
 Инструкция CREATE SERVER AUDIT относится к области транзакции. Если выполняется откат транзакции, происходит также откат этой инструкции.  
  
## <a name="permissions"></a>Permissions  
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
 В следующем примере создается база данных, схема и две таблицы. Таблица с именем `DataSchema.SensitiveData` содержит конфиденциальные данные и доступ к таблице должны записываться в аудите. Таблица с именем `DataSchema.GeneralData` не содержит конфиденциальных данных. Спецификация аудита базы данных осуществляет аудит доступа ко всем объектам в схеме `DataSchema`. Аудит сервера создается с предложением WHERE, которое ограничивает аудит сервера таблицей `SensitiveData`. Аудит сервера предполагает аудита папка существует в `C:\SQLAudit`.  
  
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
 [ALTER SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [Создание СПЕЦИФИКАЦИИ АУДИТА сервера &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [СОЗДАТЬ СПЕЦИФИКАЦИЮ АУДИТА базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [УДАЛИТЬ СПЕЦИФИКАЦИЮ АУДИТА базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.fn_get_audit_file &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys.server_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys.server_file_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.server_audit_specification_details &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys.database_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_actions &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [sys.dm_audit_class_type_map &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Создание аудита сервера и спецификации аудита сервера](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
