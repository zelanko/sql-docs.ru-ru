---
title: "Практическое руководство по созданию пула ресурсов для R | Документация Майкрософт"
ms.custom: 
ms.date: 10/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7f7f6e4-774d-4b45-b94a-f06c51718475
caps.latest.revision: 19
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: be3afb3a1ff5175fbb3d0735cde59bd19bb47f6c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="how-to-create-a-resource-pool-for-r"></a>Практическое руководство по созданию пула ресурсов для R
  Здесь описывается создание пула ресурсов специально для управления рабочими нагрузками R в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Предполагается, что службы R (в базе данных) уже установлены и экземпляр [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] необходимо перенастроить для более точного управления ресурсами, используемыми R.  
  
 Дополнительные сведения об управлении ресурсами сервера см. в статьях [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) (Регулятор ресурсов) и [Resource Governor Related Dynamic Management Views (Transact-SQL)](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md) (Динамические административные представления регулятора ресурсов (Transact-SQL)).  
  
 **Шаги**  
  
1.  Просмотр состояния существующих пулов ресурсов.  
  
2.  Изменение пулов ресурсов сервера.  
  
3.  Создание пула ресурсов для внешних процессов.  
  
4.  Создание функции классификации для идентификации запросов R.  
  
5.  Проверка отслеживания заданий R новым внешним пулом ресурсов.  
  
##  <a name="bkmk_ReviewStatus"></a> Просмотр состояния существующих пулов ресурсов  
  
1.  Во-первых, проверьте ресурсы, выделенные для сервера пулу по умолчанию.  
  
    ```  
    SELECT * FROM sys.resource_governor_resource_pools WHERE name = 'default'  
    ```  
     **Результаты**

    |pool_id|имя|min_cpu_percent|max_cpu_percent|min_memory_percent|max_memory_percent|cap_cpu_percent|min_iops_per_volume|max_iops_per_volume|  
    |-|-|-|-|-|-|-|-|-|  
    |2|значение по умолчанию|0|100|0|100|100|0|0|  

