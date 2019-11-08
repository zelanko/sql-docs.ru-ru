---
title: sys. workload_management_workload_classifiers (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/05/2019
ms.prod: sql
ms.technology: system-objects
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: 585eb4551fb688f4f6a620729310b0245462cbff
ms.sourcegitcommit: 66dbc3b740f4174f3364ba6b68bc8df1e941050f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73632967"
---
# <a name="sysworkload_management_workload_classifiers-transact-sql"></a>sys. workload_management_workload_classifiers (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

 Возвращает сведения для классификаторов рабочей нагрузки.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|
|classifier_id|**int**|Уникальный идентификатор классификатора. Не допускает значение NULL.||
group_name|**sysname**|Имя группы рабочей нагрузки, которой назначен классификатор. Не допускает значение NULL. Присоединение к sys. workload_management_workload_groups ||
имя|**sysname**|Имя классификатора. Должен быть уникальным для экземпляра. Не допускает значение NULL.||
|importance|**sysname**|— Это относительная важность запроса в этой группе рабочей нагрузки и в группах рабочей нагрузки для общих ресурсов.  Важность, указанная в классификаторе, переопределяет параметр важности группы рабочей нагрузки. Допускает значение NULL.  При значении NULL используется параметр важности группы рабочей нагрузки.|Low, below_normal, обычная (по умолчанию), above_normal, High |
|create_time|**datetime**|Время создания классификатора. Не допускает значение NULL.||
modify_time|**datetime**|Время последнего изменения классификатора. Не допускает значение NULL.||
is_enabled|**bit**|ВНУТРИКЛАСТЕРНЫХ||
|&nbsp;||||
  
## <a name="permissions"></a>Разрешения

Необходимо разрешение VIEW SERVER STATE.

## <a name="next-steps"></a>Следующие шаги

 Список всех представлений каталога для хранилища данных SQL и параллельного хранилища данных см. в статье [представления каталога данных SQL и параллельного](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)хранилища данных. Сведения о создании классификатора рабочей нагрузки см. в разделе [Создание классификатора рабочей нагрузки](../../t-sql/statements/create-workload-classifier-transact-sql.md). Дополнительные сведения о классификации рабочей нагрузки см. в разделе [классификация рабочей нагрузки](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification) .
