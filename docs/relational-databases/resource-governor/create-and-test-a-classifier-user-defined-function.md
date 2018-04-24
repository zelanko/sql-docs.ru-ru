---
title: Создание и тестирование пользовательской функции-классификатора | Документация Майкрософт
ms.custom: ''
ms.date: 07/11/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: resource-governor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Resource Governor, classifier function create
- classifier function [SQL Server], test
- classifier function [SQL Server], create
- Resource Governor, classifier function test
ms.assetid: 7866b3c9-385b-40c6-aca5-32d3337032be
caps.latest.revision: 25
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cca4d793139499715ed86829481f53a72da6b5b3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="create-and-test-a-classifier-user-defined-function"></a>Создать и проверить определяемую пользователем функцию-классификатор
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описывается создание и проверка определяемой пользователем функции-классификатора (UDF). Шаги включают выполнение инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)] в редакторе запросов [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
 Пример, показанный в следующей процедуре, иллюстрирует возможности создания довольно сложной определяемой пользователем функции-классификатора.  
  
 Пример.  
  
-   Пул ресурсов (pProductionProcessing) и группа рабочей нагрузки (gProductionProcessing) создаются для рабочей обработки в течение определенного диапазона времени.  
  
-   Пул ресурсов (pOffHoursProcessing) и группа рабочей нагрузки (gOffHoursProcessing) создаются для управления соединениями, не удовлетворяющими требованиям рабочей обработки.  
  
-   Таблица (TblClassificationTimeTable) создается в базе данных master для сохранения времени запуска и остановки, которые можно вычислить после времени входа в систему. Она должна быть создана в базе данных master, так как регулятор ресурсов использует для функций-классификаторов привязку к схеме.  
  
    > [!NOTE]  
    >  Рекомендуется хранить большие часто обновляемые таблицы за пределами базы данных master.  
  
 Функция-классификатор увеличивает время входа в систему. Излишне сложная функция может вызвать истечение времени ожидания при входе или снизить скорость быстрых соединений.  
  
## <a name="to-create-the-classifier-user-defined-function"></a>Создание определяемой пользователем функции-классификатора  
  
1.  Создайте и настройте новые пулы ресурсов и группы рабочей нагрузки. Назначьте каждую группу рабочей нагрузки соответствующему пулу ресурсов.  
  
    ```  
    --- Create a resource pool for production processing  
    --- and set limits.  
    USE master;  
    GO  
    CREATE RESOURCE POOL pProductionProcessing  
    WITH  
    (  
         MAX_CPU_PERCENT = 100,  
         MIN_CPU_PERCENT = 50  
    );  
    GO  
    --- Create a workload group for production processing  
    --- and configure the relative importance.  
    CREATE WORKLOAD GROUP gProductionProcessing  
    WITH  
    (  
         IMPORTANCE = MEDIUM  
    );  
    --- Assign the workload group to the production processing  
    --- resource pool.  
    USING pProductionProcessing  
    GO  
    --- Create a resource pool for off-hours processing  
    --- and set limits.  
  
    CREATE RESOURCE POOL pOffHoursProcessing  
    WITH  
    (  
         MAX_CPU_PERCENT = 50,  
         MIN_CPU_PERCENT = 0  
    );  
    GO  
    --- Create a workload group for off-hours processing  
    --- and configure the relative importance.  
    CREATE WORKLOAD GROUP gOffHoursProcessing  
    WITH  
    (  
         IMPORTANCE = LOW  
    )  
    --- Assign the workload group to the off-hours processing  
    --- resource pool.  
    USING pOffHoursProcessing;  
    GO  
    ```  
  
2.  Обновите конфигурацию, хранимую в памяти.  
  
    ```  
    ALTER RESOURCE GOVERNOR RECONFIGURE;  
    GO  
    ```  
  
3.  Создайте таблицу и определите время запуска и остановки диапазона времени рабочей обработки.  
  
    ```  
    USE master;  
    GO  
    CREATE TABLE tblClassificationTimeTable  
    (  
         strGroupName     sysname          not null,  
         tStartTime       time              not null,  
         tEndTime         time              not null  
    );  
    GO  
    --- Add time values that the classifier will use to  
    --- determine the workload group for a session.  
    INSERT into tblClassificationTimeTable VALUES('gProductionProcessing', '6:35 AM', '6:15 PM');  
    go  
    ```  
  
4.  Создайте функцию-классификатор, использующую функции и значения времени, которые можно оценить со временем в таблице подстановки. Дополнительные сведения об использовании таблиц подстановки в функции-классификаторе см. в подразделе «Рекомендации по использованию таблиц подстановки в функции-классификаторе» данного раздела.  
  
    > [!NOTE]  
    >  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] представлен расширенный набор типов данных и функций даты и времени. Дополнительные сведения см. в статье [Типы данных и функции даты и времени (Transact-SQL)](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
    ```  
    CREATE FUNCTION fnTimeClassifier()  
    RETURNS sysname  
    WITH SCHEMABINDING  
    AS  
    BEGIN  
    /* We recommend running the classifier function code under 
    snapshot isolation level OR using NOLOCK hint to avoid blocking on 
    lookup table. In this example, we are using NOLOCK hint. */
         DECLARE @strGroup sysname  
         DECLARE @loginTime time  
         SET @loginTime = CONVERT(time,GETDATE())  
         SELECT TOP 1 @strGroup = strGroupName  
              FROM dbo.tblClassificationTimeTable WITH(NOLOCK)
              WHERE tStartTime <= @loginTime and tEndTime >= @loginTime  
         IF(@strGroup is not null)  
         BEGIN  
              RETURN @strGroup  
         END  
    --- Use the default workload group if there is no match  
    --- on the lookup.  
         RETURN N'gOffHoursProcessing'  
    END;  
    GO  
    ```  
  
5.  Зарегистрируйте функцию-классификатор и обновите конфигурацию, хранимую в памяти.  
  
    ```  
    ALTER RESOURCE GOVERNOR with (CLASSIFIER_FUNCTION = dbo.fnTimeClassifier);  
    ALTER RESOURCE GOVERNOR RECONFIGURE;  
    GO  
    ```  
  
## <a name="to-verify-the-resource-pools-workload-groups-and-the-classifier-user-defined-function"></a>Проверка пулов ресурсов, групп рабочей нагрузки и определяемой пользователем функции-классификатора  
  
1.  Получите пул ресурсов и настройку группы рабочей нагрузки при помощи следующего запроса.  
  
    ```  
    USE master;  
    SELECT * FROM sys.resource_governor_resource_pools;  
    SELECT * FROM sys.resource_governor_workload_groups;  
    GO  
    ```  
  
2.  С помощью следующих запросов убедитесь в том, что функция-классификатор существует и включена.  
  
    ```  
    --- Get the classifier function Id and state (enabled).  
    SELECT * FROM sys.resource_governor_configuration;  
    GO  
    --- Get the classifer function name and the name of the schema  
    --- that it is bound to.  
    SELECT   
          object_schema_name(classifier_function_id) AS [schema_name],  
          object_name(classifier_function_id) AS [function_name]  
    FROM sys.dm_resource_governor_configuration;  
    ```  
  
3.  Получите текущие данные среды выполнения пулов ресурсов и групп рабочей нагрузки с помощью следующего запроса.  
  
    ```  
    SELECT * FROM sys.dm_resource_governor_resource_pools;  
    SELECT * FROM sys.dm_resource_governor_workload_groups;  
    GO  
    ```  
  
4.  С помощью следующего запроса выясните, какие сеансы существуют в каждой группе.  
  
    ```  
    SELECT s.group_id, CAST(g.name as nvarchar(20)), s.session_id, s.login_time, 
        CAST(s.host_name as nvarchar(20)), CAST(s.program_name AS nvarchar(20))  
    FROM sys.dm_exec_sessions AS s  
    INNER JOIN sys.dm_resource_governor_workload_groups AS g  
        ON g.group_id = s.group_id  
    ORDER BY g.name;  
    GO  
    ```  
  
5.  С помощью следующего запроса выясните, какие запросы существуют в каждой группе.  
  
    ```  
    SELECT r.group_id, g.name, r.status, r.session_id, r.request_id, 
        r.start_time, r.command, r.sql_handle, t.text   
    FROM sys.dm_exec_requests AS r  
    INNER JOIN sys.dm_resource_governor_workload_groups AS g  
        ON g.group_id = r.group_id  
    CROSS APPLY sys.dm_exec_sql_text(r.sql_handle) AS t  
    ORDER BY g.name;  
    GO  
    ```  
  
6.  С помощью следующего запроса выясните, какие запросы выполняются в классификаторе.  
  
    ```  
    SELECT s.group_id, g.name, s.session_id, s.login_time, s.host_name, s.program_name   
    FROM sys.dm_exec_sessions AS s  
    INNER JOIN sys.dm_resource_governor_workload_groups AS g  
        ON g.group_id = s.group_id  
           AND 'preconnect' = s.status  
    ORDER BY g.name;  
    GO  
  
    SELECT r.group_id, g.name, r.status, r.session_id, r.request_id, r.start_time, 
        r.command, r.sql_handle, t.text   
    FROM sys.dm_exec_requests AS r  
    INNER JOIN sys.dm_resource_governor_workload_groups AS g  
        ON g.group_id = r.group_id  
           AND 'preconnect' = r.status  
     CROSS APPLY sys.dm_exec_sql_text(r.sql_handle) AS t  
    ORDER BY g.name;  
    GO  
    ```  
  
## <a name="best-practices-for-using-lookup-tables-in-a-classifier-function"></a>Рекомендации по использованию таблиц подстановки в функции-классификаторе  
  
1.  Не используйте таблицу подстановки без крайней необходимости. Если таблицу подстановки необходимо использовать, ее можно включить в саму функцию, однако при этом следует учитывать сложность и динамические изменения функции-классификатора.  
  
2.  Ограничьте ввод и вывод данных, выполняемые для таблиц подстановки.  
  
    1.  Воспользуйтесь инструкцией TOP 1, чтобы вернуть только одну строку.  
  
    2.  Сведите к минимуму количество строк в таблице.  
  
    3.  Сделайте так, чтобы все строки таблицы были на одной странице или на небольшом количестве страниц.  
  
    4.  Убедитесь, что строки, найденные с помощью операций Index Seek, используют как можно больше столбцов поиска.  
  
    5.  Выполните денормализацию до одной таблицы, если необходимо использовать несколько таблиц с помощью инструкций объединения.  
  
3.  Запретите блокирование таблицы подстановки.  
  
    1.  Воспользуйтесь указанием `NOLOCK` для предотвращения блокирования или оператором `SET LOCK_TIMEOUT` в функции с максимальным значением 1000 миллисекунд.  
  
    2.  Таблицы должны существовать в базе данных master. (Когда подключение устанавливают клиентские компьютеры, можно гарантировать восстановление только базы данных master.)  
  
    3.  Всегда указывайте полное имя таблицы со схемой. Имя базы данных не требуется, так как это должна быть база данных master.  
  
    4.  Не используйте триггеры для таблицы.  
  
    5.  Обновляя содержимое таблицы, обязательно используйте в функции-классификаторе транзакцию уровня изоляции моментального снимка, чтобы запись не блокировала чтение. Обратите внимание, что может также помочь использование указания `NOLOCK` .  
  
    6.  По возможности отключите функцию-классификатор при изменении содержимого таблицы.  
  
        > [!WARNING]  
        >  Рекомендуется использовать именно эти методы. Если что-то не позволяет использовать эти методы, рекомендуем связаться со службой технической поддержки Майкрософт для эффективного устранения возможных проблем.  
  
## <a name="see-also"></a>См. также:  
 [Регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)   
 [Активация регулятора ресурсов](../../relational-databases/resource-governor/enable-resource-governor.md)   
 [Пул ресурсов регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [Группа рабочей нагрузки регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [Настройка регулятора ресурсов с помощью шаблона](../../relational-databases/resource-governor/configure-resource-governor-using-a-template.md)   
 [Просмотр свойств регулятора ресурсов](../../relational-databases/resource-governor/view-resource-governor-properties.md)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md)   
 [CREATE RESOURCE POOL (Transact-SQL)](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [CREATE WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [CREATE FUNCTION (Transact-SQL)](../../t-sql/statements/create-function-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
