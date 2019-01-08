---
title: sys.event_log (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- event_log
- sys.event_log_TSQL
- event_log_TSQL
- sys.event_log
dev_langs:
- TSQL
helpviewer_keywords:
- event_log
- sys.event_log
ms.assetid: ad5496b5-e5c7-4a18-b5a0-3f985d7c4758
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: c4a21f9ccbf1dd8bcb7918c67b98aa51a0956d41
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2018
ms.locfileid: "53590958"
---
# <a name="syseventlog-azure-sql-database"></a>sys.event_log (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Возвращает успешные [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] подключений, сбоев подключения и взаимоблокировки базы данных. С помощью этих данных можно отслеживать и устранять неполадки операций с базой данных, используя [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
> [!CAUTION]  
>  Для установок с большим числом баз данных или слишком большого числа имен входа действие в sys.event_log можно вызвать ограничения производительности, высокой загрузки ЦП и привести к ошибкам входа. Запросы к sys.event_log может усугубить проблему. Корпорация Microsoft помогает решить эту проблему. В то же время чтобы снизить влияние этой проблемы, можно ограничьте запросы из sys.event_log. Пользователи NewRelic SQL Server подключаемого модуля необходимо посетить [настройки помощник по настройке & производительности подключаемого модуля базы данных SQL Microsoft Azure](https://discuss.newrelic.com/t/microsoft-azure-sql-database-plugin-tuning-performance-tweaks/30729) Дополнительные сведения о конфигурации.  
  
 Представление `sys.event_log` содержит следующие столбцы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_name**|**sysname**|Имя базы данных. Если подключение завершилось ошибкой и пользователь не указал имя базы данных, то этот столбец остается пустым.|  
|**start_time**|**datetime2**|Дата и время начала интервала статистической обработки в формате UTC. Для статистических событий время всегда кратно 5 минутам. Пример:<br /><br /> '2011-09-28 16:00:00'<br />'2011-09-28 16:05:00'<br />'2011-09-28 16:10:00'|  
|**end_time**|**datetime2**|Дата и время окончания интервала статистической обработки в формате UTC. Для статистических событий **End_time** — всегда на 5 минут больше, чем соответствующие **start_time** в той же строке. Для событий, которые не объединяются **start_time** и **end_time** равны фактические даты в формате UTC и время события.|  
|**event_category**|**Nvarchar(64)**|Высокоуровневый компонент, вызвавший данное событие.<br /><br /> См. в разделе [типы событий](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes) список возможных значений.|  
|**event_type**|**Nvarchar(64)**|Тип события.<br /><br /> См. в разделе [типы событий](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes) список возможных значений.|  
|**event_subtype**|**int**|Подтип произошедшего события.<br /><br /> См. в разделе [типы событий](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes) список возможных значений.|  
|**event_subtype_desc**|**Nvarchar(64)**|Описание подтипа события.<br /><br /> См. в разделе [типы событий](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes) список возможных значений.|  
|**severity**|**int**|Степень серьезности ошибки. Возможны следующие значения:<br /><br /> 0 = информационные<br />1 = предупреждение<br />2 = ошибка|  
|**event_count**|**int**|Количество раз возникновения этого события для указанной базы данных в интервале времени, указанном (**start_time** и **end_time**).|  
|**Описание**|**nvarchar(max)**|Подробное описание события.<br /><br /> См. в разделе [типы событий](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes) список возможных значений.|  
|**additional_data**|**XML**|*Примечание. Это значение всегда равно NULL для базы данных SQL Azure версии 12. См. в разделе [примеры](#Deadlock) раздел по получению события взаимоблокировки для версии 12.*<br /><br /> Для **взаимоблокировки** события, этот столбец содержит диаграмму взаимоблокировок. Этот столбец содержит значение NULL для других типов событий. |  
  
##  <a name="EventTypes"></a> Типы событий  
 События, записанные каждой строкой в этом представлении, определяются по категориям (**event_category**), тип события (**event_type**) и подтипу (**event_subtype**). В следующей таблице перечислены типы событий, собираемых в этом представлении.  
  
 Для событий в **подключения** категория, сводная информация доступна в представлении sys.database_connection_stats.  
  
> [!NOTE]  
>  Это представление включает не все возможные события базы данных [!INCLUDE[ssSDS](../../includes/sssds-md.md)], которые могут возникнуть, а только события перечисленные ниже. Дополнительные категории, типы событий и подтипы могут быть добавлены в будущих версиях [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
|**event_category**|**event_type**|**event_subtype**|**event_subtype_desc**|**severity**|**Описание**|  
|-------------------------|---------------------|------------------------|------------------------------|------------------|---------------------|  
|**подключение**|**connection_successful**|0|**connection_successful**|0|Успешное подключение к базе данных.|  
|**подключение**|**connection_failed**|0|**invalid_login_name**|2|Имя входа не является допустимым именем входа в данной версии SQL Server.|  
|**подключение**|**connection_failed**|1|**windows_auth_not_supported**|2|Имена входа Windows не поддерживаются в данной версии SQL Server.|  
|**подключение**|**connection_failed**|2|**attach_db_not_supported**|2|Пользователь запросил присоединение файла базы данных, который не поддерживается.|  
|**подключение**|**connection_failed**|3|**change_password_not_supported**|2|Пользователь запросил изменение пароля пользователя, входящего в систему, который не поддерживается.|  
|**подключение**|**connection_failed**|4|**login_failed_for_user**|2|Ошибка входа пользователя.|  
|**подключение**|**connection_failed**|5|**login_disabled**|2|Имя входа отключено.|  
|**подключение**|**connection_failed**|6|**failed_to_open_db**|2|*Примечание. Применяется только к версии 11 базы данных Azure SQL.*<br /><br /> Не удалось открыть базу данных. Может быть вызвано тем, что база данных не существует или проверка подлинности для открытия базы данных не пройдена.|  
|**подключение**|**connection_failed**|7|**blocked_by_firewall**|2|Клиенту с IP-адресом доступ к серверу не разрешен.|  
|**подключение**|**connection_failed**|8|**client_close**|2|*Примечание. Применяется только к версии 11 базы данных Azure SQL.*<br /><br /> При установке соединения могло быть превышено время ожидания клиента. Попробуйте увеличить время ожидания соединения.|  
|**подключение**|**connection_failed**|9|**Перенастройка**|2|*Примечание. Применяется только к версии 11 базы данных Azure SQL.*<br /><br /> При подключении возникла ошибка, так как в это время выполнялась настройка базы данных.|  
|**подключение**|**connection_terminated**|0|**idle_connection_timeout**|2|*Примечание. Применяется только к версии 11 базы данных Azure SQL.*<br /><br /> Соединение бездействует дольше заданного системой порогового периода.|  
|**подключение**|**connection_terminated**|1|**Перенастройка**|2|*Примечание. Применяется только к версии 11 базы данных Azure SQL.*<br /><br /> Сеанс прерван из-за изменения конфигурации базы данных.|  
|**подключение**|**Регулирование**|*\<код причины >*|**reason_code**|2|*Примечание. Применяется только к версии 11 базы данных Azure SQL.*<br /><br /> Запрос регулируется.  Код причины регулирования:  *\<код причины >*. Дополнительные сведения см. в разделе [регулирование ресурсов ядра](https://msdn.microsoft.com/library/windowsazure/dn338079.aspx).|  
|**подключение**|**throttling_long_transaction**|40549|**long_transaction**|2|*Примечание. Применяется только к версии 11 базы данных Azure SQL.*<br /><br /> Сеанс завершен по причине долго выполняющейся транзакции. Рекомендуется сократить транзакцию. Дополнительные сведения см. в разделе [ограничения ресурсов](https://msdn.microsoft.com/library/windowsazure/dn338081.aspx).|  
|**подключение**|**throttling_long_transaction**|40550|**excessive_lock_usage**|2|*Примечание. Применяется только к версии 11 базы данных Azure SQL.*<br /><br /> Сеанс был завершен в связи с тем, что он получил слишком много блокировок. Рекомендуется сократить число строк, считываемых или изменяемых в одной транзакции. Дополнительные сведения см. в разделе [ограничения ресурсов](https://msdn.microsoft.com/library/windowsazure/dn338081.aspx).|  
|**подключение**|**throttling_long_transaction**|40551|**excessive_tempdb_usage**|2|*Примечание. Применяется только к версии 11 базы данных Azure SQL.*<br /><br /> Сеанс был завершен в связи с чрезмерным использованием базы данных TEMPDB. Попробуйте изменить запрос, чтобы сократить объем использования временных таблиц. Дополнительные сведения см. в разделе [ограничения ресурсов](https://msdn.microsoft.com/library/windowsazure/dn338081.aspx).|  
|**подключение**|**throttling_long_transaction**|40552|**excessive_log_space_usage**|2|*Примечание. Применяется только к версии 11 базы данных Azure SQL.*<br /><br /> Сеанс был завершен в связи с чрезмерным использованием объема журнала транзакций. Рекомендуется сократить число строк, изменяемых в одной транзакции. Дополнительные сведения см. в разделе [ограничения ресурсов](https://msdn.microsoft.com/library/windowsazure/dn338081.aspx).|  
|**подключение**|**throttling_long_transaction**|40553|**excessive_memory_usage**|2|*Примечание. Применяется только к версии 11 базы данных Azure SQL.*<br /><br /> Сеанс был завершен в связи с чрезмерным использованием памяти. Рекомендуется изменить запрос, сократив число обрабатываемых строк. Дополнительные сведения см. в разделе [ограничения ресурсов](https://msdn.microsoft.com/library/windowsazure/dn338081.aspx).|  
|**ядра**|**взаимоблокировки**|0|**взаимоблокировки**|2|Возникла взаимоблокировка.|  
  
## <a name="permissions"></a>Разрешения  
 Пользователи с разрешением на доступ к **master** базы данных имеют доступ только для чтения к этому представлению.  
  
## <a name="remarks"></a>Примечания  
  
### <a name="event-aggregation"></a>Статистическая обработка событий  
 Сведения о событиях для этого представления собираются и обрабатываются каждые 5 минут. **Event_count** столбец представляет, сколько раз определенный **event_type** и **event_subtype** произошла для конкретной базы данных в течение заданного интервала времени.  
  
> [!NOTE]  
>  Некоторые события, например взаимоблокировки, не обрабатываются статистически. Для этих событий **event_count** будет иметь значение 1 и **start_time** и **end_time** будет равно фактические даты в формате UTC и время, когда произошло событие.  
  
 Например, если пользователю не удается подключиться к базе данных Database1 из-за недопустимого имени входа 7 раз с 11:00 до 11:05 5 февраля 2012 г. (UTC), эти сведения доступны в одной строке в следующем представлении:  
  
|**database_name**|**start_time**|**end_time**|**event_category**|**event_type**|**event_subtype**|**event_subtype_desc**|**severity**|**event_count**|**Описание**|**additional_data**|  
|------------------------|---------------------|-------------------|-------------------------|---------------------|------------------------|------------------------------|------------------|----------------------|---------------------|--------------------------|  
|`Database1`|`2012-02-05 11:00:00`|`2012-02-05 11:05:00`|`connectivity`|`connection_failed`|`4`|`login_failed_for_user`|`2`|`7`|`Login failed for user.`|`NULL`|  
  
### <a name="interval-starttime-and-endtime"></a>start_time и end_time интервала  
 Событие включается в интервал статистической обработки при возникновении события *на* или _после_**start_time** и _перед_  **end_time** для этого интервала. Например, событие, которое происходит точно в `2012-10-30 19:25:00.0000000`, будет включено только во второй интервал, показанный ниже.  
  
```  
start_time                    end_time  
2012-10-30 19:20:00.0000000   2012-10-30 19:25:00.0000000  
2012-10-30 19:25:00.0000000   2012-10-30 19:30:00.0000000  
```  
  
### <a name="data-updates"></a>Обновление данных  
 Данные в этом представлении с течением времени накапливаются. Как правило, данные накапливаются в течение часа с начала интервала статистической обработки, но для отображения всех данных в представлении может потребоваться до 24 часов. В течение этого времени сведения в одной строке могут периодически обновляться.  
  
### <a name="data-retention"></a>Хранение данных  
 Данные в этом представлении сохраняются не более 30 дней или по возможности меньше в зависимости от числа баз данных на логическом сервере и числа уникальных событий, создаваемых каждой базой данных. Для сохранения этих данных в течение более длительного периода скопируйте их в отдельную базу данных. После создания первоначальной копии представления строки могут быть обновлены по мере накопления данных. Чтобы копия данных была актуальной, периодически выполняйте просмотр таблицы для определения увеличения числа событий существующих строк и для определения новых строк (вы можете определить уникальные строки с помощью времени начала и окончания интервала), а затем обновить свою копию данных с применением этих изменений.  
  
### <a name="errors-not-included"></a>Исключенные ошибки  
 Это представление может содержать не все сведения о подключениях и ошибках:  
  
-   Это представление содержит не все [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ошибки, которые могут произойти, только теми, которые указаны в базы данных [типы событий](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes) в этом разделе.  
  
-   Если в центре обработки данных [!INCLUDE[ssSDS](../../includes/sssds-md.md)] возникла ошибка компьютера, в таблице событий может отсутствовать небольшой объем данных логического сервера.  
  
-   Если IP-адрес заблокирован через DoSGuard, события подключения с этого IP-адреса не могут собираться и не будут отображаться в этом представлении.  
  
## <a name="examples"></a>Примеры  
  
### <a name="simple-examples"></a>Простые примеры  
 Следующий запрос возвращает все события, произошедшие между 12:00 25 сентября до 12:00 28 сентября 2011 г. (UTC). По умолчанию результаты запроса сортируются по **start_time** (по возрастанию).  
  
```  
SELECT * FROM sys.event_log   
WHERE start_time >= '2011-09-25 12:00:00'   
    AND end_time <= '2011-09-28 12:00:00';  
```  
  
 Следующий запрос возвращает все события взаимоблокировки для базы данных Database1 (применяется только к базе данных SQL Azure версии 11).  
  
```  
SELECT * FROM sys.event_log   
WHERE event_type = 'deadlock'   
    AND database_name = 'Database1';  
```  
<a name="Deadlock"></a> Следующий запрос возвращает все события взаимоблокировки для базы данных Database1 (применяется только к базе данных SQL Azure версии 12).  
  
```  
WITH CTE AS (  
       SELECT CAST(event_data AS XML)  AS [target_data_XML]   
   FROM sys.fn_xe_telemetry_blob_target_read_file('dl', null, null, null)  
)  
SELECT target_data_XML.value('(/event/@timestamp)[1]', 'DateTime2') AS Timestamp,  
target_data_XML.query('/event/data[@name=''xml_report'']/value/deadlock') AS deadlock_xml,  
target_data_XML.query('/event/data[@name=''database_name'']/value').value('(/value)[1]', 'nvarchar(100)') AS db_name  
FROM CTE   
  
```  
  
  
 Следующий запрос возвращает события жесткого регулирования для рабочих потоков SQL, возникших с 10:00 до 11:00 на 25 сентября 2011 г. (UTC).  
  
```  
SELECT * FROM sys.event_log   
WHERE event_type = 'throttling'   
    AND event_subtype = 4194307   
    AND start_time >= '2011-09-25 10:00:00'   
    AND end_time <= '2011-09-25 11:00:00';  
```  
  
### <a name="db-scoped-extended-event"></a>Уровня базы данных расширенных событий  
 В следующем примере кода используется для настройки сеанса расширенных событий (XEvent) уровня базы данных:  
  
```sql  
IF EXISTS  
    (SELECT * from sys.database_event_sessions  
        WHERE name = 'azure_monitor_deadlock_session')  
BEGIN  
    ALTER EVENT SESSION azure_monitor_deadlock_session  
        ON DATABASE  
        DROP TARGET package0.ring_buffer;  
  
    DROP EVENT SESSION azure_monitor_deadlock_session  
        ON DATABASE;  
END  
  
CREATE EVENT SESSION azure_monitor_deadlock_session  
    ON DATABASE  
    ADD EVENT sqlserver.database_xml_deadlock_report  
    ADD TARGET package0.ring_buffer  
    (  
        SET max_memory = 2048, max_events_limit = 10  
    )  
    WITH (STARTUP_STATE = ON,  
          EVENT_RETENTION_MODE = ALLOW_SINGLE_EVENT_LOSS);  
  
ALTER EVENT SESSION azure_monitor_deadlock_session  
    ON DATABASE  
    STATE = START;  
```  
  
### <a name="check-for-deadlock"></a>Поиск взаимоблокировок

Используйте следующий запрос для проверки, если возникает взаимоблокировка.  
  
```sql  
WITH CTE AS (  
    SELECT CAST(xet.target_data AS XML)  AS [target_data_XML]  
        FROM            sys.dm_xe_database_session_targets AS xet  
             INNER JOIN sys.dm_xe_database_sessions        AS xe  
                 ON (xe.address = xet.event_session_address)  
        WHERE xe.name = 'azure_monitor_deadlock_session'  
)  
, CTE2 AS (  
    SELECT  
            T2.EventData.query('.').value(  
                '(/event/@timestamp)[1]', 'DateTime2') AS Timestamp,  
            T2.EventData.query('.').query(  
                '(/event/data/value/deadlock)[1]')     AS deadlock_xml  
        FROM CTE  
            CROSS Apply [target_data_XML].nodes(  
                '/RingBufferTarget/event') AS T2(EventData)  
)  
SELECT * FROM CTE2;  
```  
  
## <a name="see-also"></a>См. также  
 [Расширенные события в базе данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-xevent-db-diff-from-svr/)  
  
  
