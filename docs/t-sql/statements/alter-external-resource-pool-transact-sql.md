---
title: "ИЗМЕНИТЬ внешний ПУЛ РЕСУРСОВ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_EXTERNAL_RESOURCE_POOL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER EXTERNAL RESOURCE POOL statement
ms.assetid: 634c327d-971b-49ba-b8a2-e243a04040db
caps.latest.revision: 10
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d85123a34de6dea6b76c1dd4ad8dc6af3117764d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-external-resource-pool-transact-sql"></a>ИЗМЕНИТЬ внешний ПУЛ РЕСУРСОВ (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Внешний пул регулятора ресурсов изменений, который был определен ресурсы для внешних процессов. Для служб R управляет внешний пул `rterm.exe`, `BxlServer.exe`и порожденных ими процессов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ALTER EXTERNAL RESOURCE POOL { pool_name | "default" }  
[ WITH (  
    [ MAX_CPU_PERCENT = value ]  
    [ [ , ] AFFINITY CPU =    
            {  
                AUTO   
              | ( <cpu_range_spec> )   
              | NUMANODE = (( <NUMA_node_id> )   
            } ]   
    [ [ , ] MAX_MEMORY_PERCENT = value ]  
    [ [ , ] MAX_PROCESSES = value ]   
    )   
]  
[ ; ]  
  
<CPU_range_spec> ::=    
{ CPU_ID | CPU_ID  TO CPU_ID } [ ,...n ]  
```  
  
## <a name="arguments"></a>Аргументы  
 { *pool_name* | «default»}  
 Имя существующего пула внешних ресурсов, определяемых пользователем или пул внешних ресурсов по умолчанию, создаваемой при [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлен.  
«default» должно быть заключено в кавычки ("») или квадратные скобки ([]) при использовании с `ALTER EXTERNAL RESOURCE POOL` во избежание конфликтов с `DEFAULT`, которой является системой зарезервированным словом.  
  
 MAX_CPU_PERCENT =*значение*  
 Указывает максимальную среднюю пропускную способность ЦП для всех запросов в внешний пул ресурсов при возникновении состязания использования ЦП. *значение* представляет собой целое число, значение по умолчанию 100. Допустимые значения для *значение* — от 1 до 100.  
  
СОПОСТАВЛЕНИЕ {ЦП = AUTO | ( \<CPU_range_spec >) | NUMANODE = (\<NUMA_node_range_spec >)} присоединить внешний пул ресурсов ЦП. Значение по умолчанию — AUTO.  
  
СХОДСТВО ЦП = **(** \<CPU_range_spec > **)** сопоставляет внешний пул ресурсов для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяется данного CPU_IDs ЦП.
  
При использовании AFFINITY NUMANODE = **(** \<NUMA_node_range_spec > **)**, сопоставляется внешний пул ресурсов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] физическими процессорами, соответствующими в данной архитектуре NUMA узел или диапазону узлов.
  
 MAX_MEMORY_PERCENT =*значение*  
 Указывает общий объем памяти сервера, можно использовать для запросов в этом внешнего пула ресурсов. *значение* представляет собой целое число, значение по умолчанию 100. Допустимые значения для *значение* — от 1 до 100.  
  
 MAX_PROCESSES =*значение*  
 Указывает максимальное количество процессов, разрешенного для внешнего пула ресурсов. Укажите 0, чтобы задать неограниченный порог для пула, который будет привязан только быть ресурсов компьютера. Значение по умолчанию равно 0.  
  
## <a name="remarks"></a>Замечания  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Реализует пул ресурсов при выполнении [ALTER RESOURCE GOVERNOR RECONFIGURE](../../t-sql/statements/alter-resource-governor-transact-sql.md) инструкции.  
  
 Дополнительные сведения о пулах ресурсов см. в разделе [пул ресурсов регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-resource-pool.md), [sys.resource_governor_external_resource_pools &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md), и [sys.dm_resource_governor_external_resource_pool_affinity &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Требуется разрешение `CONTROL SERVER`  
  
## <a name="examples"></a>Примеры  
 Следующая инструкция изменяет внешний пул ограничением ЦП на 50 процентов, а также максимальный объем памяти на 25 процентов доступной памяти на компьютере.  
  
```  
ALTER EXTERNAL RESOURCE POOL ep_1  
WITH (  
    MAX_CPU_PERCENT = 50  
    , AFFINITY CPU = AUTO  
    , MAX_MEMORY_PERCENT = 25  
);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Параметр конфигурации сервера External scripts enabled](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
 [Службы R SQL Server](../../advanced-analytics/r-services/sql-server-r-services.md)   
 [Известные проблемы для SQL Server R Services](../../advanced-analytics/r-services/known-issues-for-sql-server-r-services.md)   
 [CREATE EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/create-external-resource-pool-transact-sql.md)   
 [DROP EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/drop-external-resource-pool-transact-sql.md)   
 [ALTER RESOURCE POOL (Transact-SQL)](../../t-sql/statements/alter-resource-pool-transact-sql.md)   
 [CREATE WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [Пул ресурсов регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  

