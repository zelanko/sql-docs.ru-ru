---
title: Создание пула ресурсов для R и Python — службы машинного обучения SQL Server
description: Определите пул ресурсов SQL Server для процессов R или Python на экземпляр ядра СУБД SQL Server 2016 или SQL Server 2017.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: c0fcc673e61f2ee188b169a2d46f1da6a4ffd2df
ms.sourcegitcommit: 33712a0587c1cdc90de6dada88d727f8623efd11
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2018
ms.locfileid: "53596865"
---
# <a name="how-to-create-a-resource-pool-for-machine-learning-in-sql-server"></a>Создание пула ресурсов для машинного обучения в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается, как создать и использовать пул ресурсов специально для управления R и Python машины рабочих нагрузок обучения в SQL Server. Предполагается, что вы уже установлено и включено машинного обучения функции и необходимо перенастроить экземпляр, для поддержки более точного управления ресурсы, используемые внешнего процесса, например R или Python.

Этот процесс включает в себя несколько этапов:

1.  Просмотр состояния существующих пулов ресурсов. Очень важно, что вы понимаете, какие службы используются существующие ресурсы.
2.  Изменение пулов ресурсов сервера.
3.  Создайте новый пул ресурсов для внешних процессов.
4.  Создание функции классификации для идентификации запросов внешних скриптов.
5.  Убедитесь, что новый внешний пул ресурсов захватывающего заданий R или Python с указанным клиентов или учетных записей.

##  <a name="bkmk_ReviewStatus"></a> Просмотр состояния существующих пулов ресурсов
  
1.  Оператор следующего вида, чтобы проверить ресурсы, выделенные в пул по умолчанию для сервера.
  
    ```sql
    SELECT * FROM sys.resource_governor_resource_pools WHERE name = 'default'
    ```

    **Пример результатов**

    |pool_id|name|min_cpu_percent|max_cpu_percent|min_memory_percent|max_memory_percent|cap_cpu_percent|min_iops_per_volume|max_iops_per_volume|
    |-|-|-|-|-|-|-|-|-|
    |2|значение по умолчанию|0|100|0|100|100|0|0|

2.  Проверьте ресурсы, выделенные **внешнему** пулу ресурсов по умолчанию.
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pools WHERE name = 'default'
    ```

    **Пример результатов**

    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|version|
    |-|-|-|-|-|-|
    |2|значение по умолчанию|100|20|0|2|
 
3.  В разделе параметров сервера по умолчанию внешней среды выполнения, скорее всего, будет недостаточно ресурсов для выполнения большинства задач. Чтобы избежать этого, необходимо изменить параметры использования ресурсов сервера следующим образом:
  
    -   Уменьшите максимальный объем памяти компьютера, используется компонентом database engine.
  
    -   Увеличьте максимальный объем памяти компьютера, могут использоваться внешний процесс.

## <a name="modify-server-resource-usage"></a>Изменение использования ресурсов сервера

1.  В [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] выполните следующую инструкцию, чтобы ограничить объем используемой сервером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] памяти, задав для параметра максимальной памяти сервера значение **60 %**.

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
    >  Это базовые рекомендуемые параметры для запуска. следует оценить ваши задач машинного обучения в свете других серверных процессов, чтобы определить правильный баланс для среды и рабочей нагрузки.

## <a name="create-a-user-defined-external-resource-pool"></a>Создание внешнего пула ресурсов, определяемого пользователем
  
1.  Любые изменения конфигурации регулятора ресурсов применяются для сервера в целом и влияют на рабочие нагрузки, использующие пулы по умолчанию для сервера, а также на рабочие нагрузки, использующие внешние пулы.
  
     Таким образом, чтобы обеспечить более точный контроль над тем, какие рабочие нагрузки должны иметь приоритет, можно создать новый внешний пул ресурсов, определяемый пользователем. Необходимо также определить функцию классификации и присвоить ее пулу внешних ресурсов. **ВНЕШНИХ** ключевое слово является новой.
  
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
  
1. Начните с указания, что функция-классификатор должен использоваться регулятором ресурсов для определения пулов ресурсов. Вы можете назначить **null** как заполнитель для функции-классификатора.
  
    ```sql
    ALTER RESOURCE GOVERNOR WITH (classifier_function = NULL);
    ALTER RESOURCE GOVERNOR RECONFIGURE;
    ```
  
     Дополнительные сведения см. в разделе [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md).
  
2.  В функции-классификатора для каждого пула ресурсов определите тип инструкций или входящих запросов, которые должны быть назначены в пул ресурсов.
  
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

Чтобы убедиться, что были внесены изменения, следует проверить конфигурацию памяти сервера и ЦП для каждой группы рабочей нагрузки, связанные с этими пулами ресурсов экземпляра:

+ пул по умолчанию для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сервера
+ пул ресурсов по умолчанию для внешних процессов
+ определяемые пользователем пул для внешних процессов

1. Выполните следующую инструкцию, чтобы просмотреть все группы рабочей нагрузки:

    ```sql
    SELECT * FROM sys.resource_governor_workload_groups;
    ```

    **Пример результатов**

    |group_id|name|importance|request_max_memory_grant_percent|request_max_cpu_time_sec|request_memory_grant_timeout_sec|max_dop|group_max_requests pool_id|pool_idd|external_pool_id|
    |-|-|-|-|-|-|-|-|-|-|
    |1|Внутренние|Средний|25|0|0|0|0|1|2|
    |2|значение по умолчанию|Средний|25|0|0|0|0|2|2|
    |256|ds_wg|Средний|25|0|0|0|0|2|256|
  
2.  Использовать новые представления каталога [sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md), чтобы просмотреть все внешние пулы ресурсов.
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pools;
    ```

    **Пример результатов**
    
    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|version|
    |-|-|-|-|-|-|
    |2|значение по умолчанию|100|20|0|2|
    |256|ds_ep|100|40|0|1|
  
     Дополнительные сведения см. в статье [Resource Governor Catalog Views (Transact-SQL)](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md) (Представления каталога регулятора ресурсов (Transact-SQL)).
  
3.  Выполните следующую инструкцию, чтобы вернуть сведения о ресурсах компьютеров, которые привязываются к пулу внешних ресурсов, если применимо:
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pool_affinity;
    ```
  
     Так как пулы были созданы со сходством AUTO, сведения не будут отображаться. Дополнительные сведения см. в статье о [представлении sys.dm_resource_governor_resource_pool_affinity (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md).

## <a name="see-also"></a>См. также

Дополнительные сведения об управлении ресурсами сервера см. в разделе:

+  [Регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md) 
+ [Динамические административные представления, связанные с регулятора ресурсов &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)

Обзор ресурсами для машинного обучения см. в разделе:

+  [Управление ресурсами для служб машинного обучения](../../advanced-analytics/r/resource-governance-for-r-services.md)
