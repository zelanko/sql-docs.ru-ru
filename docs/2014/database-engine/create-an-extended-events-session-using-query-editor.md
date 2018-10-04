---
title: Создание сеанса расширенных событий с помощью редактора запросов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- create extended events session
- extended events [SQL Server], create session
ms.assetid: cba0e02b-b201-4863-bf1b-9164e68e5fa8
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6e0c243dcacf653167477137e26f0767985f6fa3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48150874"
---
# <a name="create-an-extended-events-session-using-query-editor"></a>Создание сеанса расширенных событий с помощью редактора запросов
  Сеанс расширенных событий можно создать с помощью редактора запросов или в обозревателе объектов. В обозревателе объектов предусмотрена расширенная подсистема событий, включающая два пользовательских интерфейса, которые могут быть использованы для создания, изменения и просмотра данных сеанса события. К ним относится мастер, который служит для создания сеанса события, а также новый пользовательский интерфейс сеанса, который представляет более сложные параметры конфигурации. Сеанс расширенных событий можно создать для диагностики трассировок SQL Server, что дает возможность решать, например, следующие проблемы.  
  
-   Находить наиболее ресурсоемкие запросы.  
  
-   Находить основные причины конфликтов кратковременных блокировок.  
  
-   Находить запросы, которые блокируют другие запросы.  
  
-   Устранять неполадки чрезмерного использования ЦП, вызванные перекомпиляцией запросов.  
  
-   Устранять неполадки взаимоблокировок.  
  
 Сведения о создании сеанса расширенных событий с помощью мастера новых сеансов см. в статье [Создание сеанса расширенных событий с помощью пользовательского интерфейса нового сеанса (обозреватель объектов)](../ssms/object/object-explorer.md). Сведения о создании сеанса расширенных событий с помощью мастера новых сеансов см. в статье [Создание сеанса расширенных событий с помощью диалогового окна "Создание сеанса"](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md).  
  
##  <a name="BeforeYouBegin"></a> Разрешения  
 Для создания сеанса расширенных событий требуется разрешение ALTER ANY EVENT SESSION.  
  
## <a name="creating-an-extended-events-session-using-query-editor"></a>Создание сеанса расширенных событий с помощью редактора запросов  
  
#### <a name="to-create-an-extended-events-session"></a>Создание сеанса расширенных событий  
  
1.  Ниже показано, как создать сеанс расширенных событий с помощью редактора запросов в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
     Определите, какие события необходимо использовать в сеансе. Для просмотра всех доступных событий вместе с ключевым словом и каналом используйте следующий запрос:  
  
    > [!NOTE]  
    >  Дополнительные сведения о ключевых словах и каналах см. в статье [Пакеты обработки расширенных событий SQL Server](../relational-databases/extended-events/sql-server-extended-events-packages.md).  
  
    ```  
    SELECT p.name, c.event, k.keyword, c.channel, c.description FROM  
       (  
       SELECT event_package = o.package_guid, o.description,   
       event=c.object_name, channel = v.map_value  
       FROM sys.dm_xe_objects o  
       LEFT JOIN sys.dm_xe_object_columns c ON o.name = c.object_name  
       INNER JOIN sys.dm_xe_map_values v ON c.type_name = v.name   
       AND c.column_value = cast(v.map_key AS nvarchar)  
       WHERE object_type = 'event' AND (c.name = 'CHANNEL' or c.name IS NULL)  
       ) c LEFT JOIN   
       (  
       SELECT event_package = c.object_package_guid, event = c.object_name,   
       keyword = v.map_value  
       FROM sys.dm_xe_object_columns c INNER JOIN sys.dm_xe_map_values v   
       ON c.type_name = v.name AND c.column_value = v.map_key   
       AND c.type_package_guid = v.object_package_guid  
       INNER JOIN sys.dm_xe_objects o ON o.name = c.object_name   
       AND o.package_guid = c.object_package_guid  
       WHERE object_type = 'event' AND c.name = 'KEYWORD'   
       ) k  
       ON  
       k.event_package = c.event_package AND (k.event=c.event or k.event IS NULL)  
       INNER JOIN sys.dm_xe_packages p ON p.guid = c.event_package  
    ORDER BY keyword desc, channel, event  
    ```  
  
2.  В новом окне запроса добавьте следующие инструкции для создания сеанса события, заменив *имя_сеанса* на имя сеанса, который будет использован.  
  
    > [!IMPORTANT]  
    >  Шаги с 2 по 6 данной процедуры описывают каждый раздел определения сеанса событий. Перед исполнением необходимо добавить все инструкции в одно окно запроса. Полный пример запроса см. в подразделе «Пример» этого раздела.  
  
    ```  
    CREATE EVENT SESSION session_name   
    ON SERVER  
    ```  
  
3.  Добавьте события, которые требуется отслеживать, в формате *имя_пакета*.*имя_события*. Для каждого события добавьте строку следующего вида:  
  
    ```  
    ADD EVENT package_name.event_name  
    ```  
  
     Пример:  
  
    ```  
    ADD EVENT sqlserver.file_read_completed,  
    ADD EVENT sqlserver.file_write_completed  
    ```  
  
