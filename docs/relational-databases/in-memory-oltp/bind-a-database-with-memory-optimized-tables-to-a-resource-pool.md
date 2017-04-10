---
title: "привязать базу данных с таблицами, оптимизированными для памяти, к пулу ресурсов | Microsoft Docs"
ms.custom: ""
ms.date: "08/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f222b1d5-d2fa-4269-8294-4575a0e78636
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# привязать базу данных с таблицами, оптимизированными для памяти, к пулу ресурсов
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Пул ресурсов представляет подмножество физических ресурсов, доступных для управления. По умолчанию базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] привязываются к пулу и потребляют ресурсы пула по умолчанию. Чтобы защитить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] от использования его ресурсов одной или несколькими оптимизированными для памяти таблицами, а также чтобы другие потребители не занимали память, необходимую таким таблицам, рекомендуется создать отдельный пул ресурсов для управления использованием памяти для базы данных с оптимизированными для памяти таблицами.  
  
 Базу данных можно привязать только к одному пулу ресурсов. Однако можно привязать несколько баз данных к одному и тому же пулу. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет привязать базу данных без таблиц, оптимизированных для памяти, к пулу ресурсов, однако это не даст результата. Может потребоваться привязка базы данных к указанному пулу ресурсов, если в будущем потребуется создание в базе данных оптимизированных для памяти таблиц.  
  
 Прежде чем создавать привязку базы данных к пулу ресурсов, как база данных, так и пул ресурсов должны существовать. Привязка вступит в силу при следующем переводе базы данных в режим «в сети». Дополнительные сведения см. в разделе [Состояния базы данных](../../relational-databases/databases/database-states.md).  
  
 Сведения о пулах ресурсов см. в разделе [Пул ресурсов регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-resource-pool.md).  
  
## Шаги для привязки базы данных к пулу ресурсов  
  
1.  [Создайте базу данных и пул ресурсов](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_CreatePool)  
  
    1.  [Создайте базу данных](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_CreateDatabase)  
  
    2.  [Определение минимального значения для MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_DeterminePercent)  
  
    3.  [Создайте новый пул ресурсов и настройте память.](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_CreateResourcePool)  
  
2.  [Привязка базы данных к пулу](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_DefineBinding)  
  
3.  [Подтвердите привязку](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_ConfirmBinding)  
  
4.  [Сделайте привязку эффективной](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_MakeBindingEffective)  
  
 Другое содержимое этого раздела  
  
-   [Измените параметры MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT для существующего пула](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_ChangeAllocation)  
  
-   [Процент доступной памяти для оптимизированных для памяти таблиц и индексов](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_PercentAvailable)  
  
##  <a name="bkmk_CreatePool"></a> Создайте базу данных и пул ресурсов  
 Можно создать базу данных и пул ресурсов в любом порядке. Важно, чтобы база данных и пул ресурсов существовали еще до привязки.  
  
###  <a name="bkmk_CreateDatabase"></a> Создайте базу данных  
 Следующая инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] создает базу данных с именем IMOLTP_DB, которая будет содержать одну или несколько таблиц, оптимизированных для памяти. Путь \<driveAndPath> должен существовать до выполнения этой команды.  
  
```tsql  
CREATE DATABASE IMOLTP_DB  
GO  
ALTER DATABASE IMOLTP_DB ADD FILEGROUP IMOLTP_DB_fg CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE IMOLTP_DB ADD FILE( NAME = 'IMOLTP_DB_fg' , FILENAME = 'c:\data\IMOLTP_DB_fg') TO FILEGROUP IMOLTP_DB_fg;  
GO  
```  
  
###  <a name="bkmk_DeterminePercent"></a> Определение минимального значения для MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT  
 После определения потребностей в памяти для оптимизированных для памяти таблиц нужно определить, какой процент доступной памяти требуется, и задать в процентах это значение или выше.  
  
 **Пример**   
