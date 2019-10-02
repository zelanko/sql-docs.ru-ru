---
title: Создание пула ресурсов для Python и R
description: Узнайте, как создать и использовать пул ресурсов для управления рабочими нагрузками Python и R в SQL Server Службы машинного обучения.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/01/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8e8c48665c2928a0c8133892cc0029b4bd82c4cc
ms.sourcegitcommit: fd3e81c55745da5497858abccf8e1f26e3a7ea7d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2019
ms.locfileid: "71714328"
---
# <a name="create-a-resource-pool-for-sql-server-machine-learning-services"></a>Создание пула ресурсов для SQL Server Службы машинного обучения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Узнайте, как создать и использовать пул ресурсов для управления рабочими нагрузками Python и R в SQL Server Службы машинного обучения. 

Процесс включает несколько шагов:

1. Проверьте состояние всех существующих пулов ресурсов. Важно понимать, какие службы используют существующие ресурсы.
2. Изменение пулов ресурсов сервера.
3. Создание нового пула ресурсов для внешних процессов.
4. Создание функции классификации для обнаружения запросов внешних скриптов.
5. Убедитесь, что новый внешний пул ресурсов записывает задания R или Python от указанных клиентов или учетных записей.

<a name="bkmk_ReviewStatus"></a>

##  <a name="review-the-status-of-existing-resource-pools"></a>Проверка состояния существующих пулов ресурсов
  
1.  Используйте следующую инструкцию, чтобы проверить ресурсы, выделенные пулу по умолчанию для сервера.
  
    ```sql
    SELECT * FROM sys.resource_governor_resource_pools WHERE name = 'default'
    ```

    **Примеры результатов**

    |pool_id|name|min_cpu_percent|max_cpu_percent|min_memory_percent|max_memory_percent|cap_cpu_percent|min_iops_per_volume|max_iops_per_volume|
    |-|-|-|-|-|-|-|-|-|
    |2|значение по умолчанию|0|100|0|100|100|0|0|

2.  Проверьте ресурсы, выделенные **внешнему** пулу ресурсов по умолчанию.
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pools WHERE name = 'default'
    ```

    **Примеры результатов**

    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|version|
    |-|-|-|-|-|-|
    |2|значение по умолчанию|100|20|0|2|
 
3.  При использовании этих параметров сервера по умолчанию внешняя среда выполнения, вероятно, не будет иметь достаточных ресурсов для выполнения большинства задач. Чтобы избежать этого, необходимо изменить параметры использования ресурсов сервера следующим образом:
  
    -   Уменьшите максимальный объем памяти компьютера, который может использоваться ядром СУБД.
  
    -   Увеличьте максимальный объем памяти компьютера, который может использоваться внешним процессом.

## <a name="modify-server-resource-usage"></a>Изменение использования ресурсов сервера

1.  В [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] выполните следующую инструкцию, чтобы ограничить объем используемой сервером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] памяти, задав для параметра максимальной памяти сервера значение **60 %** .

    ```sql
    ALTER RESOURCE POOL "default" WITH (max_memory_percent = 60);
    ```
  
2.  Аналогично выполните следующую инструкцию, чтобы ограничить использование памяти внешними процессами до **40 %** общих ресурсов компьютера.
  
    ```sql
    ALTER EXTERNAL RESOURCE POOL "default" WITH (max_memory_percent = 40);
    ```
  
3.  Чтобы применить эти изменения, необходимо перенастроить и перезапустить регулятор ресурсов следующим образом:
  
    ```sql
    ALTER RESOURCE GOVERNOR RECONFIGURE;
    ```
  
    > [!NOTE]
    >  Это только Рекомендуемые параметры, которые следует начинать с; для определения правильного баланса среды и рабочей нагрузки следует оценивать задачи машинного обучения в свете других серверных процессов.

## <a name="create-a-user-defined-external-resource-pool"></a>Создание внешнего пула ресурсов, определяемого пользователем
  
1.  Любые изменения конфигурации регулятора ресурсов применяются для сервера в целом и влияют на рабочие нагрузки, использующие пулы по умолчанию для сервера, а также на рабочие нагрузки, использующие внешние пулы.
  
     Таким образом, чтобы обеспечить более точный контроль над тем, какие рабочие нагрузки должны иметь приоритет, можно создать новый внешний пул ресурсов, определяемый пользователем. Необходимо также определить функцию классификации и присвоить ее пулу внешних ресурсов. Ключевое слово **External** — New.
  
     Начните с создания нового *внешнего пула ресурсов, определяемого пользователем*. В следующем примере пулу присваивается имя **ds_ep**.
  
    ```sql
    CREATE EXTERNAL RESOURCE POOL ds_ep WITH (max_memory_percent = 40);
    ```

2.  Создайте группу рабочей нагрузки с именем `ds_wg`, которая будет использоваться для управления запросами сеанса. Для SQL-запросов будет использоваться пул по умолчанию. Для всех запросов внешних процессов будет использоваться пул `ds_ep`.
  
    ```sql
    CREATE WORKLOAD GROUP ds_wg WITH (importance = medium) USING "default", EXTERNAL "ds_ep";
    ```
  
     Запросы назначаются группе по умолчанию всякий раз, когда невозможно классифицировать запрос, или при любой другой ошибке классификации.
  
     Дополнительные сведения см. в статьях [Resource Governor Workload Group](../../relational-databases/resource-governor/resource-governor-workload-group.md) (Группа рабочей нагрузки регулятора ресурсов) и [CREATE WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/create-workload-group-transact-sql.md) (Инструкция CREATE WORKLOAD GROUP (Transact-SQL)).
  
## <a name="create-a-classification-function-for-machine-learning"></a>Создание функции классификации для машинного обучения
  
Функция классификации проверяет входящие задачи и определяет, можно ли выполнить задачу в текущем пуле ресурсов. Задачи, которые не отвечают критериям функции классификации, назначаются обратно в пул ресурсов по умолчанию на сервере.
  
1. Начните с указания того, что функция-классификатор должна использоваться Resource Governor для определения пулов ресурсов. Можно назначить **значение NULL** в качестве заполнителя для функции-классификатора.
  
    ```sql
    ALTER RESOURCE GOVERNOR WITH (classifier_function = NULL);
    ALTER RESOURCE GOVERNOR RECONFIGURE;
    ```
  
     Дополнительные сведения см. в разделе [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md).
  
2.  В функции-классификаторе для каждого пула ресурсов определите тип инструкций или входящих запросов, которые должны быть назначены пулу ресурсов.
  
     Например, следующая функция возвращает имя схемы, назначенной внешнему пулу ресурсов, определяемому пользователем, если приложение, отправившее запрос, является узлом Microsoft R или RStudio. В противном случае возвращается пул ресурсов по умолчанию.
  
    ```sql
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
  
    ```sql
    ALTER RESOURCE GOVERNOR WITH  (classifier_function = dbo.is_ds_apps);
    ALTER RESOURCE GOVERNOR WITH reconfigure;
    GO
    ```

