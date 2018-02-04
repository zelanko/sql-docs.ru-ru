---
title: "sys.fn_get_audit_file (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- fn_get_audit_file_TSQL
- sys.fn_get_audit_file_TSQL
- fn_get_audit_file
- sys.fn_get_audit_file
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_get_audit_file function
- fn_get_audit_file function
ms.assetid: d6a78d14-bb1f-4987-b7b6-579ddd4167f5
caps.latest.revision: 
author: BYHAM
ms.author: rickbyh
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: efaffab66cba6d95d76d7c5371e43db1aca9f744
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysfngetauditfile-transact-sql"></a>sys.fn_get_audit_file (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает сведения из файла аудита, созданного аудитом сервера в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в статье [Подсистема аудита SQL Server (компонент Database Engine)](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
fn_get_audit_file ( file_pattern,   
    { default | initial_file_name | NULL },   
    { default | audit_record_offset | NULL } )  
```  
  
## <a name="arguments"></a>Аргументы  
 *file_pattern*  
 Указывает каталог или путь и имя файла для файла аудита, который предстоит прочитать. Тип — **nvarchar(260)**. 
 
 - **SQL Server**:
    
    Этот аргумент должен содержать как путь (букву диска или сетевой ресурс), так и имя файла, которое может включать символ-шаблон. Одна звездочка (*) используется для выбора нескольких файлов из набора файлов аудита. Например:  
  
    -   **\<путь >\\ \***  - собрать все файлы в указанном расположении аудита.  
  
    -   **\<путь > \LoginsAudit_{GUID}** - собрать все файлы, которые имеют указанное имя и идентификатор GUID аудита.  
  
    -   **\<путь > \LoginsAudit_{GUID}_00_29384.sqlaudit** -сбора аудита для конкретного файла.  
  
 - **База данных Azure SQL**:
 
    Этот аргумент используется для указания URL-адрес большого двоичного объекта (включая конечную точку хранения и контейнера). Пока он не поддерживает шаблон «звездочка», можно использовать для выбора нескольких файлов (BLOB), которые начинаются с этого префикса префикс имени файла частичного (blob) (а не имя полного большого двоичного объекта). Например:
 
      - **\<Storage_endpoint\>/\<контейнера\>/\<ServerName\>/\<DatabaseName\> /**  -собирает все файлы аудита (BLOB) для конкретной базы данных.    
      
      - **\<Storage_endpoint\>/\<контейнера\>/\<ServerName\>/\<DatabaseName\> / \<AuditName\>/\<CreationDate\>/\<FileName\>.xel** -файл конкретного аудита (blob).
  
> [!NOTE]  
>  При передаче пути без имени файла сформируется ошибка.  
  
 *initial_file_name*  
 Указывает путь и имя файла для определенного файла в наборе файлов аудита, из которого предстоит начать чтение записей аудита. Тип — **nvarchar(260)**.  
  
> [!NOTE]  
>  *Initial_file_name* аргумент должен содержать допустимые записи или должен содержать либо значение по умолчанию | Значение NULL.  
  
 *audit_record_offset*  
 Указывает известное местоположение с файлом, указанным для initial_file_name. Когда используется этот аргумент, функция начнет чтение с первой записи буфера, следующей немедленно после указанного смещения.  
  
> [!NOTE]  
>  *Audit_record_offset* аргумент должен содержать допустимые записи или должен содержать либо значение по умолчанию | Значение NULL. Тип — **bigint**.  
  
## <a name="tables-returned"></a>Возвращаемые таблицы  
 В следующей таблице описано содержимое файла аудита, которое может возвращаться этой функцией.  
  
|Имя столбца|Тип|Описание|  
|-----------------|----------|-----------------|  
|event_time|**datetime2**|Дата и время срабатывания действия, доступного для аудита. Не допускает значение NULL.|  
|sequence_number|**int**|Отслеживает последовательность записей в одной записи аудита, слишком большой, чтобы уместиться в буфере записи для аудитов. Не допускает значение NULL.|  
|action_id|**varchar(4)**|Идентификатор действия. Не допускает значение NULL.|  
|succeeded|**бит**|Показывает, было ли успешным действие, запустившее событие. Не допускает значение NULL. Для всех событий, отличных от событий имени входа, при этом формируются только сообщения о том, была ли проверка разрешения выполнена успешно или окончилась неудачей, а не сообщения о самой операции.<br /> 1 = успешное завершение;<br /> 0 = неуспешное завершение.|  
|permission_bitmask|**varbinary(16)**|В некоторых действиях это предоставленные, запрещенные или отмененные разрешения.|  
|is_column_permission|**бит**|Флаг, обозначающий разрешение уровня столбца. Не допускает значение NULL. Возвращает 0, если permission_bitmask = 0.<br /> 1 = true;<br /> 0 = false.|  
|session_id|**smallint**|Идентификатор сеанса, в котором произошло событие. Не допускает значение NULL.|  
|server_principal_id|**int**|Идентификатор контекста имени входа, в котором выполнено действие. Не допускает значение NULL.|  
|database_principal_id|**int**|Идентификатор контекста пользователя базы данных, в котором выполнено действие. Не допускает значение NULL. Поддерживает 0, если это неприменимо. Например, операция сервера.|  
|target_server_principal_id|**int**|Участник на уровне сервера, над которым выполняется операция GRANT/DENY/REVOKE. Не допускает значение NULL. Если неприменимо, возвращается значение 0.|  
|target_database_principal_id|**int**|Участник базы данных, над которым выполняется операция GRANT/DENY/REVOKE. Не допускает значение NULL. Если неприменимо, возвращается значение 0.|  
|object_id|**int**|Идентификатор сущности, над которой выполнен аудит. Это включает следующие действия.<br /> Объекты сервера.<br /> Базы данных<br /> Объекты базы данных<br /> Объекты схемы.<br /> Не допускает значение NULL. Возвращает 0, если сущностью является сам сервер или если аудит не выполняется на уровне объекта. Например, проверка подлинности.|  
|class_type|**varchar(2)**|Тип доступной для аудита сущности, для которой проводится аудит. Не допускает значение NULL.|  
|session_server_principal_name|**sysname**|Участник на уровне сервера для сеанса. Допускает значение NULL.|  
|server_principal_name|**sysname**|Текущее имя входа. Допускает значение NULL.|  
|server_principal_sid|**varbinary**|Идентификатор безопасности текущего имени входа. Допускает значение NULL.|  
|database_principal_name|**sysname**|Текущий пользователь. Допускает значение NULL. Возвращает значение NULL, если недоступно.|  
|target_server_principal_name|**sysname**|Целевое имя входа действия. Допускает значение NULL. Если неприменимо, возвращается значение NULL.|  
|target_server_principal_sid|**varbinary**|Идентификатор безопасности целевого имени входа. Допускает значение NULL. Если неприменимо, возвращается значение NULL.|  
|target_database_principal_name|**sysname**|Целевой пользователь действия. Допускает значение NULL. Если неприменимо, возвращается значение NULL.|  
|server_instance_name|**sysname**|Имя экземпляра сервера, где проводился аудит. Используется стандартный формат «сервер\экземпляр».|  
|database_name|**sysname**|Контекст базы данных, в котором выполнялось действие. Допускает значение NULL. Возвращает значение NULL для аудитов, выполняемых на уровне сервера.|  
|schema_name|**sysname**|Контекст схемы, в котором выполнялось действие. Допускает значение NULL. Возвращает значение NULL для аудитов, выполняемых вне схемы.|  
|object_name|**sysname**|Имя сущности, для которой проводился аудит. Это включает следующие действия.<br /> Объекты сервера.<br /> Базы данных<br /> Объекты базы данных<br /> Объекты схемы.<br /> Допускает значение NULL. Возвращает NULL, если сущностью является сам сервер или если аудит не выполняется на уровне объекта. Например, проверка подлинности.|  
|инструкция|**nvarchar(4000)**|Инструкция TSQL (если существует). Допускает значение NULL. Если неприменимо, возвращается значение NULL.|  
|additional_information|**nvarchar(4000)**|Уникальные сведения, применимые только к одиночному событию, возвращаются в формате XML. Немногие действия, доступные для аудита, содержат сведения этого вида.<br /><br /> Для действий, имеющих связанный с ними стек TSQL, отображается один уровень стека TSQL в формате XML. Используется следующий формат XML:<br /><br /> `<tsql_stack><frame nest_level = '%u' database_name = '%.*s' schema_name = '%.*s' object_name = '%.*s' /></tsql_stack>`<br /><br /> Параметр «frame nest_level» указывает текущий уровень вложенности кадра. Имя модуля состоит из трех частей (имя базы данных database_name, имя схемы schema_name и имя объекта object_name).  Имя модуля выполняется анализ escape-символы, такие как недопустимый XML-код `'\<'`, `'>'`, `'/'`, `'_x'`. Они будут экранируются как `_xHHHH\_`. Здесь HHHH обозначает четырехразрядный шестнадцатеричный код символа в UCS-2.<br /><br /> Допускает значение NULL. Возвращает NULL, если событие не сообщает дополнительных сведений.|  
|file_name|**varchar(260)**|Путь и имя файла журнала аудита, из которого получена запись. Не допускает значение NULL.|  
|audit_file_offset|**bigint**|Смещение буфера в файле, который содержит запись аудита. Не допускает значение NULL.|  
|user_defined_event_id|**smallint**|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Определенный пользователем идентификатор события передается в качестве аргумента для **sp_audit_write**. **Значение NULL** системные события (по умолчанию) и ненулевое значение для определяемых пользователем событий. Дополнительные сведения см. в разделе [sp_audit_write &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-audit-write-transact-sql.md).|  
|user_defined_information|**nvarchar(4000)**|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Используется для записи любой дополнительной информации, которую пользователь хочет записи в |журнал аудита с помощью **sp_audit_write** хранимой процедуры.|  
|audit_schema_version |**int** | |  
|sequence_group_id |**varbinary** | Только SQL Server (начиная с 2016) |  
|transaction_id |**bigint** | Только SQL Server (начиная с 2016) |  
|client_ip |**nvarchar(128)** | Azure баз данных SQL Server и экземпляр SQL Server (начиная с 2017 г.) |  
|application_name |**nvarchar(128)** | Azure баз данных SQL Server и экземпляр SQL Server (начиная с 2017 г.) |  
|duration_milliseconds |**bigint** | Только базы данных Azure SQL |  
|response_rows |**bigint** | Только базы данных Azure SQL |  
|affected_rows |**bigint** | Только базы данных Azure SQL |  
  
## <a name="remarks"></a>Remarks  
 Если *file_pattern* аргумент, передаваемый **fn_get_audit_file** ссылается на путь или файл, который не существует, или если файл не является файлом аудита **MSG_INVALID_AUDIT_FILE**возвращается сообщение об ошибке.  
  
## <a name="permissions"></a>Разрешения  
 - **SQL Server**: требуется **CONTROL SERVER** разрешение.  
 - **База данных SQL Azure**: требуется **базы данных системы УПРАВЛЕНИЯ** разрешение.     
    - Администраторы серверов могут обращаться к журналам аудита всех баз данных на сервере.
    - Администраторы серверов не имеет доступ только к журналы аудита из текущей базы данных.
    - Большие двоичные объекты, которые не соответствуют приведенным выше критериям будут пропущены (список пропущенных больших двоичных объектов будет отображаться в выходном сообщении запроса), и функция возвращает журналы только из больших двоичных объектов, для которых разрешен доступ.  
  
## <a name="examples"></a>Примеры

- **SQL Server**

  В следующем примере выполняется чтение из файла, который имеет имя `\\serverName\Audit\HIPPA_AUDIT.sqlaudit`.  
  
  ```  
  SELECT * FROM sys.fn_get_audit_file ('\\serverName\Audit\HIPPA_AUDIT.sqlaudit',default,default);  
  GO  
  ```  

- **База данных SQL Azure**

  Этот пример считывает из файла с именем `ShiraServer/MayaDB/SqlDbAuditing_Audit/2017-07-14/10_45_22_173_1.xel`:  
  
  ```  
  SELECT * FROM sys.fn_get_audit_file ('https://mystorage.blob.core.windows.net/sqldbauditlogs/ShiraServer/MayaDB/SqlDbAuditing_Audit/2017-07-14/10_45_22_173_1.xel',default,default);
  GO  
  ```  

  Этот пример считывает из одного файла, как описано выше, но с предложениями дополнительных T-SQL (**ВЕРХНЕЙ**, **ORDER BY**, и **ГДЕ** предложение для фильтрации возвращенных записей аудита функция):
  
  ```  
  SELECT TOP 10 * FROM sys.fn_get_audit_file ('https://mystorage.blob.core.windows.net/sqldbauditlogs/ShiraServer/MayaDB/SqlDbAuditing_Audit/2017-07-14/10_45_22_173_1.xel',default,default)
  WHERE server_principal_name = 'admin1'
  ORDER BY event_time
  GO
  ```  

  Этот пример считывает все журналы с серверов, которые начинаются с аудита `Sh`: 
  
  ```  
  SELECT * FROM sys.fn_get_audit_file ('https://mystorage.blob.core.windows.net/sqldbauditlogs/Sh',default,default);
  GO  
  ```

Полный пример о способах создания аудита см. в разделе [аудита SQL Server &#40; компонент Database Engine &#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).

Сведения о настройке аудита базы данных SQL Azure см. в разделе [начало работы с аудитом базы данных SQL](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-auditing).
  
## <a name="see-also"></a>См. также  
 [Создание АУДИТА сервера &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [Создание СПЕЦИФИКАЦИИ АУДИТА сервера &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [СОЗДАТЬ СПЕЦИФИКАЦИЮ АУДИТА базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [УДАЛИТЬ СПЕЦИФИКАЦИЮ АУДИТА базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.server_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys.server_file_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.server_audit_specification_details &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys.database_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_actions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [sys.dm_audit_class_type_map &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Создание аудита сервера и спецификации аудита сервера](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
