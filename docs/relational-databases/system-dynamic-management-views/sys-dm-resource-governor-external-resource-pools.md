---
title: sys.dm_resource_governor_external_resource_pools (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 05/02/2018
ms.suite: sql
ms.prod: sql
ms.technology: machine-learning
ms.reviewer: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_external_resource_pools_TSQL
- sys.dm_resource_governor_external_resource_pools
- dm_resource_governor_external_resource_pools
- dm_resource_governor_external_resource_pools_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_resource_governor_external_resource_pools
- sys.dm_resource_governor_external_resource_pools
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 9e28e848c7a95e8c29558cb6ee77056d47a955e7
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmresourcegovernorexternalresourcepools-transact-sql"></a>sys.dm_resource_governor_external_resource_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Возвращает сведения о текущем состоянии пула внешних ресурсов, текущую конфигурацию пулов ресурсов и статистику пула ресурсов. 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
|Имя столбца      |Тип данных      |Описание|  
|----------------|---------------|-----------------| 
| external_pool_id|**int**|Идентификатор пула ресурсов. Не допускает значение NULL. |
| имя|**sysname**|Имя пула ресурсов. Не допускает значение NULL. 
| pool_version|**int**|номер версии внутреннего.|
| max_cpu_percent|**int**|Текущая конфигурация максимальной средней пропускной способности ЦП, разрешенной для всех запросов в пуле ресурсов при возникновении состязания использования ЦП. Не допускает значение NULL. |
| max_processes|**int**|Максимальное число параллельных внешних процессов. Значение по умолчанию равно 0 и означает отсутствие ограничений. Не допускает значение NULL.|
| max_memory_percent|**int**|Текущая конфигурация процентной доли от общего объема памяти сервера, которая может использоваться для запросов в данном пуле ресурсов. Не допускает значение NULL. |
| statistics_start_time|**datetime**|Время, когда была очищена статистика для данного пула. Не допускает значение NULL. 
| peak_memory_kb|**bigint**|он максимальный объем используемой памяти, в килобайтах, для пула ресурсов. Не допускает значение NULL. |
| write_io_count|**int**|Общая сумма выполненных операций ввода-вывода записи с момента сброса регулятора ресурсов. Не допускает значение NULL. |
| read_io_count|**int**|Общая сумма выполненных операций ввода-вывода с момента сброса регулятора ресурсов. Не допускает значение NULL. |
| total_cpu_kernel_ms|**bigint**|Совокупное время пользователя ЦП в миллисекундах с момента сброса статистики регулятора ресурсов. Не допускает значение NULL. |
| total_cpu_user_ms|**bigint**|Совокупное время пользователя ЦП в миллисекундах с момента сброса статистики регулятора ресурсов. Не допускает значение NULL. |
| active_processes_count|**int**|Количество внешних процессов, запущенных в данный момент запроса. Не допускает значение NULL. |

 
## <a name="permissions"></a>Разрешения

Требуется разрешение `VIEW SERVER STATE`.

## <a name="see-also"></a>См. также  
 [sys.dm_resource_governor_external_resource_pool_affinity (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  
