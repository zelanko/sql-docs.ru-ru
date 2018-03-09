---
title: "ИЗМЕНИТЬ внешний ПУЛ РЕСУРСОВ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 11/13/2017
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
- ALTER_EXTERNAL_RESOURCE_POOL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER EXTERNAL RESOURCE POOL statement
ms.assetid: 634c327d-971b-49ba-b8a2-e243a04040db
caps.latest.revision: 
author: jeannt
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cb4073a8114e953dc9df87614a63e074ab8c9683
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="alter-external-resource-pool-transact-sql"></a>ИЗМЕНИТЬ внешний ПУЛ РЕСУРСОВ (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**Применяется к:** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] и [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)][!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Изменение внешнего пула регулятора ресурсов, указывающий ресурсы, которые могут использоваться с внешними процессами. 

+ Для [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] в [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)], управляющий внешний пул `rterm.exe`, `BxlServer.exe`и порожденных ими процессов.

+ Для [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] в SQL Server 2017 г внешний пул управляет процессами R для предыдущей версии, а также `python.exe`, `BxlServer.exe`и порожденных ими процессов.

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).

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

{ *pool_name* | «default»}  
Имя существующего пула внешних ресурсов, определяемых пользователем или пул внешних ресурсов по умолчанию, создаваемой при [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлен.
«default» должно быть заключено в кавычки ("») или квадратные скобки ([]) при использовании с `ALTER EXTERNAL RESOURCE POOL` во избежание конфликтов с `DEFAULT`, которой является системой зарезервированным словом.


MAX_CPU_PERCENT =*значение*  
Указывает максимальное среднюю пропускную способность ЦП для всех запросов в пуле внешнего ресурса можно при возникновении состязания использования ЦП. *значение* представляет собой целое число, значение по умолчанию 100. Допустимые значения для *значение* — от 1 до 100.


СОПОСТАВЛЕНИЕ {ЦП = AUTO | ( \<CPU_range_spec >) | NUMANODE = (\<NUMA_node_range_spec >)}  
Подключите внешний пул ресурсов ЦП. Значение по умолчанию — AUTO.

СХОДСТВО ЦП = **(** \<CPU_range_spec > **)** сопоставляет внешний пул ресурсов для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяется данного CPU_IDs ЦП. При использовании AFFINITY NUMANODE = **(** \<NUMA_node_range_spec > **)**, сопоставляется внешний пул ресурсов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] физическими процессорами, соответствующими в данной архитектуре NUMA узел или диапазону узлов.


MAX_MEMORY_PERCENT =*значение*  
Указывает общий объем памяти сервера, можно использовать для запросов в этом внешнего пула ресурсов. *значение* представляет собой целое число, значение по умолчанию 100. Допустимые значения для *значение* — от 1 до 100.


MAX_PROCESSES =*значение*  
Указывает максимальное количество процессов, разрешенного для внешнего пула ресурсов. Укажите 0, чтобы задать неограниченный порог для пула, который впоследствии ограничивается только ресурсы компьютера. Значение по умолчанию равно 0.

## <a name="remarks"></a>Замечания

[!INCLUDE[ssDE](../../includes/ssde-md.md)] Реализует пуле ресурсов при выполнении [ALTER RESOURCE GOVERNOR RECONFIGURE](../../t-sql/statements/alter-resource-governor-transact-sql.md) инструкции.

Общие сведения о пулах ресурсов см. в разделе [пул ресурсов регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-resource-pool.md), [sys.resource_governor_external_resource_pools &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md), и [sys.dm_resource_governor_external_resource_pool_affinity &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md).  

Связанный с использованием внешних пулов ресурсов для управления задач обучения машины Подробнее [управление ресурсами для машинного обучения в SQL Server](../../advanced-analytics/r/resource-governance-for-r-services.md)...
## <a name="permissions"></a>Permissions

Требуется разрешение `CONTROL SERVER`

## <a name="examples"></a>Примеры

Следующая инструкция изменяет внешний пул, ограничением ЦП на 50 процентов, а также максимальный объем памяти на 25 процентов доступной памяти на компьютере.
  
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

## <a name="see-also"></a>См. также:

[Управление ресурсами для машинного обучения в SQL Server](../../advanced-analytics/r/resource-governance-for-r-services.md)

[Параметр конфигурации сервера «external scripts enabled»](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)

[Удалить внешний ПУЛ РЕСУРСОВ &#40; Transact-SQL &#41;](../../t-sql/statements/drop-external-resource-pool-transact-sql.md)

[ALTER RESOURCE POOL &#40; Transact-SQL &#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)

[Создание группы рабочей НАГРУЗКИ &#40; Transact-SQL &#41;](../../t-sql/statements/create-workload-group-transact-sql.md)

[Пул ресурсов регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-resource-pool.md)

[ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md) 