## <a name="verify-new-resource-pools-and-affinity"></a>Проверка новых пулов ресурсов и сопоставления

Чтобы убедиться в том, что изменения внесены, следует проверить конфигурацию памяти сервера и ЦП для каждой группы рабочей нагрузки, связанной с этими пулами ресурсов.

+ пул по умолчанию для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сервера
+ пул ресурсов по умолчанию для внешних процессов
+ определяемый пользователем пул для внешних процессов

1. Выполните следующую инструкцию, чтобы просмотреть все группы рабочей нагрузки:

    ```sql
    SELECT * FROM sys.resource_governor_workload_groups;
    ```

    **Примеры результатов**

    |group_id|name|importance|request_max_memory_grant_percent|request_max_cpu_time_sec|request_memory_grant_timeout_sec|max_dop|group_max_requests pool_id|pool_idd|external_pool_id|
    |-|-|-|-|-|-|-|-|-|-|
    |1|Внутренние|Средний|25|0|0|0|0|1|2|
    |2|значение по умолчанию|Средний|25|0|0|0|0|2|2|
    |256|ds_wg|Средний|25|0|0|0|0|2|256|
  
2.  Используйте новое представление каталога [sys. resource_governor_external_resource_pools &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)для просмотра всех внешних пулов ресурсов.
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pools;
    ```

    **Примеры результатов**
    
    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|version|
    |-|-|-|-|-|-|
    |2|значение по умолчанию|100|20|0|2|
    |256|ds_ep|100|40|0|1|
  
     Дополнительные сведения см. в статье [Resource Governor Catalog Views (Transact-SQL)](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md) (Представления каталога регулятора ресурсов (Transact-SQL)).
  
3.  Выполните следующую инструкцию, чтобы получить сведения о ресурсах компьютера, которые привязаны к внешнему пулу ресурсов (если применимо):
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pool_affinity;
    ```
  
     Так как пулы были созданы со сходством AUTO, сведения не будут отображаться. Дополнительные сведения см. в статье о [представлении sys.dm_resource_governor_resource_pool_affinity (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md).

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения об управлении ресурсами сервера см. в следующих статьях:

+ [Регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md) 
+ [Динамическое представление &#40;управления, связанное с Resource Governor TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)

Общие сведения о управлении ресурсами для машинного обучения см. в следующих статьях:

+ [Управление рабочими нагрузками Python и R с помощью Resource Governor в SQL Server Службы машинного обучения](resource-governor.md)