2.  Проверьте ресурсы, выделенные **внешнему** пулу ресурсов по умолчанию.  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pools WHERE name = 'default'  
    ```  
     
    **Результаты**

    |external_pool_id|имя|max_cpu_percent|max_memory_percent|max_processes|version|  
    |-|-|-|-|-|-|  
    |2|значение по умолчанию|100|20|0|2|  
 
3.  При таких параметрах сервера по умолчанию среде выполнения R, вероятно, будет недостаточно ресурсов для выполнения большинства задач. Чтобы избежать этого, необходимо изменить параметры использования ресурсов сервера следующим образом:  
  
    -   уменьшить максимальный объем памяти компьютера, который может использоваться [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)];  
  
    -   увеличить максимальный объем памяти компьютера, который может использоваться внешними процессами.  
  
## <a name="modify-server-resource-usage"></a>Изменение использования ресурсов сервера  
  
1.  В [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] выполните следующую инструкцию, чтобы ограничить объем используемой сервером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] памяти, задав для параметра максимальной памяти сервера значение **60 %**.  
  
    ```  
    ALTER RESOURCE POOL "default" WITH (max_memory_percent = 60);  
    ```  
  
2.  Аналогично выполните следующую инструкцию, чтобы ограничить использование памяти внешними процессами до **40 %** общих ресурсов компьютера.  
  
    ```  
    ALTER EXTERNAL RESOURCE POOL "default" WITH (max_memory_percent = 40);  
    ```  
  
3.  Чтобы применить эти изменения, необходимо перенастроить и перезапустить регулятор ресурсов следующим образом:  
  
    ```  
    ALTER RESOURCE GOVERNOR reconfigure;  
    ```  
  
    > [!NOTE]  
    >  Это базовые рекомендуемые параметры. Следует оценить требования R относительно других серверных процессов, чтобы определить правильный баланс для среды и рабочей нагрузки.  
  
## <a name="create-a-user-defined-external-resource-pool"></a>Создание внешнего пула ресурсов, определяемого пользователем  
  
1.  Любые изменения конфигурации регулятора ресурсов применяются для сервера в целом и влияют на рабочие нагрузки, использующие пулы по умолчанию для сервера, а также на рабочие нагрузки, использующие внешние пулы.  
  
     Таким образом, чтобы обеспечить более точный контроль над тем, какие рабочие нагрузки должны иметь приоритет, можно создать новый внешний пул ресурсов, определяемый пользователем. Необходимо также определить функцию классификации и присвоить ее пулу внешних ресурсов.  
  
     Начните с создания нового *внешнего пула ресурсов, определяемого пользователем*. В следующем примере пулу присваивается имя **ds_ep**.  
  
    ```  
    CREATE EXTERNAL RESOURCE POOL ds_ep WITH (max_memory_percent = 40);  
    ```  
  
     Обратите внимание на новое ключевое слово **EXTERNAL**.  
  
2.  Создайте группу рабочей нагрузки с именем `ds_wg`, которая будет использоваться для управления запросами сеанса. Для SQL-запросов будет использоваться пул по умолчанию. Для всех запросов внешних процессов будет использоваться пул `ds_ep`.  
  
    ```  
    CREATE WORKLOAD GROUP ds_wg WITH (importance = medium) USING "default", EXTERNAL "ds_ep";  
    ```  
  
     Запросы назначаются группе по умолчанию всякий раз, когда невозможно классифицировать запрос, или при любой другой ошибке классификации.  
  
     Дополнительные сведения см. в статьях [Resource Governor Workload Group](../../relational-databases/resource-governor/resource-governor-workload-group.md) (Группа рабочей нагрузки регулятора ресурсов) и [CREATE WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/create-workload-group-transact-sql.md) (Инструкция CREATE WORKLOAD GROUP (Transact-SQL)).  
  
## <a name="create-a-classification-function-for-r"></a>Создание функции классификации для R  
  
1.  Функция классификации проверяет входящие задачи и определяет, можно ли выполнить задачу в текущем пуле ресурсов. Задачи, которые не отвечают критериям функции классификации, назначаются обратно в пул ресурсов по умолчанию на сервере.  
  
     Начните с указания, что регулятор ресурсов должен использовать функцию классификации для определения пулов ресурсов. В качестве заполнителя для функции классификации можно назначить значение null.  
  
    ```  
    ALTER RESOURCE GOVERNOR WITH (classifier_function = NULL);  
    ALTER RESOURCE GOVERNOR reconfigure;  
    ```  
  
     Дополнительные сведения см. в разделе [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md).  
  
2.  В функции классификации для каждого пула ресурсов можно определить тип инструкций или входящих запросов, которые должны быть назначены пулу ресурсов.  
  
     Например, следующая функция возвращает имя схемы, назначенной внешнему пулу ресурсов, определяемому пользователем, если приложение, отправившее запрос, является узлом Microsoft R или RStudio. В противном случае возвращается пул ресурсов по умолчанию.  
  
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
  
3.  После создания функции перенастройте группу ресурсов, чтобы назначить новую функцию классификации внешней группе ресурсов, определенной ранее.  
  
    ```  
    ALTER RESOURCE GOVERNOR WITH  (classifier_function = dbo.is_ds_apps);  
    ALTER RESOURCE GOVERNOR WITH reconfigure;  
    go  
    ```  
  
## <a name="verify-new-resource-pools-and-affinity"></a>Проверка новых пулов ресурсов и сопоставления  
  
1.  Чтобы убедиться, что изменения применены, проверьте конфигурацию памяти сервера и ЦП для каждой группы рабочей нагрузки, связанной со всеми пулами ресурсов экземпляра: пул по умолчанию для сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], пул ресурсов по умолчанию для внешних процессов и пул для внешних процессов, определяемый пользователем.  
  
    ```  
    SELECT * FROM sys.resource_governor_workload_groups;  
    ```  

    **Результаты**

    |group_id|имя|importance|request_max_memory_grant_percent|request_max_cpu_time_sec|request_memory_grant_timeout_sec|max_dop|group_max_requests pool_id|pool_idd|external_pool_idd|  
    |-|-|-|-|-|-|-|-|-|-|  
    |1|Внутренние|Средний|25|0|0|0|0|1|2|  
    |2|значение по умолчанию|Средний|25|0|0|0|0|2|2|  
    |256|ds_wg|Средний|25|0|0|0|0|2|256|  
  
2.  Чтобы просмотреть все внешние пулы ресурсов, можно использовать новое представление каталога [sys.resource_governor_external_resource_pools (Transact-SQL)](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md).  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pools;  
    ```  
    **Результаты**
    
    |external_pool_id|имя|max_cpu_percent|max_memory_percent|max_processes|version|  
    |-|-|-|-|-|-|  
    |2|значение по умолчанию|100|20|0|2|  
    |256|ds_ep|100|40|0|1|  
  
     Дополнительные сведения см. в статье [Resource Governor Catalog Views (Transact-SQL)](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md) (Представления каталога регулятора ресурсов (Transact-SQL)).  
  
3.  Следующая инструкция возвращает сведения о ресурсах компьютеров, сопоставленных с внешним пулом ресурсов.  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pool_affinity;  
    ```  
  
     Так как пулы были созданы со сходством AUTO, сведения не будут отображаться. Дополнительные сведения см. в статье о [представлении sys.dm_resource_governor_resource_pool_affinity (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [Регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)   
 [Управление ресурсами для служб R](../../advanced-analytics/r-services/resource-governance-for-r-services.md)  
  
  

