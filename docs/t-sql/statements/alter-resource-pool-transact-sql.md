---
title: "Инструкция ALTER RESOURCE POOL (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/01/2017
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
- ALTER_RESOURCE_POOL_TSQL
- ALTER RESOURCE POOL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER RESOURCE POOL
ms.assetid: 9c1c4cfb-0e3b-4f01-bf57-3fce94c7d1d4
caps.latest.revision: 47
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 662686f08e370f3d3ee4dee3211f28df58e3b171
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-resource-pool-transact-sql"></a>Инструкция ALTER RESOURCE POOL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет существующую конфигурацию пула ресурсов регулятора ресурсов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ALTER RESOURCE POOL { pool_name | "default" }  
[WITH  
    ( [ MIN_CPU_PERCENT = value ]  
    [ [ , ] MAX_CPU_PERCENT = value ]   
    [ [ , ] CAP_CPU_PERCENT = value ]   
    [ [ , ] AFFINITY {
                        SCHEDULER = AUTO 
                      | ( <scheduler_range_spec> ) 
                      | NUMANODE = ( <NUMA_node_range_spec> )
                      }]   
    [ [ , ] MIN_MEMORY_PERCENT = value ]  
    [ [ , ] MAX_MEMORY_PERCENT = value ]   
    [ [ , ] MIN_IOPS_PER_VOLUME = value ]  
    [ [ , ] MAX_IOPS_PER_VOLUME = value ]  
)]   
[;]  
  
<scheduler_range_spec> ::=  
{SCHED_ID | SCHED_ID TO SCHED_ID}[,…n]  
  
<NUMA_node_range_spec> ::=  
{NUMA_node_ID | NUMA_node_ID TO NUMA_node_ID}[,…n]  
```  
  
## <a name="arguments"></a>Аргументы  
 { *pool_name* | **«default»** }  
 Имя существующего определяемого пользователем пула ресурсов или пула ресурсов по умолчанию, создаваемого при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если слово "default" используется с инструкцией ALTER RESOURCE POOL, оно должно быть заключено в кавычки ("") или квадратные скобки ([]) во избежание конфликта с системным зарезервированным словом DEFAULT. Дополнительные сведения см. в разделе [Database Identifiers](../../relational-databases/databases/database-identifiers.md).  
  
> [!NOTE]  
>  В стандартных группах рабочей нагрузки и пулах ресурсов используются имена со строчными буквами, такие как «default». Это необходимо учитывать при работе с серверами, где параметры сортировки учитывают регистр символов. Серверы, параметры сортировки которых не учитывают регистр (например, SQL_Latin1_General_CP1_CI_AS), будут рассматривать строки «default» и «Default» как одинаковые.  
  
 MIN_CPU_PERCENT =*значение*  
 Указывает гарантированную среднюю пропускную способность ЦП для всех запросов в пуле ресурсов при возникновении состязания использования ЦП. *значение* представляет собой целое число, значение по умолчанию 0. Допустимые значения для *значение* — от 0 до 100.  
  
 MAX_CPU_PERCENT =*значение*  
 Указывает максимальную среднюю пропускную способность ЦП для всех запросов в пуле ресурсов при возникновении состязания за ресурсы ЦП. *значение* представляет собой целое число, значение по умолчанию 100. Допустимые значения для *значение* — от 1 до 100.  
  
 CAP_CPU_PERCENT =*значение*  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Указывает целевой максимальной емкости ЦП для запросов в пуле ресурсов. *значение* представляет собой целое число, значение по умолчанию 100. Допустимые значения для *значение* — от 1 до 100.  
  
> [!NOTE]  
>  Из-за статистической природы управления ЦП могут появиться случайные пики которых превышает значение, указанное в CAP_CPU_PERCENT.  
  
 AFFINITY {SCHEDULER = AUTO | (Scheduler_range_spec) | NUMANODE = (NUMA_node_range_spec)}  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Подключает пул ресурсов к заданным планировщикам. Значение по умолчанию — AUTO.  
  
 AFFINITY SCHEDULER = (Scheduler_range_spec) сопоставляет пул ресурсов с расписаниями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], обозначенными заданными идентификаторами. Эти идентификаторы сопоставляются со значениями в столбце scheduler_id из [sys.dm_os_schedulers &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md).  
  
 При использовании AFFINITY NAMANODE = (NUMA_node_range_spec) пул ресурсов приводится в соответствие с планировщиками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которые сопоставляются с физическими процессорами, соответствующими данному узлу NUMA или диапазону узлов. Вы можете использовать следующий запрос Transact-SQL для обнаружения сопоставления между конфигурацией физического узла NUMA и идентификаторами планировщиков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT osn.memory_node_id AS [numa_node_id], sc.cpu_id, sc.scheduler_id  
FROM sys.dm_os_nodes AS osn  
INNER JOIN sys.dm_os_schedulers AS sc 
   ON osn.node_id = sc.parent_node_id 
      AND sc.scheduler_id < 1048576;  
```  
  
 MIN_MEMORY_PERCENT =*значение*  
 Указывает минимальный объем памяти, резервируемый для данного пула ресурсов, который не подлежит использованию совместно с другими пулами ресурсов. *значение* представляет собой целое число, значение по умолчанию 0. Допустимые значения для *значение* — от 0 до 100.  
  
 MAX_MEMORY_PERCENT =*значение*  
 Указывает общий объем памяти сервера, который может использоваться для запросов в данном пуле ресурсов. *значение* представляет собой целое число, значение по умолчанию 100. Допустимые значения для *значение* — от 1 до 100.  
  
 MIN_IOPS_PER_VOLUME =*значение*  
 **Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Указывает минимальный объем операций ввода-вывода в секунду (IOPS) на дисковый том, который следует резервировать для пула ресурсов. Допустимые значения для *значение* — от 0 до 2 ^ 31-1 (2 147 483 647). Укажите значение 0, чтобы не указывать минимальный порог для пула.  
  
 MAX_IOPS_PER_VOLUME =*значение*  
 **Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Указывает максимальный объем операций ввода-вывода в секунду (IOPS) на дисковый том, при котором поддерживается пул ресурсов. Допустимые значения для *значение* — от 0 до 2 ^ 31-1 (2 147 483 647). Укажите значение 0, чтобы задать неограниченный порог для пула. Значение по умолчанию равно 0.  
  
 Если значение параметра MAX_IOPS_PER_VOLUME для пула установлено в 0, пул не регулируется вообще и может занять все IOPS в системе, даже если для остальных пулов задан параметр MIN_IOPS_PER_VOLUME. На этот случай рекомендуется устанавливать достаточно высокое значение MAX_IOPS_PER_VOLUME для этого пула (например, максимальное значение 2^31-1), если требуется, чтобы пул регулировался на ввод-вывод.  
  