В этом примере предполагается, что согласно вычислениям для оптимизированных для памяти таблиц и индексов требуется 16 ГБ памяти. Предположим, доступно 32 ГБ памяти.  
  
 На первый взгляд может показаться, что для MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT нужно задать значение 50 (16 — это 50 % от 32).  Но в этом случае оптимизированные для памяти таблицы не получат достаточного объема памяти. В приведенной ниже таблице ([Процент доступной памяти для оптимизированных для памяти таблиц и индексов](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_PercentAvailable)) видно, что при наличии 32 ГБ выделенной памяти только 80 % доступно для оптимизированных для памяти таблиц и индексов.  Поэтому следует вычислять минимальный и максимальный процент исходя из доступной памяти, а не общей.  
  
 `memoryNeedeed = 16`   
 `memoryCommitted = 32`   
 `availablePercent = 0.8`   
 `memoryAvailable = memoryCommitted * availablePercent`   
 `percentNeeded = memoryNeeded / memoryAvailable`  
  
 Использование реальных чисел:   
`percentNeeded = 16 / (32 * 0.8) = 16 / 25.6 = 0.625`  
  
 Таким образом, необходимо по крайней мере 62,5 % доступной памяти, чтобы уложиться в требование 16 ГБ для оптимизированных для памяти таблиц и индексов.  Поскольку значения MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT должны быть целыми числами, рекомендуется задать для них значение не менее 63 %.  
  
###  <a name="bkmk_CreateResourcePool"></a> Создайте новый пул ресурсов и настройте память.  
 При настройке памяти для таблиц, оптимизированных для памяти, планирование загрузки следует выполнять на основе MIN_MEMORY_PERCENT, но не MAX_MEMORY_PERCENT.  Сведения о MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT см. в разделе [ALTER RESOURCE POOL (Transact-SQL)](../../t-sql/statements/alter-resource-pool-transact-sql.md). Это повышает прогнозируемую доступность памяти для таблиц, оптимизированных для памяти, так как использование MIN_MEMORY_PERCENT повышает нагрузку на другие пулы ресурсов, чтобы добиться выделения памяти. Чтобы обеспечить доступность памяти и избежать ее нехватки, значения MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT должны быть одинаковыми. В разделе [Процент доступной памяти для оптимизированных для памяти таблиц и индексов](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_PercentAvailable) ниже процент доступной памяти для таблиц, оптимизированных для памяти, основан на объеме выделенной памяти.  
  
 Дополнительные сведения см. в разделе [Использование In-Memory OLTP в среде ВМ](../Topic/Using%20In-Memory%20OLTP%20in%20a%20VM%20Environment.md).  
  
 Следующий код [!INCLUDE[tsql](../../includes/tsql-md.md)] создает пул ресурсов с именем Pool_IMOLTP, в котором для использования будет доступно 50 % памяти.  После создания пула регулятор ресурсов настраивается для включения Pool_IMOLTP.  
  
