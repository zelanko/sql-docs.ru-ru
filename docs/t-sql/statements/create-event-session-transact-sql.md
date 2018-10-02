---
title: CREATE EVENT SESSION (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CREATE EVENT SESSION
- SESSION
- EVENT SESSION
- SESSION_TSQL
- EVENT_SESSION_TSQL
- CREATE_EVENT_SESSION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- event sessions [SQL Server]
- CREATE EVENT SESSION statement
ms.assetid: 67683027-2b0f-47aa-b223-604731af8b4d
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: c143f1abe85594cc399f19ed9d845c6c01573396
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47769022"
---
# <a name="create-event-session-transact-sql"></a>CREATE EVENT SESSION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Создает сеанс расширенных событий, который идентифицирует источник событий, цели и параметры сеанса событий.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CREATE EVENT SESSION event_session_name  
ON SERVER  
{  
    <event_definition> [ ,...n]  
    [ <event_target_definition> [ ,...n] ]  
    [ WITH ( <event_session_options> [ ,...n] ) ]  
}  
;  
  
<event_definition>::=  
{  
    ADD EVENT [event_module_guid].event_package_name.event_name   
         [ ( {   
                 [ SET { event_customizable_attribute = <value> [ ,...n] } ]  
                 [ ACTION ( { [event_module_guid].event_package_name.action_name [ ,...n] } ) ]  
                 [ WHERE <predicate_expression> ]  
        } ) ]  
}  
  
<predicate_expression> ::=   
{  
    [ NOT ] <predicate_factor> | {( <predicate_expression> ) }   
    [ { AND | OR } [ NOT ] { <predicate_factor> | ( <predicate_expression> ) } ]   
    [ ,...n ]  
}  
  
<predicate_factor>::=   
{  
    <predicate_leaf> | ( <predicate_expression> )  
}  
  
<predicate_leaf>::=  
{  
      <predicate_source_declaration> { = | < > | ! = | > | > = | < | < = } <value>   
    | [event_module_guid].event_package_name.predicate_compare_name ( <predicate_source_declaration>, <value> )   
}  
  
<predicate_source_declaration>::=   
{  
    event_field_name | ( [event_module_guid].event_package_name.predicate_source_name )  
}  
  
<value>::=   
{  
    number | 'string'  
}  
  
<event_target_definition>::=  
{  
    ADD TARGET [event_module_guid].event_package_name.target_name  
        [ ( SET { target_parameter_name = <value> [ ,...n] } ) ]  
}  
  
<event_session_options>::=  
{  
    [    MAX_MEMORY = size [ KB | MB ] ]  
    [ [,] EVENT_RETENTION_MODE = { ALLOW_SINGLE_EVENT_LOSS | ALLOW_MULTIPLE_EVENT_LOSS | NO_EVENT_LOSS } ]  
    [ [,] MAX_DISPATCH_LATENCY = { seconds SECONDS | INFINITE } ]  
    [ [,] MAX_EVENT_SIZE = size [ KB | MB ] ]  
    [ [,] MEMORY_PARTITION_MODE = { NONE | PER_NODE | PER_CPU } ]  
    [ [,] TRACK_CAUSALITY = { ON | OFF } ]  
    [ [,] STARTUP_STATE = { ON | OFF } ]  
}  
```  
  
## <a name="arguments"></a>Аргументы  
 *event_session_name*  
 Определяемое пользователем имя для сеанса событий. Аргумент *event_session_name* является алфавитно-цифровым и может содержать до 128 символов. Данный аргумент должен быть уникальным в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и соответствовать правилам для [идентификаторов](../../relational-databases/databases/database-identifiers.md).  
  
 ADD EVENT [ *event_module_guid* ].*event_package_name*.*event_name*  
 Событие, связываемое с сеансом событий, где:  
  
-   *event_module_guid* — идентификатор GUID для модуля, содержащего событие;  
  
-   *event_package_name* — пакет, который содержит объект действия;  
  
-   *event_name* — объект события.  
  
 События отображаются в представлении sys.dm_xe_objects со значением object_type, равным "event".  
  
 SET { *event_customizable_attribute*= \<value> [ ,...*n*] }  
 Позволяет установить настраиваемые атрибуты для события. Настраиваемые атрибуты отображаются в представлении sys.dm_xe_object_columns со значением column_type, равным "customizable", и object_name = *event_name*.  
  
 ACTION ( { [*event_module_guid*].*event_package_name*.*action_name* [ **,**...*n*] })  
 Действие, связанное с сеансом событий, где:  
  
-   *event_module_guid* — идентификатор GUID для модуля, содержащего событие;  
  
-   *event_package_name* — пакет, который содержит объект действия;  
  
-   *action_name* — объект действия.  
  
 Действия отображаются в представлении sys.dm_xe_objects со значением object_type, равным "action".  
  
 WHERE \<predicate_expression> задает выражение предиката, используемое для определения необходимости обработки события. Если \<predicate_expression> имеет значение true, то обработка события продолжается действиями и целями сеанса. Если \<predicate_expression> имеет значение false, то событие удаляется сеансом прежде, чем оно будет обработано действиями и целями для сеанса. Выражения предиката ограничены 3000 символами, что является пределом для строковых аргументов. 
  
 *event_field_name*  
 Имя поля события, которое идентифицирует источник предиката.  
  
 [*event_module_guid*].*event_package_name*.*predicate_source_name*  
 Имя глобального источника предиката, где:  
  
-   *event_module_guid* — идентификатор GUID для модуля, содержащего событие;  
  
-   *event_package_name* — пакет, который содержит объект предиката;  
  
-   *predicate_source_name* определен в представлении sys.dm_xe_objects как object_type со значением "pred_source".  
  
 [*event_module_guid*].*event_package_name*.*predicate_compare_name*  
 Имя объекта предиката, связываемого с событием, где:  
  
-   *event_module_guid* — идентификатор GUID для модуля, содержащего событие;  
  
-   *event_package_name* — пакет, который содержит объект предиката;  
  
-   *predicate_compare_name* — глобальный источник, определенный в представлении sys.dm_xe_objects со значением object_type, равным "pred_compare".  
  
 *number*  
 Любой числовой тип, включая **decimal**. Ограничения: недостаток доступной физической памяти или слишком большое число, которое невозможно представить 64-разрядным целым.  
  
 '*string*'  
 Для предикатного сравнения требуется строка в Юникоде или ANSI. Для функций предикатного сравнения не выполняется неявное преобразование строкового типа. Передача неверного типа приводит к ошибке.  
  
 ADD TARGET [*event_module_guid*].*event_package_name*.*target_name*  
 Цель, связываемая с сеансом событий, где:  
  
-   *event_module_guid* — идентификатор GUID для модуля, содержащего событие;  
  
-   *event_package_name* — пакет, который содержит объект действия;  
  
-   *target_name* представляет собой целевой объект. Целевые объекты отображаются в представлении sys.dm_xe_objects со значением object_type, равным «target».  
  
 SET { *target_parameter_name*= \<value> [, ...*n*] }  
 Задает параметр целевого объекта. Параметры цели отображаются в представлении sys.dm_xe_object_columns со значением column_type, равным "customizable", и object_name = *target_name*.  
  
> [!IMPORTANT]  
>  Если используется цель "Кольцевой буфер", рекомендуется установить параметр цели max_memory в значение 2048 килобайт (КБ), чтобы избежать возможного усечения выходных XML-данных. Дополнительные сведения об использовании разных типов целевых объектов см. в статье [Цели расширенных событий SQL Server](http://msdn.microsoft.com/library/e281684c-40d1-4cf9-a0d4-7ea1ecffa384).  
  
 WITH ( \<event_session_options> [ ,...*n*] ) Задает параметры, используемые с сеансом событий.  
  
 MAX_MEMORY =*size* [ KB | **MB** ]  
 Задает максимальный объем памяти, выделенной в сеансе для буферов событий. Значение по умолчанию — 4 МБ. *size* — целое значение, которое может быть представлено значением в килобайтах (КБ) или мегабайтах (МБ).  
  
 EVENT_RETENTION_MODE = { **ALLOW_SINGLE_EVENT_LOSS** | ALLOW_MULTIPLE_EVENT_LOSS | NO_EVENT_LOSS }  
 Задает режим хранения событий, используемый для обработки потери события.  
  
 **ALLOW_SINGLE_EVENT_LOSS**  
 Возможна потеря события в сеансе. Если все буферы событий полны, то удаляется только одно событие. Потеря одного события при заполнении буферов событий обеспечивает приемлемые характеристики производительности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], одновременно уменьшая до минимума потери данных в обработанном потоке событий.  
  
 ALLOW_MULTIPLE_EVENT_LOSS  
 Из сеанса могут быть потеряны полные буферы событий, содержащие несколько событий. Число потерянных событий зависит от размера памяти, выделенной для сеанса, способа секционирования памяти и размера событий в буфере. Этот параметр уменьшает влияние быстрого заполнения буферов событий на производительность сервера, но возможна потеря большого числа событий в сеансе.  
  
 NO_EVENT_LOSS  
 Потеря событий не разрешена. Этот параметр обеспечивает сохранение всех произошедших событий. При использовании этого параметра все задачи, которые инициируют события, должны ждать освобождения пространства в буфере событий. Это может привести к заметному снижению производительности во время активного сеанса событий. Соединения пользователя могут простаивать при ожидании событий, данные которых должны быть записаны на диск из буфера.  
  
 MAX_DISPATCH_LATENCY = { *seconds* SECONDS | **INFINITE** }  
 Задает промежуток времени, в течение которого события будут находиться в буферной памяти перед отправкой в цели сеанса событий. По умолчанию это значение равно 30 секундам.  
  
 *seconds* SECONDS  
 Время ожидания (в секундах) перед началом выгрузки содержимого буферов в цели. *seconds* является целым числом. Минимальное значение задержки составляет 1 секунду. Чтобы задать неограниченную задержку (INFINITE), можно использовать значение 0.  
  
 **INFINITE**  
 Запись на диск буферов в цели только при заполнении буферов или закрытии сеанса событий.  
  
> [!NOTE]  
>  MAX_DISPATCH_LATENCY = 0 SECONDS эквивалентно MAX_DISPATCH_LATENCY = INFINITE.  
  
 MAX_EVENT_SIZE =*size* [ KB | **MB** ]  
 Задает максимальный допустимый размер для событий. MAX_EVENT_SIZE следует устанавливать только для того, чтобы разрешить одиночные события размером более MAX_MEMORY; задание значения, меньшего MAX_MEMORY, приведет к ошибке. *size* — целое значение, которое может быть представлено значением в килобайтах (КБ) или мегабайтах (МБ). Если значение *size* указано в килобайтах, то минимально допустимое значение — 64 KБ. Если задано значение MAX_EVENT_SIZE, то в дополнение к MAX_MEMORY создаются два буфера размером *size*. Это значит, что общий объем памяти, используемой для буферизации событий, составляет MAX_MEMORY + 2 * MAX_EVENT_SIZE.  
  
 MEMORY_PARTITION_MODE = { **NONE** | PER_NODE | PER_CPU }  
 Задает место, в котором создаются буферы событий.  
  
 **NONE**  
 В экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создается один набор буферов.  
  
 PER_NODE  
 Набор буферов создается для каждого узла NUMA.  
  
 PER_CPU  
 Набор буферов создается для каждого ЦП.  
  
 TRACK_CAUSALITY = { ON | **OFF** }  
 Указывает, будут ли отслеживаться причинно-следственные связи. Если отслеживание включено, то причинность позволяет коррелировать связанные события в различных серверных соединениях.  
  
 STARTUP_STATE = { ON | **OFF** }  
 Указывает, необходимо ли запустить данный сеанс событий автоматически при запуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Если STARTUP_STATE = ON, то сеанс событий будет запущен, только если SQL Server остановлен, а затем перезапущен.  
  
 ON  
 Сеанс событий запускается при начальном запуске.  
  
 **OFF**  
 Сеанс событий не запускается при начальном запуске.  
  
## <a name="remarks"></a>Remarks  
 Приоритеты выполнения логических операторов распределяются следующим образом: NOT (наивысший приоритет), AND, OR (низший приоритет).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER ANY EVENT SESSION.  
  
## <a name="examples"></a>Примеры  
 В следующем примере демонстрируется, как создать сеанс событий с именем `test_session`. В этом примере добавляются два события, а также используется цель средства отслеживания событий для Windows.  
  
```  
IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='test_session')  
    DROP EVENT session test_session ON SERVER;  
GO  
CREATE EVENT SESSION test_session  
ON SERVER  
    ADD EVENT sqlos.async_io_requested,  
    ADD EVENT sqlserver.lock_acquired  
    ADD TARGET package0.etw_classic_sync_target   
        (SET default_etw_session_logfile_path = N'C:\demo\traces\sqletw.etl' )  
    WITH (MAX_MEMORY=4MB, MAX_EVENT_SIZE=4MB);  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER EVENT SESSION (Transact-SQL)](../../t-sql/statements/alter-event-session-transact-sql.md)   
 [DROP EVENT SESSION (Transact-SQL)](../../t-sql/statements/drop-event-session-transact-sql.md)   
 [sys.server_event_sessions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql.md)   
 [sys.dm_xe_objects (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql.md)   
 [sys.dm_xe_object_columns (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-xe-object-columns-transact-sql.md)  
  
  

