---
title: ALTER EXTERNAL RESOURCE POOL (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 11/13/2017
ms.prod: sql
ms.prod_service: sql-database
ms.service: ''
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ALTER_EXTERNAL_RESOURCE_POOL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER EXTERNAL RESOURCE POOL statement
ms.assetid: 634c327d-971b-49ba-b8a2-e243a04040db
caps.latest.revision: 10
author: jeannt
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a0e15c7848fd7c91f48b4ef9e73c134980eaff54
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="alter-external-resource-pool-transact-sql"></a>ALTER EXTERNAL RESOURCE POOL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**Применимо к:** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] и [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Изменяет внешний пул Resource Governor, указывающий ресурсы, которые могут использоваться внешними процессами. 

+ Для [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] в [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] внешний пул управляет `rterm.exe`, `BxlServer.exe` и другими сформированными процессами.

+ Для [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] в SQL Server 2017 внешний пул управляет процессами R для предыдущей версии, а также `python.exe`, `BxlServer.exe` и другими сформированными процессами.

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="syntax"></a>Синтаксис

```sql
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

{ *pool_name* | "default" }  
Имя существующего определяемого пользователем внешнего пула ресурсов или внешнего пула ресурсов по умолчанию, создаваемого при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
Если слово "default" используется с инструкцией `ALTER EXTERNAL RESOURCE POOL`, оно должно быть заключено в кавычки ("") или квадратные скобки ([]) во избежание конфликта с системным зарезервированным словом `DEFAULT`.


MAX_CPU_PERCENT =*value*  
Указывает максимальную среднюю пропускную способность ЦП для всех запросов во внешнем пуле ресурсов при возникновении состязания за ресурсы ЦП. *value* имеет тип integer и значение по умолчанию 100. Диапазон допустимых значений для *value* — от 1 до 100.


AFFINITY {CPU = AUTO | ( \<CPU_range_spec> ) | NUMANODE = (\<NUMA_node_range_spec>)}  
Подключает внешний пул ресурсов к конкретным ЦП. Значение по умолчанию — AUTO.

AFFINITY CPU = **(** \<CPU_range_spec> **)** сопоставляет внешний пул ресурсов с ЦП [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], определенными с помощью CPU_IDs. При использовании AFFINITY NUMANODE = **(** \<NUMA_node_range_spec> **)** внешний пул ресурсов сопоставляется с физическими процессорами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], соответствующими данному узлу NUMA или диапазону узлов.


MAX_MEMORY_PERCENT =*value*  
Указывает общий объем памяти сервера, который может использоваться для запросов в данном внешнем пуле ресурсов. *value* имеет тип integer и значение по умолчанию 100. Диапазон допустимых значений для *value* — от 1 до 100.


MAX_PROCESSES =*value*  
Указывает максимально допустимое количество процессов для внешнего пула ресурсов. Укажите 0, чтобы задать неограниченный порог для пула, который впоследствии ограничивается только ресурсами компьютера. Значение по умолчанию равно 0.

## <a name="remarks"></a>Remarks

[!INCLUDE[ssDE](../../includes/ssde-md.md)] реализует пул ресурсов при выполнении инструкции [ALTER RESOURCE GOVERNOR RECONFIGURE](../../t-sql/statements/alter-resource-governor-transact-sql.md).

Общие сведения о пулах ресурсов см. в разделах [Пул ресурсов Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md), [sys.resource_governor_external_resource_pools (Transact-SQL)](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md) и [sys.dm_resource_governor_external_resource_pool_affinity (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md).  

Сведения об использовании внешних пулов ресурсов для управления заданиями машинного обучения см. в статье [Resource governance for machine learning in SQL Server](../../advanced-analytics/r/resource-governance-for-r-services.md) (Управление ресурсами для машинного обучения в SQL Server).
## <a name="permissions"></a>Разрешения

Требуется разрешение `CONTROL SERVER`.

## <a name="examples"></a>Примеры

Следующая инструкция изменяет внешний пул, ограничивая загрузку ЦП 50 процентами, а максимальный объем памяти — 25 процентами доступной памяти на компьютере.
  
```sql
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

## <a name="see-also"></a>См. также раздел

[Управление ресурсами для машинного обучения в SQL Server](../../advanced-analytics/r/resource-governance-for-r-services.md)

[Параметр конфигурации сервера «external scripts enabled»](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)

[DROP EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/drop-external-resource-pool-transact-sql.md)

[ALTER RESOURCE POOL (Transact-SQL)](../../t-sql/statements/alter-resource-pool-transact-sql.md)

[CREATE WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/create-workload-group-transact-sql.md)

[Пул ресурсов регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-resource-pool.md)

[ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md) 
