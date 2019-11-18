---
title: ALTER SERVER AUDIT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER_SERVER_AUDIT_TSQL
- ALTER SERVER AUDIT
dev_langs:
- TSQL
helpviewer_keywords:
- server audit [SQL Server]
- audits [SQL Server], specification
- ALTER SERVER AUDIT statement
ms.assetid: 63426d31-7a5c-4378-aa9e-afcf4f64ceb3
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: c4649a591f7261943d2d5393678f63888930c01f
ms.sourcegitcommit: e37636c275002200cf7b1e7f731cec5709473913
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2019
ms.locfileid: "73982038"
---
# <a name="alter-server-audit--transact-sql"></a>ALTER SERVER AUDIT (Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Изменяет объект аудита сервера с помощью функции аудита [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в статье [Подсистема аудита SQL Server (ядро СУБД)](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ALTER SERVER AUDIT audit_name  
{  
    [ TO { { FILE ( <file_options> [, ...n] ) } | APPLICATION_LOG | SECURITY_LOG } | URL]  
    [ WITH ( <audit_options> [ , ...n] ) ]   
    [ WHERE <predicate_expression> ]  
}  
| REMOVE WHERE  
| MODIFY NAME = new_audit_name  
[ ; ]  
  
<file_options>::=  
{  
      FILEPATH = 'os_file_path'   
    | MAXSIZE = { max_size { MB | GB | TB } | UNLIMITED }   
    | MAX_ROLLOVER_FILES = { integer | UNLIMITED }   
    | MAX_FILES = integer   
    | RESERVE_DISK_SPACE = { ON | OFF }   
}  
  
<audit_options>::=  
{  
      QUEUE_DELAY = integer   
    | ON_FAILURE = { CONTINUE | SHUTDOWN | FAIL_OPERATION }   
    | STATE = = { ON | OFF }   
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
 TO { FILE | APPLICATION_LOG | SECURITY |URL}  
 Определяет расположение целевого объекта аудита. Возможные режимы — двоичный файл, журнал событий приложений Windows или журнал безопасности Windows.  

> [!IMPORTANT]
> В управляемом экземпляре Базы данных SQL Azure компонент аудита SQL выполняется на уровне сервера и сохраняет файлы `.xel` в хранилище BLOB-объектов Azure.
  
 FILEPATH **= '** _os\_file\_path_ **'**  
 Путь следа аудита. Имя файла формируется на основе имени аудита и его идентификатора GUID.  
  
 MAXSIZE **=** _max\_size_  
 Задает максимальный размер, до которого может увеличиваться файл аудита. Значение *max_size* должно быть целым числом, за которым следует **MB**, **GB**, **TB** или **UNLIMITED**. Минимальный размер для *max_size* составляет 2 **МБ**, а максимальный — 2 147 483 647 **ТБ**. Если указано значение **UNLIMITED**, увеличение размера файла будет происходить до заполнения диска. Если указано значение менее 2 МБ, возникает ошибка MSG_MAXSIZE_TOO_SMALL. Значение по умолчанию — **UNLIMITED**.  
  
 MAX_ROLLOVER_FILES **=** _integer_ | **UNLIMITED**  
 Задает максимальное число файлов, которые хранятся в файловой системе. Если установлено значение MAX_ROLLOVER_FILES=0, отсутствует ограничение на число создаваемых файлов продолжения. Значение по умолчанию — 0. Максимальное число файлов, которое можно указать, составляет 2 147 483 647.  
  
 MAX_FILES =*integer*  
 Задает максимальное число файлов аудита, которые могут быть созданы. При достижении предела переключение на первый файл не производится. При достижении предела MAX_FILES любое действие, которое вызывает создание дополнительных событий аудита, завершается ошибкой.  
**Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.  
  
 RESERVE_DISK_SPACE **=** { ON | OFF }  
 Этот параметр заранее размещает на диске файл в соответствии со значением MAXSIZE. Применяется, только если значение MAXSIZE не равно UNLIMITED. Значение по умолчанию — OFF.  
  
 QUEUE_DELAY **=** _integer_  
 Определяет задержку в миллисекундах, после которой продолжается выполнение действий аудита. Значение 0 соответствует синхронной доставке. Минимальное значение задаваемой задержки запроса составляет 1000 (1 секунда), и это значение используется по умолчанию. Максимальное значение составляет 2 147 483 647 (2 147 483,647 секунд или 24 дня, 20 часов, 31 минута и 23,647 секунд). Если указано недопустимое значение, происходит ошибка MSG_INVALID_QUEUE_DELAY.  
  
 ON_FAILURE **=** { CONTINUE | SHUTDOWN | FAIL_OPERATION}  
 Указывает, будет ли экземпляр, выполняющий запись в целевой объект, вызывать ошибку, продолжать работу или остановится, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может выполнить запись в журнал аудита.  
  
 CONTINUE  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работа продолжается. Записи аудита не сохраняются. Аудит продолжает попытки регистрации событий и возобновляется после устранения причины сбоя. Выбор варианта "Продолжить" разрешает непроверенные действия, которые могут нарушать политики безопасности. Используйте этот параметр, когда продолжение операции компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] является более важным, чем сохранение полного аудита.  
  
