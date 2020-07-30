---
title: sys. dm_os_server_diagnostics_log_configurations | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_server_diagnostics_log_configurations
- sys.dm_os_server_diagnostics_log_configurations_TSQL
- dm_os_server_diagnostics_log_configurations
- dm_os_server_diagnostics_log_configurations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_os_server_diagnostics_log_configurations
- sys.dm_os_server_diagnostics_log_configurations
ms.assetid: c09ea433-d283-4f83-af69-d458aad59217
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 797cdece07651499a9b770ba59972792805828a5
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87395236"
---
# <a name="sysdm_os_server_diagnostics_log_configurations"></a>sys.dm_os_server_diagnostics_log_configurations
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Возвращает одну строку с текущей конфигурацией диагностического журнала отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эти значения свойств определяют, включено ли ведение журнала диагностики, а также указывают расположение, количество и размер файлов журнала.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|is_enabled|**bit**|Указывает, включено ли ведение журнала.<br /><br /> 1 = ведение журнала диагностики включено<br /><br /> 0 = ведение журнала диагностики отключено|  
|max_size|**int**|Максимальный размер каждого из журналов диагностики в мегабайтах. Значение по умолчанию равно 100 МБ.|  
|max_files|**int**|Максимальное число файлов журналов диагностики, которое может храниться на компьютере, прежде чем существующие файлы будут очищены и использованы для новых журналов диагностики.|  
|path|**nvarchar(260)**|Путь, определяющий расположение журналов диагностики. Расположение по умолчанию — \<\MSSQL\Log> в папке установки экземпляра отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="permissions"></a>Разрешения  
 Требует наличия разрешения VIEW SERVER STATE для экземпляра отказоустойчивого кластера SQL Server.  
  
## <a name="examples"></a>Примеры  
 В следующем примере sys.dm_os_server_diagnostics_log_configurations используется для возврата значений свойств журналов диагностики отработки отказа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT <list of columns>  
FROM sys.dm_os_server_diagnostics_log_configurations;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|IS_ENABLED|PATH|MAX_SIZE|MAX_FILES|  
|-----------------|----------|---------------|----------------|  
|1|\<C:\Program Files\Microsoft SQL Server\MSSQL13\MSSQL\Log>|10|10|  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и чтение журнала диагностики для экземпляра отказоустойчивого кластера](../../sql-server/failover-clusters/windows/view-and-read-failover-cluster-instance-diagnostics-log.md)  
  
  
