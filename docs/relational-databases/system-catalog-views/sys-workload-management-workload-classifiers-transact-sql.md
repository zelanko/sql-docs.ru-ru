---
title: sys.workload_management_workload_classifiers (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/01/2019
ms.prod: sql
ms.technology: system-objects
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: 5d125f6bdbc024e0f72cb138075e5abb97ae93eb
ms.sourcegitcommit: 0a4879dad09c6c42ad1ff717e4512cfea46820e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67413237"
---
# <a name="sysworkloadmanagementworkloadclassifiers-transact-sql"></a>sys.workload_management_workload_classifiers (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

 Возвращает подробные сведения о рабочей нагрузке классификаторов.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|
|classifier_id|**int**|Уникальный идентификатор классификатора. Не допускает значение NULL.||
group_name|**sysname**|Имя группы рабочей нагрузки, которой назначен классификатора. Не допускает значение NULL. |Статические классы ресурсов</br>staticrc10</br>staticrc20</br>staticrc30</br>staticrc40</br>staticrc50</br>staticrc60</br>staticrc70</br>staticrc80 </br> </br>Динамические классы ресурсов</br>smallrc</br>mediumrc</br>largerc</br>xlargerc|
name|**sysname**|Имя классификатора. Должно быть уникальным в экземпляре. Не допускает значение NULL.||
|importance|**sysname**|— Это относительная важность запроса в данной группе рабочей нагрузки и группы рабочей нагрузки для общих ресурсов.  Важность, указанный в классификаторе переопределяет параметр важности группы рабочей нагрузки.|низкий, below_normal "," Обычная "," above_normal, высокий |
|create_time|**datetime**|Время создания классификатора. Не допускает значение NULL.||
modify_time|**datetime**|Время последнего изменения классификатора. Не допускает значение NULL.||
is_enabled|**bit**|Отображается ли классификатор включен или нет. Включено по умолчанию. Не допускает значение NULL.|0 = классификатор не включена </br> 1 = включено классификатор|
|&nbsp;||||
  
## <a name="permissions"></a>Разрешения

Необходимо разрешение VIEW SERVER STATE.

## <a name="next-steps"></a>Следующие шаги

 Список всех представлений каталога для хранилища данных SQL и Parallel Data Warehouse, см. в разделе [хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md). Чтобы создать классификатор рабочей нагрузки, см. в разделе [СОЗДАНИЯ КЛАССИФИКАТОРА рабочей НАГРУЗКИ](../../t-sql/statements/create-workload-classifier-transact-sql.md). Дополнительные сведения о классификации рабочей нагрузки, см. в разделе [классификации рабочей нагрузки хранилища данных SQL](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)