SHUTDOWN  
Приводит к принудительному завершению работы экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удается записать данные в целевой объект аудита по любой причине. Имя входа, выполняющее инструкцию `ALTER`, должно иметь разрешение `SHUTDOWN` в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Поведение завершения работы сохраняется даже в том случае, если имя входа, выполняющее инструкцию, позднее отменяет разрешение `SHUTDOWN`. Если у пользователя нет этого разрешения, выполнение инструкции завершится ошибкой и аудит не будет изменен. Используйте этот параметр, когда сбой аудита может нанести ущерб безопасности или целостности системы. Дополнительные сведения см. в разделе [SHUTDOWN](../../t-sql/language-elements/shutdown-transact-sql.md). 
  
 FAIL_OPERATION  
 Действия с базой данных завершаются ошибкой, если они вызывают события аудита. Действия, которые не вызывают события аудита, можно продолжить, но события аудита возникать не будут. Аудит продолжает попытки регистрации событий и возобновляется после устранения причины сбоя. Используйте этот параметр, если обеспечение полного аудита более важно, чем полный доступ к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
 **Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.   
  
 STATE **=** { ON | OFF }  
 Включает или отключает аудит из сбора записей. При изменении состояния работающего аудита (из ON в OFF) создается запись аудита об остановке аудита, об остановившем аудит участнике и времени остановки аудита.  
  
 MODIFY NAME = *new_audit_name*  
 Изменяет имя аудита. Нельзя использовать совместно ни с каким другим параметром.  
  
 predicate_expression  
 Задает выражение предиката, используемое для определения необходимости обработки события. Выражения предиката ограничены 3000 символами, что является пределом для строковых аргументов.  
 **Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.  
  
 event_field_name  
 Имя поля события, которое идентифицирует источник предиката. Поля аудита описаны в разделе [sys.fn_get_audit_file (Transact-SQL)](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md). Аудиту могут быть подвержены все поля, за исключением `file_name` и `audit_file_offset`.  
 **Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.  
  
 number  
 Любой числовой тип, включая **decimal**. Ограничения: недостаток доступной физической памяти или слишком большое число, которое невозможно представить 64-разрядным целым.  
 **Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.  
  
 ' string '  
 Для предикатного сравнения требуется строка в Юникоде или ANSI. Для функций предикатного сравнения не выполняется неявное преобразование строкового типа. Передача неверного типа приводит к ошибке.  
 **Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.  
  
