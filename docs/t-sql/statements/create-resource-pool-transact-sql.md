---
title: "СОЗДАТЬ ПУЛ РЕСУРСОВ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2017
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
- CREATE RESOURCE POOL
- RESOURCE POOL
- CREATE_RESOURCE_POOL_TSQL
- RESOURCE_POOL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE RESOURCE POOL
ms.assetid: 82712505-c6f9-4a65-a469-f029b5a2d6cd
caps.latest.revision: 42
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5c6f9a6ae8f0f869eb5ddd32c0189fcbaab198d3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-resource-pool-transact-sql"></a>CREATE RESOURCE POOL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает пул ресурсов регулятора ресурсов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Пул ресурсов представляет подмножество физических ресурсов (память, процессоры и ввод-вывод) экземпляра компонента Database Engine. Регулятор ресурсов позволяет администратору базы данных распределять ресурсы сервера по пулам ресурсов, используя до 64 пулов. Регулятор ресурсов доступен не во всех выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CREATE RESOURCE POOL pool_name  
[ WITH  
    (  
        [ MIN_CPU_PERCENT = value ]  
        [ [ , ] MAX_CPU_PERCENT = value ]   
        [ [ , ] CAP_CPU_PERCENT = value ]   
        [ [ , ] AFFINITY {SCHEDULER =  
                  AUTO 
                | ( <scheduler_range_spec> )   
                | NUMANODE = ( <NUMA_node_range_spec> )
                } ]   
        [ [ , ] MIN_MEMORY_PERCENT = value ]  
        [ [ , ] MAX_MEMORY_PERCENT = value ]  
        [ [ , ] MIN_IOPS_PER_VOLUME = value ]  
        [ [ , ] MAX_IOPS_PER_VOLUME = value ]  
    )   
]  
[;]  
  
<scheduler_range_spec> ::=  
{ SCHED_ID | SCHED_ID TO SCHED_ID }[,…n]  
  
<NUMA_node_range_spec> ::=  
{ NUMA_node_ID | NUMA_node_ID TO NUMA_node_ID }[,…n]  
```  
  
## <a name="arguments"></a>Аргументы  
 *pool_name*  
 Определяемое пользователем имя для пула ресурсов. *pool_name* является алфавитно-цифровым, может иметь длину до 128 символов, должны быть уникальными в рамках экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]и должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md).  
  
 MIN_CPU_PERCENT =*значение*  
 Указывает гарантированную среднюю пропускную способность ЦП для всех запросов в пуле ресурсов при возникновении состязания использования ЦП. *значение* представляет собой целое число, значение по умолчанию 0. Допустимые значения для *значение* — от 0 до 100.  
  
 MAX_CPU_PERCENT =*значение*  
 Указывает максимальную среднюю пропускную способность ЦП для всех запросов в пуле ресурсов при возникновении состязания использования ЦП. *значение* представляет собой целое число, значение по умолчанию 100. Допустимые значения для *значение* — от 1 до 100.  
  
 CAP_CPU_PERCENT =*значение*  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Задает жесткое ограничение пропускной способности ЦП, которая предоставляется всем запросам в пуле ресурсов. Ограничивает максимальный уровень пропускной способности ЦП заданным значением. *значение* представляет собой целое число, значение по умолчанию 100. Допустимые значения для *значение* — от 1 до 100.  
  
 СОПОСТАВЛЕНИЕ {ПЛАНИРОВЩИКА = AUTO | ( \<scheduler_range_spec >) | NUMANODE = (\<NUMA_node_range_spec >)} **применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Подключает пул ресурсов к заданным планировщикам. Значение по умолчанию — AUTO.  
  
 AFFINITY SCHEDULER = **(** \<scheduler_range_spec > **)** сопоставляет пул ресурсов для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] расписания, определяемые заданными идентификаторами. Эти идентификаторы сопоставляются со значениями в столбце scheduler_id из [sys.dm_os_schedulers &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md). 
  
 При использовании AFFINITY NUMANODE = **(** \<NUMA_node_range_spec > **)**, пул ресурсов сопоставляется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] планировщиками, которые сопоставляются с физическими процессорами, соответствующими данному узлу NUMA или диапазону узлов. Вы можете использовать следующий запрос [!INCLUDE[tsql](../../includes/tsql-md.md)] для обнаружения сопоставления между конфигурацией физического узла NUMA и идентификаторами планировщиков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 
  
```  
SELECT osn.memory_node_id AS [numa_node_id], sc.cpu_id, sc.scheduler_id  
FROM sys.dm_os_nodes AS osn  
INNER JOIN sys.dm_os_schedulers AS sc   
    ON osn.node_id = sc.parent_node_id   
    AND sc.scheduler_id < 1048576;  
