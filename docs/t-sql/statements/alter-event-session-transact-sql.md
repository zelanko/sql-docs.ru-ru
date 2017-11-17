---
title: "ALTER EVENT SESSION (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/07/2017
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
- ALTER EVENT SESSION
- ALTER_EVENT_SESSION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- event sessions [SQL Server]
- extended events [SQL Server], Transact-SQL
- ALTER EVENT SESSION statement
ms.assetid: da006ac9-f914-4995-a2fb-25b5d971cd90
caps.latest.revision: 46
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b6fd062bf55bb2630c436d452d2bab05a2f2d53d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-event-session-transact-sql"></a>ALTER EVENT SESSION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Запускает или останавливает сеанс событий или изменяет конфигурацию сеанса.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ALTER EVENT SESSION event_session_name  
ON SERVER  
{  
    [ [ {  <add_drop_event> [ ,...n] }     
       | { <add_drop_event_target> [ ,...n ] } ]   
    [ WITH ( <event_session_options> [ ,...n ] ) ]  
    ]  
    | [ STATE = { START | STOP } ]  
}  
  
<add_drop_event>::=  
{  
    [ ADD EVENT <event_specifier>   
         [ ( {   
                 [ SET { event_customizable_attribute = <value> [ ,...n ] } ]  
                 [ ACTION ( { [event_module_guid].event_package_name.action_name [ ,...n ] } ) ]  
                 [ WHERE <predicate_expression> ]  
        } ) ]  
   ]   
   | DROP EVENT <event_specifier> }  
  
