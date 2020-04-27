---
title: sys. dm_os_buffer_pool_extension_configuration (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 09/09/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_buffer_pool_extension_configuration
- sys.dm_os_buffer_pool_extension_configuration_TSQL
- dm_os_buffer_pool_extension_configuration_TSQL
- sys.dm_os_buffer_pool_extension_configuration
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_buffer_pool_extension_configuration dynamic management view
ms.assetid: d52cc481-4d29-4f33-b63d-231ec35d092f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 38e4e1ad85a5e968d4b0bb33a3a72a829942585b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67900227"
---
# <a name="sysdm_os_buffer_pool_extension_configuration-transact-sql"></a>sys.dm_os_buffer_pool_extension_configuration (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о конфигурации расширения буферного пула в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Возвращает по одной строке для каждого файла расширения буферного пула.  
  

  
| Имя столбца | Тип данных | Описание |
| :---------- | :-------- | :---------- |
|path|**nvarchar**(256)|Путь и имя файла кэша расширения буферного пула. Допускает значение NULL.|  
|file_id|**int**|Идентификатор файла расширения буферного пула. Не допускает значение NULL.|  
|state|**int**|Состояние расширения буферного пула. Не допускает значение NULL.<br /><br /> 0 = расширение буферного пула выключено<br /><br /> 1 = отключение расширения буферного пула<br /><br /> 2 — зарезервировано для будущего использования<br /><br /> 3 = включение расширения буферного пула<br /><br /> 4 = зарезервировано для использования в будущем<br /><br /> 5 = расширение буферного пула включено|  
|state_description|**nvarchar**(60)|Описывает состояние расширения буферного пула. Допускает значение NULL.<br /><br /> 0 = РАСШИРЕНИЕ БУФЕРНОГО ПУЛА ВЫКЛЮЧЕНО<br /><br /> 5 = РАСШИРЕНИЕ БУФЕРНОГО ПУЛА ВКЛЮЧЕНО|
|current_size_in_kb|**bigint**|Текущий размер файла расширения буферного пула. Не допускает значение NULL.|
| &nbsp; | &nbsp; | &nbsp; |

## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-configuration-buffer-pool-extension-information"></a>A. Возвращает сведения о конфигурации расширения буферного пула.  
 Следующий пример возвращает все столбцы из динамического административного представления sys.dm_os_buffer_pool_extension_configruation.  
  
```sql  
SELECT path, file_id, state, state_description, current_size_in_kb  
FROM sys.dm_os_buffer_pool_extension_configuration;  
```  
  
### <a name="b-returning-the-number-of-cached-pages-in-the-buffer-pool-extension-file"></a>Б) Возвращает число кэшированных страниц в файле расширения буферного пула.  
 В следующем примере возвращается количество кэшированных страниц в каждом файле расширения буферного пула.  
  
```sql  
SELECT COUNT(*) AS cached_pages_count  
FROM sys.dm_os_buffer_descriptors  
WHERE is_in_bpool_extension <> 0  
;  
```  
  
## <a name="see-also"></a>См. также  
 [Расширение буферного пула](../../database-engine/configure-windows/buffer-pool-extension.md)   
 [sys.dm_os_buffer_descriptors (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-buffer-descriptors-transact-sql.md)  
  
  