## <a name="remarks"></a>Замечания  
 Значения MAX_CPU_PERCENT и MAX_MEMORY_PERCENT должны быть больше либо равны значениям MIN_CPU_PERCENT и MIN_MEMORY_PERCENT соответственно.  
  
 MAX_CPU_PERCENT могут использовать производительность ЦП выше значения MAX_CPU_PERCENT, если он доступен. Несмотря на то, что может быть пиковых значений выше CAP_CPU_PERCENT, рабочие нагрузки не должно превышать CAP_CPU_PERCENT течение продолжительного периода времени, даже если мощности ЦП Достаточно доступен.  
  
 Общий процент ЦП для каждого соответствующего компонента (планировщики или узлы NUMA) не должен превышать 100 %.  
  
 При выполнении инструкций DDL рекомендуется иметь представление о состояниях регулятора ресурсов. Дополнительные сведения см. в разделе [регулятора ресурсов](../../relational-databases/resource-governor/resource-governor.md).  
  
 При изменении плана влияет на параметр, новые параметры только вступят в силу в ранее кэшированных планов после выполнения инструкции DBCC FREEPROCCACHE (*pool_name*), где *pool_name* имя ресурса Пула ресурсов регулятора ресурсов.  
  
-   При изменении СОПОСТАВЛЕНИЕ из нескольких планировщиков один планировщик, выполнение инструкции DBCC FREEPROCCACHE не требуется, так как параллельные планы можно запустить в последовательном режиме. Тем не менее он может оказаться сравнимой план, созданный как последовательного плана.  
  
-   При изменении СХОДСТВА из одного планировщика для нескольких планировщиков, выполнение инструкции DBCC FREEPROCCACHE не требуется. Однако последовательных планов не может выполняться параллельно, поэтому Очистка кэша соответствующих позволит новые планы для потенциально могут компилироваться с помощью параллелизма.  
  
> [!CAUTION]  
>  Очистка кэшированных планов из пула ресурсов, который связан с более чем одной группы рабочей нагрузки будет влиять на все группы рабочей нагрузки с пулом ресурсов, определяемых пользователем, определяется *pool_name*.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение CONTROL SERVER.  
  
## <a name="examples"></a>Примеры  
 В следующем примере сохраняются все параметры по умолчанию для пула ресурсов `default`, за исключением `MAX_CPU_PERCENT`, значение которого изменяется на `25`.  
  
```  
ALTER RESOURCE POOL "default"  
WITH  
     ( MAX_CPU_PERCENT = 25);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
 В следующем примере `CAP_CPU_PERCENT` задает жесткое ограничение 80 %, а `AFFINITY SCHEDULER` получает отдельное значение 8 и диапазон от 12 до 16.  
  
**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
ALTER RESOURCE POOL Pool25  
WITH(   
     MIN_CPU_PERCENT = 5,  
     MAX_CPU_PERCENT = 10,       
     CAP_CPU_PERCENT = 80,  
     AFFINITY SCHEDULER = (8, 12 TO 16),   
     MIN_MEMORY_PERCENT = 5,  
     MAX_MEMORY_PERCENT = 15  
);  
  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)   
 [CREATE RESOURCE POOL (Transact-SQL)](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [DROP RESOURCE POOL (Transact-SQL)](../../t-sql/statements/drop-resource-pool-transact-sql.md)   
 [CREATE WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [ALTER WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [DROP WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  

