---
title: "ALTER SERVER AUDIT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6d2522a2876165f8e18222f2268dad091a6ba342
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-server-audit--transact-sql"></a>ALTER SERVER AUDIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Изменяет объект аудита сервера с помощью функции аудита [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в статье [Подсистема аудита SQL Server (компонент Database Engine)](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ALTER SERVER AUDIT audit_name  
{  
    [ TO { { FILE ( <file_options> [, ...n] ) } | APPLICATION_LOG | SECURITY_LOG } ]  
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
 TO { FILE | APPLICATION_LOG | SECURITY }  
 Определяет расположение целевого объекта аудита. Возможные режимы — двоичный файл, журнал событий приложений Windows или журнал безопасности Windows.  
  
 FILEPATH **= "***os_file_path***"**  
 Путь следа аудита. Имя файла формируется на основе имени аудита и его идентификатора GUID.  
  
 Параметр MAXSIZE  **=**  *max_size*  
 Задает максимальный размер, до которого может увеличиваться файл аудита. *Max_size* значение должно быть целое число, за которым следует **МБ**, **ГБ**, **ТБ**, или **неограниченное количество**. Минимальный размер, который можно указать для *max_size* 2 **МБ** , максимальное — 2 147 483 647 **ТБ**. Когда **неограниченное количество** указан, файл будет увеличиваться до заполнения диска. Указав значение менее 2 МБ вызывает ошибку MSG_MAXSIZE_TOO_SMALL. Значение по умолчанию — **неограниченное количество**.  
  
 MAX_ROLLOVER_FILES  **=**  *целое* | **без ограничений**  
 Задает максимальное число файлов, которые хранятся в файловой системе. Если установлено значение max_rollover_files = 0, отсутствует ограничение на количество файлов продолжения, которые создаются. Значение по умолчанию — 0. Максимальное число файлов, которое можно указать, составляет 2 147 483 647.  
  
 MAX_FILES =*целое число со знаком*  
 Задает максимальное число файлов аудита, которые могут быть созданы. Не наведите курсор на первый файл при достижении этого предела. При достижении предела MAX_FILES любое действие, которое вызывает дополнительных событий аудита для создаваемого завершается с ошибкой.  
**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ПАРАМЕТР RESERVE_DISK_SPACE  **=**  {ON | {OFF}  
 Этот параметр заранее размещает на диске файл в соответствии со значением MAXSIZE. Применяется, только если значение MAXSIZE не равно UNLIMITED. Значение по умолчанию — OFF.  
  
 QUEUE_DELAY  **=**  *целое число со знаком*  
 Определяет задержку в миллисекундах, после которой продолжается выполнение действий аудита. Значение 0 соответствует синхронной доставке. Минимальное значение задаваемой задержки запроса составляет 1000 (1 секунда), и это значение используется по умолчанию. Максимальное значение составляет 2 147 483 647 (2 147 483,647 секунд или 24 дня, 20 часов, 31 минута и 23,647 секунд). Если указано недопустимое значение, возникает ошибка MSG_INVALID_QUEUE_DELAY.  
  
 ON_FAILURE  **=**  {ПРОДОЛЖИТЬ | ЗАВЕРШЕНИЕ РАБОТЫ | FAIL_OPERATION}  
 Указывает, будет ли экземпляр, выполняющий запись в целевой объект, вызывать ошибку, продолжать работу или остановится, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может выполнить запись в журнал аудита.  
  
 CONTINUE  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работа продолжается. Записи аудита не сохраняются. Аудит продолжает попытки регистрации событий и возобновляется, если причина сбоя будет устранена. Выбрав вариант продолжения можно разрешить непроверенные действия, которые могут нарушать политики безопасности. Используйте этот параметр, когда продолжение операции компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] является более важным, чем сохранение полного аудита.  
  
SHUTDOWN  
Вызывает экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершить работу, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удалось записать данные в цель аудита по любой причине. Пользователь, который запустил `ALTER` оператора должен быть `SHUTDOWN` разрешения внутри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. С завершением работы сохраняется даже в том случае, если `SHUTDOWN` позже отменено разрешение от выполнения входа. Если пользователь имеет это разрешение, инструкция завершится ошибкой, и аудит не будет изменен. Используйте этот параметр, когда сбой аудита может нанести ущерб безопасности или целостности системы. Дополнительные сведения см. в разделе [завершение работы](../../t-sql/language-elements/shutdown-transact-sql.md). 
  
 FAIL_OPERATION  
 Действия с базой данных завершаются ошибкой, если они вызывают события аудита. Действия, которые не вызывают события аудита, можно продолжить, но могут быть отсутствуют события аудита. Аудит продолжает попытки регистрации событий и возобновляется, если причина сбоя будет устранена. Используйте этот параметр, если обеспечение полного аудита более важно, чем полный доступ к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].   
  
 СОСТОЯНИЕ  **=**  {ON | {OFF}  
 Включает или отключает аудит из сбора записей. При изменении состояния работающего аудита (из ON в OFF) создается запись аудита об остановке аудита, об остановившем аудит участнике и времени остановки аудита.  
  
 Параметр MODIFY NAME = *new_audit_name*  
 Изменяет имя аудита. Нельзя использовать совместно ни с каким другим параметром.  
  
 predicate_expression  
 Задает выражение предиката, используемое для определения необходимости обработки события. Выражения предиката ограничены 3000 символами, что является пределом для строковых аргументов.  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 event_field_name  
 Имя поля события, которое идентифицирует источник предиката. Поля аудита описаны в [sys.fn_get_audit_file &#40; Transact-SQL &#41; ](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md). Аудиту могут быть подвержены все поля, за исключением `file_name` и `audit_file_offset`.  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 number  
 — Включая любого числового типа **десятичное**. Ограничения: недостаток доступной физической памяти или слишком большое число, которое невозможно представить 64-разрядным целым.  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ' string '  
 Для предикатного сравнения требуется строка в Юникоде или ANSI. Для функций предикатного сравнения не выполняется неявное преобразование строкового типа. Передача неверного типа приводит к ошибке.  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="remarks"></a>Замечания  
 В вызове ALTER AUDIT надо указывать хотя бы одно предложение из TO, WITH и MODIFY NAME.  
  
 Чтобы внести изменения в аудит, для состояния аудита необходимо установить параметр OFF. Если ALTER AUDIT выполняется, когда аудит включен с любыми параметрами, отличными от STATE = OFF, появляется сообщение об ошибке MSG_NEED_AUDIT_DISABLED.  
  
 Можно добавлять, изменять или удалять спецификации аудита без остановки аудита.  
  
 После создания аудита нельзя изменить его идентификатор GUID.  
  
## <a name="permissions"></a>Permissions  
 Чтобы создать, изменить или удалить участника на уровне сервера требуется разрешение ALTER ANY SERVER AUDIT или CONTROL SERVER.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-changing-a-server-audit-name"></a>A. Изменение имени аудита сервера  
 В данном примере показано изменение имени аудита базы данных с `HIPPA_Audit` на `HIPAA_Audit_Old`.  
  
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
 В следующем примере аудит сервера с именем `HIPPA_Audit` изменяется на целевой файл.  
  
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
 В следующем примере изменяется where предложения, созданная в примере из [CREATE SERVER AUDIT &#40; Transact-SQL &#41; ](../../t-sql/statements/create-server-audit-transact-sql.md). Новое предложение WHERE фильтрует события определяемой пользователем идентификатором 27.  
  
```tsql  
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
  
```tsql  
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
  
```tsql  
ALTER SERVER AUDIT [FilterForSensitiveData] WITH (STATE = OFF)  
GO  
ALTER SERVER AUDIT [FilterForSensitiveData]  
MODIFY NAME = AuditDataAccess;  
GO  
ALTER SERVER AUDIT [AuditDataAccess] WITH (STATE = ON);  
GO  
```  
  
## <a name="see-also"></a>См. также:  
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
 [Создание аудита сервера и спецификации аудита сервера](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  

