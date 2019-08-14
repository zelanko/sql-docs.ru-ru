---
title: ALTER EXTERNAL RESOURCE POOL (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/07/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: machine-learning
ms.topic: language-reference
f1_keywords:
- ALTER_EXTERNAL_RESOURCE_POOL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER EXTERNAL RESOURCE POOL statement
ms.assetid: 634c327d-971b-49ba-b8a2-e243a04040db
author: dphansen
ms.author: davidph
manager: cgronlund
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: ebab091b0e674339141c4ee2ea6d7c7993ccbabf
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893681"
---
# <a name="alter-external-resource-pool-transact-sql"></a>ALTER EXTERNAL RESOURCE POOL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

Изменяет внешний пул Resource Governor, указывающий ресурсы, которые могут использоваться внешними процессами. 

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Для [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] в [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] внешний пул управляет `rterm.exe`, `BxlServer.exe` и другими сформированными процессами.
::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
Для [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] внешний пул управляет `rterm.exe`, `python.exe`, `BxlServer.exe` и другими сформированными процессами.
::: moniker-end

![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

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

{ *pool_name* | "default" }  
Имя существующего определяемого пользователем внешнего пула ресурсов или внешнего пула ресурсов по умолчанию, создаваемого при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
Если слово "default" используется с инструкцией `ALTER EXTERNAL RESOURCE POOL`, оно должно быть заключено в кавычки ("") или квадратные скобки ([]) во избежание конфликта с системным зарезервированным словом `DEFAULT`.

MAX_CPU_PERCENT =*value*  
Указывает максимальную среднюю пропускную способность ЦП для всех запросов во внешнем пуле ресурсов при возникновении состязания за ресурсы ЦП. *value* — целое число. Диапазон допустимых значений для *value* — от 1 до 100.

AFFINITY {CPU = AUTO | ( \<CPU_range_spec> ) | NUMANODE = (\<NUMA_node_range_spec>)}  
Подключает внешний пул ресурсов к конкретным ЦП.

AFFINITY CPU = **(** \<CPU_range_spec> **)** сопоставляет внешний пул ресурсов с ЦП [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], определенными с помощью CPU_IDs. При использовании AFFINITY NUMANODE = **(** \<NUMA_node_range_spec> **)** внешний пул ресурсов сопоставляется с физическими процессорами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], соответствующими данному узлу NUMA или диапазону узлов.

MAX_MEMORY_PERCENT =*value*  
Указывает общий объем памяти сервера, который может использоваться для запросов в данном внешнем пуле ресурсов. *value* — целое число. Диапазон допустимых значений для *value* — от 1 до 100.

MAX_PROCESSES =*value*  
Указывает максимально допустимое количество процессов для внешнего пула ресурсов. Укажите 0, чтобы задать неограниченный порог для пула, который впоследствии ограничивается только ресурсами компьютера.

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

+ [Управление ресурсами для машинного обучения в SQL Server](../../advanced-analytics/r/resource-governance-for-r-services.md)
+ [Параметр конфигурации сервера «external scripts enabled»](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)
+ [CREATE EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/create-external-resource-pool-transact-sql.md)
+ [DROP EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/drop-external-resource-pool-transact-sql.md)
+ [ALTER RESOURCE POOL (Transact-SQL)](../../t-sql/statements/alter-resource-pool-transact-sql.md)
+ [CREATE WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/create-workload-group-transact-sql.md)
+ [Пул ресурсов регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-resource-pool.md)
+ [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md) 
