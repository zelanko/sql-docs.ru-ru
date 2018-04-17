---
title: sys.resource_governor_configuration (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_configuration_TSQL
- sys.resource_governor_configuration
- resource_governor_configuration_TSQL
- resource_governor_configuration
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governor_configuration catalog view
ms.assetid: 89099668-1dc6-4b07-9d8b-49bc95c7bfc0
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2c4387024aca3d7bd1240a1eae8dcc4e282f184a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysresourcegovernorconfiguration-transact-sql"></a>sys.resource_governor_configuration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает хранимое состояние регулятора ресурсов.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|classifier_function_id|**int**|Идентификатор функции-классификатора в том виде, в каком он хранится в метаданных. Не допускает значение NULL.<br /><br /> **Примечание** эта функция используется для классификации новых сеансов и использует правила для перенаправления рабочей нагрузки в соответствующую группу рабочей нагрузки. Дополнительные сведения см. в разделе [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) (Регулятор ресурсов).|  
|is_enabled|**бит**|Отображает текущее состояние регулятора ресурсов:<br /><br /> 0 = не включен регулятор ресурсов.<br /><br /> 1 = включен регулятор ресурсов.<br /><br /> Не допускает значение NULL.|  
|max_outstanding_io_per_volume|**int**|**Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Максимальное число невыполненных операций ввода-вывода в расчете на том.|  
  
## <a name="remarks"></a>Замечания  
 Представление каталога отображает конфигурацию регулятора ресурсов в том виде, в каком она хранится в метаданных. Для просмотра конфигурации, хранимой в памяти, используйте соответствующее динамическое административное представление.  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешение VIEW ANY DEFINITION для просмотра содержимого и разрешение CONTROL SERVER для изменения содержимого.  
  
## <a name="examples"></a>Примеры  
 Следующий пример иллюстрирует получение и сравнение хранимых значений метаданных и значений из памяти настройки регулятора ресурсов.  
  
```  
USE master;  
GO  
-- Get the stored metadata.  
SELECT   
object_schema_name(classifier_function_id) AS 'Classifier UDF schema in metadata',   
object_name(classifier_function_id) AS 'Classifier UDF name in metadata'  
FROM   
sys.resource_governor_configuration;  
GO  
-- Get the in-memory configuration.  
SELECT   
object_schema_name(classifier_function_id) AS 'Active classifier UDF schema',   
object_name(classifier_function_id) AS 'Active classifier UDF name'  
FROM   
sys.dm_resource_governor_configuration;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Представления каталога регулятора ресурсов &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.dm_resource_governor_configuration &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql.md)   
 [регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)  
  
  