## <a name="remarks"></a>Remarks  
 В вызове ALTER AUDIT надо указывать хотя бы одно предложение из TO, WITH и MODIFY NAME.  
  
 Чтобы внести изменения в аудит, для состояния аудита необходимо установить параметр OFF. Если инструкция DROP AUDIT выполняется, когда аудит включен с любыми параметрами, отличными от STATE=OFF, выводится сообщение об ошибке MSG_NEED_AUDIT_DISABLED.  
  
 Можно добавлять, изменять или удалять спецификации аудита без остановки аудита.  
  
 После создания аудита нельзя изменить его идентификатор GUID.  
 
 Инструкцию **ALTER SERVER AUDIT** нельзя использовать в пользовательской транзакции.
 
## <a name="permissions"></a>Разрешения  
 Чтобы создать, изменить или удалить участника на уровне сервера требуется разрешение ALTER ANY SERVER AUDIT или CONTROL SERVER.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-changing-a-server-audit-name"></a>A. Изменение имени аудита сервера  
 В данном примере показано изменение имени аудита базы данных с `HIPAA_Audit` на `HIPAA_Audit_Old`.  
  
```  
USE master  
GO  
ALTER SERVER AUDIT HIPAA_Audit  
WITH (STATE = OFF);  
GO  
ALTER SERVER AUDIT HIPAA_Audit  
MODIFY NAME = HIPAA_Audit_Old;  
GO  
ALTER SERVER AUDIT HIPAA_Audit_Old  
WITH (STATE = ON);  
GO  
```  
  
### <a name="b-changing-a-server-audit-target"></a>Б. Изменение цели аудита сервера  
 В следующем примере аудит сервера с именем `HIPAA_Audit` изменяется на целевой файл.  
  
```  
USE master  
GO  
ALTER SERVER AUDIT HIPAA_Audit  
WITH (STATE = OFF);  
GO  
ALTER SERVER AUDIT HIPAA_Audit  
TO FILE (FILEPATH ='\\SQLPROD_1\Audit\',  
          MAXSIZE = 1000 MB,  
          RESERVE_DISK_SPACE=OFF)  
WITH (QUEUE_DELAY = 1000,  
       ON_FAILURE = CONTINUE);  
GO  
ALTER SERVER AUDIT HIPAA_Audit  
WITH (STATE = ON);  
GO  
```  
  
### <a name="c-changing-a-server-audit-where-clause"></a>В. Изменение предложения WHERE аудита сервера  
 Следующий пример изменяет предложение WHERE, созданное в примере В раздела [CREATE SERVER AUDIT (Transact-SQL)](../../t-sql/statements/create-server-audit-transact-sql.md). Новое предложение WHERE отбирает определяемые пользователем события с идентификатором 27.  
  
```sql  
ALTER SERVER AUDIT [FilterForSensitiveData] WITH (STATE = OFF)  
GO  
ALTER SERVER AUDIT [FilterForSensitiveData]  
WHERE user_defined_event_id = 27;  
GO  
ALTER SERVER AUDIT [FilterForSensitiveData] WITH (STATE = ON);  
GO  
```  
  
### <a name="d-removing-a-where-clause"></a>Г. Удаление предложения WHERE  
 Следующий пример удаляет выражение предиката предложения WHERE.  
  
```sql  
ALTER SERVER AUDIT [FilterForSensitiveData] WITH (STATE = OFF)  
GO  
ALTER SERVER AUDIT [FilterForSensitiveData]  
REMOVE WHERE;  
GO  
ALTER SERVER AUDIT [FilterForSensitiveData] WITH (STATE = ON);  
GO  
```  
  
### <a name="e-renaming-a-server-audit"></a>Д. Переименование аудита сервера  
 В данном примере показано изменение имени аудита сервера с `FilterForSensitiveData` на `AuditDataAccess`.  
  
```sql  
ALTER SERVER AUDIT [FilterForSensitiveData] WITH (STATE = OFF)  
GO  
ALTER SERVER AUDIT [FilterForSensitiveData]  
MODIFY NAME = AuditDataAccess;  
GO  
ALTER SERVER AUDIT [AuditDataAccess] WITH (STATE = ON);  
GO  
```  
  
## <a name="see-also"></a>См. также:  
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
 [Создание аудита сервера и спецификации аудита сервера](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