```tsql  
-- set MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT to the same value  
CREATE RESOURCE POOL Pool_IMOLTP   
  WITH   
    ( MIN_MEMORY_PERCENT = 63,   
    MAX_MEMORY_PERCENT = 63 );  
GO  
  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
##  <a name="bkmk_DefineBinding"></a> Привязка базы данных к пулу  
 Используйте системную функцию `sp_xtp_bind_db_resource_pool`, чтобы привязать базу данных к пулу ресурсов. Эта функция принимает два параметра: имя базы данных и имя пула ресурсов.  
  
 Следующий код [!INCLUDE[tsql](../../includes/tsql-md.md)] определяет привязку базы данных IMOLTP_DB к пулу ресурсов Pool_IMOLTP. Привязка не вступит в силу до тех пор, пока база данных не будет переведена в режим запуска.  
  
```tsql  
EXEC sp_xtp_bind_db_resource_pool 'IMOLTP_DB', 'Pool_IMOLTP'  
GO  
```  
  
 Системная функция sp_xtp_bind_db_resourece_pool принимает два строковых параметра: database_name и pool_name.  
  
##  <a name="bkmk_ConfirmBinding"></a> Подтвердите привязку  
 Подтвердите привязку, указав идентификатор пула ресурсов для IMOLTP_DB. Он не должен принимать значение NULL.  
  
```tsql  
SELECT d.database_id, d.name, d.resource_pool_id  
FROM sys.databases d  
GO  
```  
  
##  <a name="bkmk_MakeBindingEffective"></a> Сделайте привязку эффективной  
 Необходимо вывести базу данных из сети, а затем снова вернуть в сеть после ее привязки к пулу ресурсов, чтобы привязка вступила в силу. Если база данных была ранее привязана к другому пулу, то перезапуск базы данных удаляет выделенную память из предыдущего пула ресурсов, после этого память будет выделяться для оптимизированных для памяти таблиц и индексов пула ресурсов, только что привязанного к базе данных.  
  
```tsql  
USE master  
GO  
  
ALTER DATABASE IMOLTP_DB SET OFFLINE  
GO  
ALTER DATABASE IMOLTP_DB SET ONLINE  
GO  
  
USE IMOLTP_DB  
GO  
```  
  
 Теперь база данных будет привязана к пулу ресурсов.  
  
##  <a name="bkmk_ChangeAllocation"></a> Измените параметры MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT для существующего пула  
 Если на сервере увеличилась дополнительная память либо если изменился объем памяти, необходимый оптимизированным для памяти таблицам, может потребоваться изменить значения MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT. Следующие шаги показывают, как изменить значение MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT в пуле ресурсов. Инструкции по использованию значений для MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT см. ниже.  Дополнительные сведения см. в статье [Использование In-Memory OLTP в среде ВМ](../Topic/Using%20In-Memory%20OLTP%20in%20a%20VM%20Environment.md).  
  
1.  Используйте `ALTER RESOURCE POOL`, чтобы изменить значение как MIN_MEMORY_PERCENT, так и MAX_MEMORY_PERCENT.  
  
2.  Используйте `ALTER RESURCE GOVERNOR`, чтобы настроить регулятор ресурсов с новыми значениями.  
  
 **Образец кода**  
  
```tsql  
ALTER RESOURCE POOL Pool_IMOLTP  
WITH  
     ( MIN_MEMORY_PERCENT = 70,  
       MAX_MEMORY_PERCENT = 70 )   
GO  
  