4.  (Необязательно) После добавления события можно добавить действия, подлежащие выполнению. Можно также добавить предикаты. Предикаты используются для установки условия, когда целевой объект должен получить сведения о событии. Действия добавляются с помощью предложения ACTION действия, а предикаты добавляются с помощью предложения WHERE. Например, чтобы добавить действие и предикат, в котором текст [!INCLUDE[tsql](../includes/tsql-md.md)] записывается для события sqlserver.file_read_completed и идентификатор файла равен 1, следует включить следующий инструкцию:  
  
    ```  
    ADD EVENT sqlserver.file_read_completed  
       (ACTION (sqlserver.sql_text)  
       WHERE file_id = 1),  
    ```  
  
    -   Для просмотра доступных действий используйте следующий запрос:  
  
        ```  
        SELECT p.name AS 'package_name', xo.name AS 'action_name', xo.description, xo.object_type  
        FROM sys.dm_xe_objects AS xo  
        JOIN sys.dm_xe_packages AS p  
           ON xo.package_guid = p.guid  
        WHERE xo.object_type = 'action'  
        AND (xo.capabilities & 1 = 0   
        OR xo.capabilities IS NULL)  
        ORDER BY p.name, xo.name  
        ```  
  
    -   Чтобы просмотреть предикаты, доступные для события, используйте следующий запрос, заменив *имя_события* на имя события, для которого необходимо добавить предикат:  
  
        ```  
        SELECT *  
        FROM sys.dm_xe_object_columns  
        WHERE object_name = 'event_name'  
        AND column_type = 'data'  
        ```  
  
         Пример:  
  
        ```  
        SELECT *   
        FROM sys.dm_xe_object_columns   
        WHERE object_name = 'file_read_completed'  
        AND column_type = 'data'  
        ```  
  
         Помните, что можно также добавить источники глобальных предикатов. Источник глобальных предикатов может быть использован в любом выражении предикатов. Для просмотра доступных источников глобальных предикатов используйте следующий запрос:  
  
        ```  
        SELECT p.name AS package_name, xo.name AS predicate_name  
           , xo.description, xo.object_type  
        FROM sys.dm_xe_objects AS xo  
        JOIN sys.dm_xe_packages AS p  
           ON xo.package_guid = p.guid  
        WHERE xo.object_type = 'pred_source'  
        ORDER BY p.name, xo.name  
        ```  
  
         Например, следующее выражение предиката можно использовать для указания, что данные должны быть собраны для события первые пять раз, когда происходит событие.  
  
        ```  
        WHERE package0.counter <= 5  
        ```  
  
5.  Добавьте нужный целевой объект, в котором данные события будут обработаны и использованы. Используйте следующий формат:  
  
    ```  
    ADD TARGET package_name.target_name  
    ```  
  
     В следующем примере добавляется асинхронный целевой объект файла.  
  
    ```  
    ADD TARGET package0.asynchronous_file_target  
       (SET filename = 'c:\temp\xelog.xel', metadatafile = 'c:\temp\xelog.xem')  
    ```  
  
     Для просмотра списка доступных целей используйте следующий запрос:  
  
    ```  
    SELECT p.name AS 'package_name', xo.name AS 'target_name'  
       , xo.description, xo.object_type   
    FROM sys.dm_xe_objects AS xo  
    JOIN sys.dm_xe_packages AS p  
       ON xo.package_guid = p.guid  
    WHERE xo.object_type = 'target'  
    AND (xo.capabilities & 1 = 0  
    OR xo.capabilities IS NULL)  
    ORDER BY p.name, xo.name  
    ```  
  
    > [!NOTE]  
    >  Дополнительные сведения о разных типах целевых объектов см. в статье [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md).  
  
6.  Просмотрите и добавьте любые дополнительные параметры конфигурации. Например, можно настроить параметры, такие как режим хранения событий, срок хранения событий в буфере или необходимость запуска сеанса событий автоматически при запуске [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Параметры описаны в статье [ALTER EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/alter-event-session-transact-sql). Если эти параметры не заданы вручную, будут использоваться значения по умолчанию.  
  
7.  Запустите сеанс.  
  
    > [!NOTE]  
    >  Дополнительные сведения о просмотре результатов сеанса см. в соответствующем разделе для типа целевого объекта [Цели расширенных событий SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md) электронной документации.  
  
 В примере ниже создается сеанс расширенных событий с именем IOActivity, который собирает следующие сведения.  
  
-   Данные события для завершенных операций чтения файла, включая связанный текст [!INCLUDE[tsql](../includes/tsql-md.md)] для операций чтения, в которых идентификатор файла равен 1.  
  
-   Данные события для завершенных операций записи в файл.  
  
-   Данные событий для данных, которые записаны из кэша журнала в физический файл журнала.  
  
 Сеанс отправляет результат в файл целевого объекта.  
  
```  
CREATE EVENT SESSION IOActivity  
ON SERVER  
  
ADD EVENT sqlserver.file_read_completed  
   (  
   ACTION (sqlserver.sql_text)  
   WHERE file_id = 1),  
ADD EVENT sqlserver.file_write_completed,  
ADD EVENT sqlserver.databases_log_flush  
  
ADD TARGET package0.asynchronous_file_target   
   (SET filename = 'c:\temp\xelog.xel', metadatafile = 'c:\temp\xelog.xem')  
```  
  
## <a name="see-also"></a>См. также  
 [CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql)   
 [Цели расширенных событий SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md)   
 [Пакеты обработки расширенных событий SQL Server](../relational-databases/extended-events/sql-server-extended-events-packages.md)  
  
  
