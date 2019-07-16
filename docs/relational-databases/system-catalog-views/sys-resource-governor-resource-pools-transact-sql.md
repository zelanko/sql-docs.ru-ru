---
title: sys.resource_governor_resource_pools (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_resource_pools
- resource_governor_resource_pools
- sys.resource_governor_resource_pools_TSQL
- resource_governor_resource_pools_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governor_resource_pools catalog view
ms.assetid: 56793e9c-aa90-452e-88c6-d9b799239888
author: stevestein
ms.author: sstein
ms.openlocfilehash: 06ed4b4820ce7a6e6483df6efd1de2e8fbadf954
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67904465"
---
# <a name="sysresourcegovernorresourcepools-transact-sql"></a>sys.resource_governor_resource_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает хранимую конфигурацию пула ресурсов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Каждая строка представления определяет конфигурацию пула.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|pool_id|**int**|Уникальный идентификатор пула ресурсов. Не допускает значение NULL.|  
|name|**sysname**|Имя пула ресурсов. Не допускает значение NULL.|  
|min_cpu_percent|**int**|Гарантированная средняя пропускная способность ЦП для всех запросов в пуле ресурсов при возникновении состязания использования ЦП. Не допускает значение NULL.|  
|max_cpu_percent|**int**|Максимальная средняя пропускная способность ЦП, разрешенная для всех запросов в пуле ресурсов при возникновении состязания использования ЦП. Не допускает значение NULL.|  
|min_memory_percent|**int**|Гарантированный объем памяти для всех запросов в пуле ресурсов. Не используется совместно с другими пулами ресурсов. Не допускает значение NULL.|  
|max_memory_percent|**int**|Процентная доля от общего объема памяти сервера, который может использоваться для запросов в данном пуле ресурсов. Не допускает значение NULL. Эффективный максимум зависит от минимальных значений для пула. Например, значение max_memory_percent можно установить в 100, но реальный максимум будет ниже.|  
|cap_cpu_percent|**int**|**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Жесткое ограничение пропускной способности ЦП, которая предоставляется всем запросам в пуле ресурсов. Ограничивает максимальный уровень пропускной способности ЦП заданным значением. Диапазон допустимых значений — от 1 до 100.|  
|min_iops_per_volume|**int**|**Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Параметр минимального числа операций ввода-вывода в секунду (IOPS) в расчете на том для этого пула. 0 = без резервирования. Не может иметь значение null.|  
|max_iops_per_volume|**int**|**Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Параметр максимального числа операций ввода-вывода в секунду (IOPS) в расчете на том для этого пула. 0 = неограниченно. Не может иметь значение null.|  
  
## <a name="remarks"></a>Примечания  
 Представление каталога отображает хранимые метаданные. Чтобы увидеть конфигурации, хранимой в памяти, используйте соответствующее динамическое административное представление [sys.dm_resource_governor_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешение VIEW ANY DEFINITION для просмотра содержимого и разрешение CONTROL SERVER для изменения содержимого.  
  
## <a name="see-also"></a>См. также  
 [Представления каталога регулятора ресурсов &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)   
 [sys.dm_resource_governor_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)   
 [регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)   
 [sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)  
  
  
