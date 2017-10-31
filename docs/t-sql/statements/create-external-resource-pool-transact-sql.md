---
title: "Создание ПУЛА ВНЕШНИХ РЕСУРСОВ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE EXTERNAL RESOURCE POOL
- CREATE EXTERNAL_RESOURCE_POOL_TSQL
- EXTERNAL RESOURCE POOL
- EXTERNAL_RESOURCE_POOL_TSQL
- EXTERNAL RESOURCE
- EXTERNAL_RESOURCE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE EXTERNAL RESOURCE POOL statement
ms.assetid: 8cc798ad-c395-461c-b7ff-8c561c098808
caps.latest.revision: 12
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 32c33076f26332f2a8510c4660696106bef824b5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-external-resource-pool-transact-sql"></a>Создание ПУЛА ВНЕШНИХ РЕСУРСОВ (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Создает внешний пул позволяет определить ресурсы для внешних процессов. Для служб R управляет внешний пул `rterm.exe`, `BxlServer.exe`и порожденных ими процессов. Пул ресурсов представляет подмножество физических ресурсов (память и процессоры) экземпляра компонента Database Engine. Регулятор ресурсов позволяет администратору базы данных распределять ресурсы сервера по пулам ресурсов, используя до 64 пулов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CREATE EXTERNAL RESOURCE POOL pool_name  
[ WITH (  
    [ MAX_CPU_PERCENT = value ]  
    [ [ , ] AFFINITY CPU =    
            {  
                AUTO   
              | ( <cpu_range_spec> )   
              | NUMANODE = ( <NUMA_node_id> )   
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
 *pool_name*  
 Представляет определенное пользователем имя для внешнего пула ресурсов. *pool_name* является алфавитно-цифровым, может иметь длину до 128 символов, должны быть уникальными в рамках экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]и должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md).  
  
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
 Следующая инструкция определяет внешний пул, ограничивающий использование ЦП до 75 процентов и максимальный объем памяти на 30 процентов доступной памяти на компьютере.  
  
```  
CREATE EXTERNAL RESOURCE POOL ep_1  
WITH (  
    MAX_CPU_PERCENT = 75  
    , AFFINITY CPU = AUTO  
    , MAX_MEMORY_PERCENT = 30  
);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Параметр конфигурации сервера External scripts enabled](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
 [sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)   
 [Службы R SQL Server](../../advanced-analytics/r-services/sql-server-r-services.md)   
 [Известные проблемы для SQL Server R Services](../../advanced-analytics/r-services/known-issues-for-sql-server-r-services.md)   
 [ИЗМЕНИТЬ внешний ПУЛ РЕСУРСОВ &#40; Transact-SQL &#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)   
 [DROP EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/drop-external-resource-pool-transact-sql.md)   
 [CREATE RESOURCE POOL (Transact-SQL)](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [CREATE WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [Пул ресурсов регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [sys.resource_governor_external_resource_pools (Transact-SQL)](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)   
 [sys.dm_resource_governor_external_resource_pool_affinity &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  