```  
  
 MIN_MEMORY_PERCENT =*значение*  
 Указывает минимальный объем памяти, резервируемый для данного пула ресурсов, который не подлежит использованию совместно с другими пулами ресурсов. *значение* представляет собой целое число, значение по умолчанию 0 в разрешенный диапазон для *значение* — от 0 до 100.  
  
 MAX_MEMORY_PERCENT =*значение*  
 Указывает общий объем памяти сервера, который может использоваться для запросов в данном пуле ресурсов. *значение* представляет собой целое число, значение по умолчанию 100. Допустимые значения для *значение* — от 1 до 100.  
  
 MIN_IOPS_PER_VOLUME =*значение*  
 **Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Указывает минимальный объем операций ввода-вывода в секунду (IOPS) на дисковый том, который следует резервировать для пула ресурсов. Допустимые значения для *значение* — от 0 до 2 ^ 31-1 (2 147 483 647). Укажите значение 0, чтобы не указывать минимальный порог для пула. Значение по умолчанию равно 0.  
  
 MAX_IOPS_PER_VOLUME =*значение*  
 **Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Указывает максимальный объем операций ввода-вывода в секунду (IOPS) на дисковый том, при котором поддерживается пул ресурсов. Допустимые значения для *значение* — от 0 до 2 ^ 31-1 (2 147 483 647). Укажите значение 0, чтобы задать неограниченный порог для пула. Значение по умолчанию равно 0.  
  
 Если значение параметра MAX_IOPS_PER_VOLUME для пула установлено в 0, пул не регулируется вообще и может занять все IOPS в системе, даже если для остальных пулов задан параметр MIN_IOPS_PER_VOLUME. На этот случай рекомендуется устанавливать достаточно высокое значение MAX_IOPS_PER_VOLUME для этого пула (например, максимальное значение 2^31-1), если требуется, чтобы пул регулировался на ввод-вывод.  
  
## <a name="remarks"></a>Замечания  
 MIN_IOPS_PER_VOLUME и MAX_IOPS_PER_VOLUME определяют минимальное и максимальное значения для операций чтения или записи в секунду. Эти операции чтения или записи могут быть любого размера и не показывают минимальную или максимальную пропускную способность.  
  
 Значения MAX_CPU_PERCENT и MAX_MEMORY_PERCENT должны быть больше или равны значениям MIN_CPU_PERCENT и MIN_MEMORY_PERCENT соответственно.  
  
 CAP_CPU_PERCENT отличается от MAX_CPU_PERCENT, поскольку рабочие нагрузки, связанные с пулом, могут использовать ресурсы ЦП, превышающие значение MAX_CPU_PERCENT, если они доступны, но не могут использовать ресурсы, превышающие CAP_CPU_PERCENT.  
  
 Общий процент ЦП для каждого соответствующего компонента (планировщики или узлы NUMA) не должен превышать 100 %.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение CONTROL SERVER.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как создать пул ресурсов с именем `bigPool`. Для этого пула используются параметры по умолчанию регулятора ресурсов.  
  
```  
CREATE RESOURCE POOL bigPool;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
 В следующем примере `CAP_CPU_PERCENT` задает жесткое ограничение в 30%, а параметр `AFFINITY SCHEDULER` устанавливается равным диапазону от 0 до 63, от 128 до 191. 
  
**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
CREATE RESOURCE POOL PoolAdmin  
WITH (  
     MIN_CPU_PERCENT = 10,  
     MAX_CPU_PERCENT = 20,  
     CAP_CPU_PERCENT = 30,  
     AFFINITY SCHEDULER = (0 TO 63, 128 TO 191),  
     MIN_MEMORY_PERCENT = 5,  
     MAX_MEMORY_PERCENT = 15  
      );  
  
```  
  
 В следующем примере задается `MIN_IOPS_PER_VOLUME` для \<некоторое значение > и `MAX_IOPS_PER_VOLUME` для \<некоторое значение >. Эти значения управляют физическими операциями чтения и записи при вводе-выводе, доступными для пула ресурсов.  
  
**Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
CREATE RESOURCE POOL PoolAdmin  
WITH (  
    MIN_IOPS_PER_VOLUME = 20,  
    MAX_IOPS_PER_VOLUME = 100  
      );  
  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER RESOURCE POOL (Transact-SQL)](../../t-sql/statements/alter-resource-pool-transact-sql.md)   
 [DROP RESOURCE POOL (Transact-SQL)](../../t-sql/statements/drop-resource-pool-transact-sql.md)   
 [CREATE WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [ALTER WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [DROP WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md)   
 [Пул ресурсов регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [Создание пула ресурсов](../../relational-databases/resource-governor/create-a-resource-pool.md)  
  
  