<event_specifier> ::=  
{  
[event_module_guid].event_package_name.event_name  
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
  
<add_drop_event_target>::=  
{  
    ADD TARGET <event_target_specifier>  
        [ ( SET { target_parameter_name = <value> [ ,...n] } ) ]  
    | DROP TARGET <event_target_specifier>  
}  
  
<event_target_specifier>::=  
{  
    [event_module_guid].event_package_name.target_name  
}  
  
<event_session_options>::=  
{  
    [    MAX_MEMORY = size [ KB | MB] ]  
    [ [,] EVENT_RETENTION_MODE = { ALLOW_SINGLE_EVENT_LOSS | ALLOW_MULTIPLE_EVENT_LOSS | NO_EVENT_LOSS } ]  
    [ [,] MAX_DISPATCH_LATENCY = { seconds SECONDS | INFINITE } ]  
    [ [,] MAX_EVENT_SIZE = size [ KB | MB ] ]  
    [ [,] MEMORY_PARTITION_MODE = { NONE | PER_NODE | PER_CPU } ]  
    [ [,] TRACK_CAUSALITY = { ON | OFF } ]  
    [ [,] STARTUP_STATE = { ON | OFF } ]  
}  
```  
  
## <a name="arguments"></a>Аргументы  
  
|||  
|-|-|  
|Термин|Определение|  
|*event_session_name*|Имя существующего сеанса событий.|  
|СОСТОЯНИЕ = НАЧАЛО &#124; ОСТАНОВИТЬ|Запускает или останавливает сеанс событий. Это аргумент действителен, только если к объекту сеанса событий применяется ALTER EVENT SESSION.|  
|Добавить СОБЫТИЕ \<event_specifier >|Связывает событие, обозначенное \<event_specifier > с сеансом событий.|
|[*event_module_guid*]*. event_package_name.event_name*|Имя события в пакете событий, где:<br /><br /> -   *event_module_guid* — это GUID для модуля, содержащего событие.<br />-   *event_package_name* — пакет, который содержит объект действия.<br />-   *имя_события* — объект события.<br /><br /> События отображаются в представлении sys.dm_xe_objects со значением object_type, равным «event».|  
|ЗНАЧЕНИЕ { *event_customizable_attribute*= \<значение > [,...*n*] }|Указывает настраиваемые атрибуты для события. Настраиваемые атрибуты отображаются в представлении sys.dm_xe_object_columns со значением column_type, равным «customizable» и object_name = *имя_события*.|  
|ДЕЙСТВИЕ ({[*event_module_guid*]*. event_package_name.action_name* [ **,**... *n*] } )|Действие, связанное с сеансом событий, где:<br /><br /> -   *event_module_guid* — это GUID для модуля, содержащего событие.<br />-   *event_package_name* — пакет, который содержит объект действия.<br />-   *имя_действия* — объект действия.<br /><br /> Действия отображаются в представлении sys.dm_xe_objects со значением object_type, равным «action».|  
|ГДЕ \<predicate_expression >|Задает выражение предиката, используемое, чтобы определить необходимость обработки события. Если \<predicate_expression > имеет значение true, то обработка события продолжается действиями и целями сеанса. Если \<predicate_expression > имеет значение false, то событие удаляется сеансом прежде, чем обрабатываются с действиями и целями сеанса. Выражения предиката ограничены 3000 символами, что является пределом для строковых аргументов.|
|*event_field_name*|Имя поля события, которое идентифицирует источник предиката.|  
|[event_module_guid].event_package_name.predicate_source_name|Имя глобального источника предиката, где:<br /><br /> -   *event_module_guid* — это GUID для модуля, содержащего событие.<br />-   *event_package_name* является пакет, содержащий объект предиката.<br />-   *predicate_source_name* определяется в представлении sys.dm_xe_objects как object_type 'pred_source'.|  
|[*event_module_guid*]. *event_package_name*. *predicate_compare_name*|Имя объекта предиката, связываемого с событием, где:<br /><br /> -   *event_module_guid* — это GUID для модуля, содержащего событие.<br />-   *event_package_name* является пакет, содержащий объект предиката.<br />-   *predicate_compare_name* — глобальный источник, определенный в представлении sys.dm_xe_objects как object_type 'pred_compare'.|  
|DROP EVENT \<event_specifier >|Удаляет событие, обозначенное  *\<event_specifier >*. \<event_specifier > должен быть допустимым в сеансе событий.|  
|Добавить ЦЕЛЬ \<event_target_specifier >|Связывает цель, обозначенную \<event_target_specifier > с сеансом событий.|
|[*event_module_guid*]. *event_package_name*. *target_name*|Имя цели в сеансе событий, где:<br /><br /> -   *event_module_guid* — это GUID для модуля, содержащего событие.<br />-   *event_package_name* — пакет, который содержит объект действия.<br />-   *target_name* действие. Действия отображаются в представлении sys.dm_xe_objects как object_type со значением «target».|  
|ЗНАЧЕНИЕ { *target_parameter_name*= \<значение > [,...*n*] }|Задает параметр цели. Целевые параметры отображаются в представлении sys.dm_xe_object_columns со значением column_type, равным «customizable» и object_name = *target_name*.<br /><br /> **ПРИМЕЧАНИЕ.** Если используется цель «Кольцевой буфер», рекомендуется установить параметр цели max_memory в значение 2048 килобайт (КБ), чтобы избежать возможного усечения выходных XML-данных. Дополнительные сведения об использовании разных типах целевых см. в разделе [SQL Server Extended Events Targets](http://msdn.microsoft.com/library/e281684c-40d1-4cf9-a0d4-7ea1ecffa384).|  
|ПЕРЕТАЩИТЕ ЦЕЛЕВОЙ \<event_target_specifier >|Удаляет цель, обозначенную \<event_target_specifier >. \<event_target_specifier > должен быть допустимым в сеансе событий.|  
|EVENT_RETENTION_MODE = { **ALLOW_SINGLE_EVENT_LOSS** &#124; ALLOW_MULTIPLE_EVENT_LOSS &#124; NO_EVENT_LOSS}|Задает режим хранения событий, используемый для обработки потери события.<br /><br /> **ALLOW_SINGLE_EVENT_LOSS.**<br /> Возможна потеря события в сеансе. Если все буферы событий полны, то удаляется только одно событие. Потеря одного события при заполнении буферов событий обеспечивает приемлемые характеристики производительности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], одновременно уменьшая до минимума потери данных в обработанном потоке событий.<br /><br /> ALLOW_MULTIPLE_EVENT_LOSS<br /> Из сеанса могут быть потеряны полные буферы событий, содержащие несколько событий. Число потерянных событий зависит от размера памяти, выделенной для сеанса, способа секционирования памяти и размера событий в буфере. Этот параметр уменьшает влияние быстрого заполнения буферов событий на производительность сервера, но возможна потеря большого числа событий в сеансе.<br /><br /> NO_EVENT_LOSS<br /> Потеря событий не разрешена. Этот параметр обеспечивает сохранение всех произошедших событий. При использовании этого параметра все задачи, которые инициируют события, должны ждать освобождения пространства в буфере событий. Это может привести к заметному снижению производительности во время активного сеанса событий. Соединения пользователя могут простаивать при ожидании событий, данные которых должны быть записаны на диск из буфера.|  
|MAX_DISPATCH_LATENCY = { *секунд* СЕКУНД &#124; **БЕСКОНЕЧНЫЙ** }|Задает промежуток времени, в течение которого события находятся в буферной памяти перед отправкой в цели сеанса событий. Минимальное значение задержки составляет 1 секунду. Чтобы задать неограниченную задержку (INFINITE), можно использовать значение 0. По умолчанию это значение равно 30 секундам.<br /><br /> *секунд* СЕКУНД<br /> Время ожидания (в секундах) перед началом выгрузки содержимого буферов в цели. *секунд* является целым числом.<br /><br /> **БЕСКОНЕЧНЫЙ**<br /> Запись на диск буферов в цели только при заполнении буферов или закрытии сеанса событий.<br /><br /> **ПРИМЕЧАНИЕ.** MAX_DISPATCH_LATENCY = 0 SECONDS эквивалентно MAX_DISPATCH_LATENCY = INFINITE.|  
|MAX_EVENT_SIZE =*размер* [КБ &#124; **МБ** ]|Задает максимальный допустимый размер для событий. MAX_EVENT_SIZE следует устанавливать только для того, чтобы разрешить одиночные события размером более MAX_MEMORY; задание значения, меньшего MAX_MEMORY, приведет к ошибке. *размер* является целым числом и может быть представлено значением в килобайтах (КБ) или значение мегабайт (МБ). Если *размер* указано в килобайтах, минимальный допустимый размер составляет 64 КБ. Если значение MAX_EVENT_SIZE два буфера *размер* дополнение к MAX_MEMORY создаются. Это значит, что общий объем памяти, используемой для буферизации событий, составляет MAX_MEMORY + 2 * MAX_EVENT_SIZE.|  
|MEMORY_PARTITION_MODE = { **NONE** &#124; PER_NODE &#124; PER_CPU;}|Задает место, в котором создаются буферы событий.<br /><br /> **NONE**<br /> В экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создается один набор буферов.<br /><br /> На каждом узле - набор буферов создается для каждого узла NUMA.<br /><br /> На один ЦП - набор буферов создается для каждого ЦП.|  
|TRACK_CAUSALITY = {ON &#124; **OFF** }|Указывает, будут ли отслеживаться причинно-следственные связи. Если отслеживание включено, то причинность позволяет коррелировать связанные события в различных серверных соединениях.|  
|STARTUP_STATE = {ON &#124; **OFF** }|Указывает, необходимо ли запустить данный сеанс событий автоматически при запуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Если STARTUP_STATE = ON, сеанс событий будет загружаться только в том случае, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] останавливается и затем перезапускается.<br /><br /> = Сеанс запускается при запуске события.<br /><br /> **ОТКЛЮЧЕНИЕ** = сеанс не запущен при запуске события.|  
  
## <a name="remarks"></a>Замечания  
 Аргументы ADD и DROP нельзя использовать в одной инструкции.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение ALTER ANY EVENT SESSION.  
  
## <a name="examples"></a>Примеры  
 Следующий пример запускает сеанс событий, получает динамическую статистику сеанса, а затем добавляет два события в существующий сеанс.  
  
```  
-- Start the event session  
ALTER EVENT SESSION test_session  
ON SERVER  
STATE = start;  
GO  
-- Obtain live session statistics   
SELECT * FROM sys.dm_xe_sessions;  
SELECT * FROM sys.dm_xe_session_events;  
GO  
  
-- Add new events to the session  
ALTER EVENT SESSION test_session ON SERVER  
ADD EVENT sqlserver.database_transaction_begin,  
ADD EVENT sqlserver.database_transaction_end;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE EVENT SESSION (Transact-SQL)](../../t-sql/statements/create-event-session-transact-sql.md)   
 [DROP EVENT SESSION (Transact-SQL)](../../t-sql/statements/drop-event-session-transact-sql.md)   
 [Цели расширенных событий SQL Server](http://msdn.microsoft.com/library/e281684c-40d1-4cf9-a0d4-7ea1ecffa384)   
 [sys.server_event_sessions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql.md)   
 [sys.dm_xe_objects &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql.md)   
 [sys.dm_xe_object_columns (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-xe-object-columns-transact-sql.md)  
  
  

