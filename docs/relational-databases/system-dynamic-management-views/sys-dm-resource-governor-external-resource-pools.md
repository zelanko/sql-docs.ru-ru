---
description: sys.dm_resource_governor_external_resource_pools (Transact-SQL)
title: sys.dm_resource_governor_external_resource_pools (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/06/2020
ms.prod: sql
ms.technology: machine-learning-services
ms.reviewer: ''
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
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15'
ms.openlocfilehash: 1fdce8416bf28b1013b32efb5c2d1dc46c76831d
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97484596"
---
# <a name="sysdm_resource_governor_external_resource_pools-transact-sql"></a>sys.dm_resource_governor_external_resource_pools (Transact-SQL)
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Возвращает сведения о текущем состоянии внешнего пула ресурсов, текущую конфигурацию пулов ресурсов и статистику пула ресурсов. 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
|Имя столбца      |Тип данных      |Описание|  
|----------------|---------------|-----------------| 
| external_pool_id|**int**|Идентификатор пула ресурсов. Не допускает значение NULL. |
| name|**sysname**|Имя пула ресурсов. Не допускает значение NULL. 
| pool_version|**int**|Внутренний номер версии.|
| max_cpu_percent|**int**|Текущая конфигурация максимальной средней пропускной способности ЦП, разрешенной для всех запросов в пуле ресурсов при возникновении состязания использования ЦП. Не допускает значение NULL. |
| max_processes|**int**|Максимальное количество одновременных внешних процессов. Значение по умолчанию равно 0 и означает отсутствие ограничений. Не допускает значение NULL.|
| max_memory_percent|**int**|Текущая конфигурация процентной доли от общего объема памяти сервера, которая может использоваться для запросов в данном пуле ресурсов. Не допускает значение NULL. |
| statistics_start_time|**datetime**|Время, когда была очищена статистика для данного пула. Не допускает значение NULL. 
| peak_memory_kb|**bigint**|Максимальный объем используемой памяти (в килобайтах) для пула ресурсов. Не допускает значение NULL. |
| write_io_count|**int**|Общее число выполненных операций ввода-вывода записи с момента сброса статистики Resource Governor. Не допускает значение NULL. |
| read_io_count|**int**|Общее число выполненных операций ввода-вывода чтения с момента сброса статистики Resource Governor. Не допускает значение NULL. |
| total_cpu_kernel_ms|**bigint**|Совокупное время ядра использования ЦП, в миллисекундах, с момента сброса статистики Resource Governor. Не допускает значение NULL. |
| total_cpu_user_ms|**bigint**|Совокупное время использования ЦП, в миллисекундах, с момента сброса статистики Resource Governor. Не допускает значение NULL. |
| active_processes_count|**int**|Количество внешних процессов, выполняемых в момент запроса. Не допускает значение NULL. |

 
## <a name="permissions"></a>Разрешения

Требуется разрешение `VIEW SERVER STATE`.

## <a name="see-also"></a>См. также:  
 [sys.dm_resource_governor_external_resource_pool_affinity (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  