-- reconfigure the Resource Governor  
ALTER RESOURCE GOVERNOR RECONFIGURE  
GO  
```  
  
##  <a name="bkmk_PercentAvailable"></a> Процент доступной памяти для оптимизированных для памяти таблиц и индексов  
 Если база данных, в которой есть оптимизированные для памяти таблицы, и рабочая нагрузка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сопоставлены с одним и тем же пулом ресурсов, регулятор ресурсов задает внутренний порог для использования служб [!INCLUDE[hek_2](../../includes/hek-2-md.md)], чтобы пользователи пула не имели конфликтов при его использовании. В целом, порог для использования [!INCLUDE[hek_2](../../includes/hek-2-md.md)] составляет 80 % из пула. В следующей таблице показаны фактические пороговые значения для разного размера памяти.  
  
 При создании выделенного пула ресурсов для базы данных [!INCLUDE[hek_2](../../includes/hek-2-md.md)] необходимо оценить объем физической памяти, который потребуется для таблиц в памяти после учета версий строк и роста объема данных. Когда потребуется оценка памяти, необходимо создать пул ресурсов с частью памяти целевого объема для экземпляра SQL, который показан в столбце committed_target_kb в динамическом административном представлении `sys.dm_os_sys_info` (см. [sys.dm_os_sys_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)). Например, можно создать пул ресурсов P1 с 40 % от общего объема памяти, доступного для экземпляра. Из этих 40 % модуль [!INCLUDE[hek_2](../../includes/hek-2-md.md)] получает малый процент для хранения данных [!INCLUDE[hek_2](../../includes/hek-2-md.md)].  Это необходимо для того, чтобы удостовериться, что [!INCLUDE[hek_2](../../includes/hek-2-md.md)] не использует всю память из этого пула.  Это значение меньшего процента зависит от целевого объема зафиксированной памяти. В следующей таблице показана память, доступная в пуле ресурсов (именованном или стандартном) для базы данных [!INCLUDE[hek_2](../../includes/hek-2-md.md)] до появлении ошибки нехватки памяти.  
  
|Память, выделенная в целевом режиме|Процент доступной памяти для таблиц|  
|-----------------------------|---------------------------------------------|  
|<= 8 ГБ|70 %|  
|<= 16 ГБ|75 %|  
|<= 32 ГБ|80 %|  
|\<= 96 ГБ|85 %|  
|>96 ГБ|90 %|  
  
 Например, если «целевая зафиксированная память» равна 100 ГБ, а по вашей оценке для таблиц и индексов, оптимизированных для памяти, требуется 60 ГБ, то можно создать пул ресурсов с параметром MAX_MEMORY_PERCENT = 67 (60 требуемых ГБ / 0,90 = 66,667 ГБ, после округления — 67 ГБ; 67 ГБ / 100 установленных ГБ = 67%), чтобы обеспечить нужный объем памяти объектам [!INCLUDE[hek_2](../../includes/hek-2-md.md)].  
  
 После привязки базы данных к указанному пулу ресурсов выполните следующий запрос, чтобы узнать объем выделенной памяти в разных пулах ресурсов.  
  
```tsql  
SELECT pool_id  
     , Name  
     , min_memory_percent  
     , max_memory_percent  
     , max_memory_kb/1024 AS max_memory_mb  
     , used_memory_kb/1024 AS used_memory_mb   
     , target_memory_kb/1024 AS target_memory_mb  
   FROM sys.dm_resource_governor_resource_pools  
```  
  
 Этот пример вывода показывает, что память, занятая оптимизированными для памяти объектами, равна 1356 МБ в пуле ресурсов PoolIMOLTP с верхней границей в 2307 МБ. Эта верхняя граница определяет общий объем памяти, который может быть занят пользовательскими и оптимизированными для памяти объектами, сопоставленными с этим пулом.  
  
 **Образец вывода**   
Этот вывод из базы данных и таблиц, созданных ранее.  
  
```  
pool_id     Name        min_memory_percent max_memory_percent max_memory_mb used_memory_mb target_memory_mb  
----------- ----------- ------------------ ------------------ ------------- -------------- ----------------   
1           internal    0                  100                3845          125            3845  
2           default     0                  100                3845          32             3845  
259         PoolIMOLTP 0                  100                3845          1356           2307  
```  
  
 Дополнительные сведения см. в разделе [sys.dm_resource_governor_resource_pools (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md).  
  
 Если не привязать базу данных к именованному пулу ресурсов, он привязывается к пулу ресурсов «default». Поскольку стандартный пул ресурсов используется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и при других операциях выделения памяти, вы не сможете отслеживать память, потребляемую таблицами, оптимизированными для памяти, в нужной базе данных с помощью динамического административного представления sys.dm_resource_governor_resource_pools.  
  
## См. также:  
 [sys.sp_xtp_bind_db_resource_pool (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql.md)   
 [sys.sp_xtp_unbind_db_resource_pool (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql.md)   
 [регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)   
 [Пул ресурсов регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [Создание пула ресурсов](../../relational-databases/resource-governor/create-a-resource-pool.md)   
 [Изменение параметров пула ресурсов](../../relational-databases/resource-governor/change-resource-pool-settings.md)   
 [Удаление пула ресурсов](../../relational-databases/resource-governor/delete-a-resource-pool.md)  
  
  