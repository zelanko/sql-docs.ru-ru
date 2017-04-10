---
title: "Практическое руководство: Создание пула ресурсов для R | Microsoft Docs"
ms.custom: ""
ms.date: "10/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c7f7f6e4-774d-4b45-b94a-f06c51718475
caps.latest.revision: 19
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 19
---
# Практическое руководство: Создание пула ресурсов для R
  В этом разделе описывается создание пула ресурсов специально для управления рабочими нагрузками R в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Он предполагает, что службы R (в базы данных) уже установлены и необходимо перенастроить [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] экземпляра для поддержки более точное управление ресурсы, используемые R.  
  
 Дополнительные сведения об управлении ресурсами сервера см. в разделе [регулятора ресурсов](../../relational-databases/resource-governor/resource-governor.md) и [ресурсов регулятора связанных динамических административных представлений и #40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md).  
  
 **Шаги**  
  
1.  Просмотреть состояние существующих пулов ресурсов  
  
2.  Изменение пулов ресурсов сервера  
  
3.  Создание пула ресурсов для внешних процессов  
  
4.  Создайте функцию классификации для идентификации запросов R  
  
5.  Убедитесь, что новый пул ресурсов внешних захватывающего задания R  
  
##  <a name="bkmk_ReviewStatus"></a> Просмотр состояния существующих пулов ресурсов  
  
1.  Во-первых Проверьте ресурсы, выделенные в пул по умолчанию для сервера.  
  
    ```  
    SELECT * FROM sys.resource_governor_resource_pools WHERE name = 'default'  
    ```  
     **Результаты**

    |pool_id|имя|min_cpu_percent|max_cpu_percent|min_memory_percent|max_memory_percent|cap_cpu_percent|min_iops_per_volume|max_iops_per_volume|  
    |-|-|-|-|-|-|-|-|-|  
    |2|значение по умолчанию|0|100|0|100|100|0|0|  

2.  Проверьте ресурсы, выделенные по умолчанию **внешних** пула ресурсов.  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pools WHERE name = 'default'  
    ```  
     
    **Результаты**

    |external_pool_id|имя|max_cpu_percent|max_memory_percent|max_processes|version|  
    |-|-|-|-|-|-|  
    |2|значение по умолчанию|100|20|0|2|  
 
3.  В разделе Параметры сервера по умолчанию среда выполнения R, вероятно, будет недостаточно ресурсов для выполнения большинства задач. Чтобы изменить это, необходимо изменить использование ресурсов сервера следующим образом:  
  
    -   Уменьшить максимальный компьютера памяти, который может использоваться [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
    -   Увеличение памяти максимальный компьютера, который используется внешний процесс  
  
## Изменить использование ресурсов сервера  
  
1.  В [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], выполните следующую инструкцию, чтобы ограничить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объема используемой памяти **60%** значения в параметре «max server memory».  
  
    ```  
    ALTER RESOURCE POOL "default" WITH (max_memory_percent = 60);  
    ```  
  
2.  Аналогично, необходимо выполнить следующую инструкцию, чтобы ограничить использование памяти, внешние процессы для **40%** ресурсов всего компьютера.  
  
    ```  
    ALTER EXTERNAL RESOURCE POOL "default" WITH (max_memory_percent = 40);  
    ```  
  
3.  Чтобы применить эти изменения, необходимо перенастроить и перезапустить регулятора ресурсов следующим образом:  
  
    ```  
    ALTER RESOURCE GOVERNOR reconfigure;  
    ```  
  
    > [!NOTE]  
    >  Это просто рекомендуемые параметры для запуска. следует оценить R требования относительно других серверных процессов, чтобы определить правильный баланс для среды и рабочей нагрузки.  
  
## Создание пула внешних ресурсов, определяемых пользователем  
  
1.  Любые изменения конфигурации регулятора ресурсов применяются для сервера в целом и рабочих нагрузок, использующих пулы по умолчанию для сервера, а также рабочих нагрузок, использующих внешние пулов.  
  
     Таким образом чтобы обеспечить более точный контроль над которой рабочие нагрузки должны иметь приоритет, можно создать новый пул внешних ресурсов, определяемых пользователем. Необходимо также определить функцию классификации и назначить пула внешних ресурсов.  
  
     Начните с создания нового *пула пользовательских внешних ресурсов*. В следующем примере с именем пула **ds_ep**.  
  
    ```  
    CREATE EXTERNAL RESOURCE POOL ds_ep WITH (max_memory_percent = 40);  
    ```  
  
     Обратите внимание, новый **ВНЕШНИХ** ключевое слово.  
  
2.  Создайте группу рабочей нагрузки с именем `ds_wg` для использования в управлении запросов сеанса. Для SQL-запросов будет использовать пул по умолчанию; для внешнего процесса, все запросы будут использовать `ds_ep` пула.  
  
    ```  
    CREATE WORKLOAD GROUP ds_wg WITH (importance = medium) USING "default", EXTERNAL "ds_ep";  
    ```  
  
     Запросы назначаются в группу по умолчанию всякий раз, когда невозможно классифицировать запрос, или любой другой сбой классификации.  
  
     Дополнительные сведения см. в разделе [группы рабочей нагрузки регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-workload-group.md) и [СОЗДАНИЕ ГРУППЫ рабочей НАГРУЗКИ и #40; Transact-SQL &#41;](../../t-sql/statements/create-workload-group-transact-sql.md).  
  
## Создайте функцию классификации для R  
  
1.  Функция классификации проверяет входящие задачи и определяет, является ли задача, могут выполняться в текущем пуле ресурсов. Задачи, которые не отвечают критериям этого функцию классификации назначаются обратно в пул ресурсов по умолчанию на сервере.  
  
     Начните с указания функцию-классификатор использование регулятором ресурсов для определения пулов ресурсов. Значение null можно назначить в качестве заполнителя для функции-классификатора.  
  
    ```  
    ALTER RESOURCE GOVERNOR WITH (classifier_function = NULL);  
    ALTER RESOURCE GOVERNOR reconfigure;  
    ```  
  
     Дополнительные сведения см. в разделе [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md).  
  
2.  В функцию-классификатор для каждого пула ресурсов определить тип инструкции или входящих запросов, которые должны быть назначены в пул ресурсов.  
  
     Например следующая функция возвращает имя схемы, назначенный пулу внешних ресурсов, определяемых пользователем, если приложение, отправившего запрос, является «Узел Microsoft R» или «RStudio»; в противном случае возвращается в пул ресурсов по умолчанию.  
  
    ```  
    USE master  
    GO  
    CREATE FUNCTION is_ds_apps()  
    RETURNS sysname  
    WITH schemabinding  
    AS  
    BEGIN  
        IF program_name() in ('Microsoft R Host', 'RStudio') RETURN 'ds_wg';  
        RETURN 'default'  
        END;  
    GO  
    ```  
  
3.  При создании функции перенастройте группу ресурсов, чтобы назначить новую функцию-классификатор внешней группы ресурсов, определенных ранее.  
  
    ```  
    ALTER RESOURCE GOVERNOR WITH  (classifier_function = dbo.is_ds_apps);  
    ALTER RESOURCE GOVERNOR WITH reconfigure;  
    go  
    ```  
  
## Проверьте сопоставление и новые пулы ресурсов  
  
1.  Чтобы убедиться, что были внесены изменения, проверьте конфигурацию сервера памяти и ЦП для каждой группы рабочей нагрузки, связанные с всех пулов ресурсов экземпляра: пул по умолчанию для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сервера, пул ресурсов по умолчанию для внешних процессов и пользовательских пула для внешних процессов.  
  
    ```  
    SELECT * FROM sys.resource_governor_workload_groups;  
    ```  

    **Результаты**

    |идентификатор_группы|имя|importance|request_max_memory_grant_percent|request_max_cpu_time_sec|request_memory_grant_timeout_sec|max_dop|group_max_requests pool_id|pool_idd|external_pool_idd|  
    |-|-|-|-|-|-|-|-|-|-|  
    |1|Внутренние|Средний|25|0|0|0|0|1|2|  
    |2|значение по умолчанию|Средний|25|0|0|0|0|2|2|  
    |256|ds_wg|Средний|25|0|0|0|0|2|256|  
  
2.  Можно использовать новые представления каталога [sys.resource_governor_external_resource_pools &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md), для просмотра всех пулов внешних ресурсов.  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pools;  
    ```  
    **Результаты**
    
    |external_pool_id|имя|max_cpu_percent|max_memory_percent|max_processes|version|  
    |-|-|-|-|-|-|  
    |2|значение по умолчанию|100|20|0|2|  
    |256|ds_ep|100|40|0|1|  
  
     Дополнительные сведения см. в разделе [представления каталога регулятора ресурсов &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md).  
  
3.  Следующая инструкция возвращает сведения о ресурсов компьютеров, которые будут привязаны к пулу внешних ресурсов.  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pool_affinity;  
    ```  
  
     В этом случае поскольку пулы были созданы со сходством AUTO, не будут отображаться данные. Дополнительные сведения см. в разделе [представление sys.dm_resource_governor_resource_pool_affinity &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md).  
  
## См. также  
 [регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)   
 [Управление ресурсами для служб R](../../advanced-analytics/r-services/resource-governance-for-r-services.md)  
  
  