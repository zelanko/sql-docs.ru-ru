---
title: sys. workload_management_workload_classifier_details (Transact-SQL) | Документация Майкрософт
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
ms.openlocfilehash: 3fbbc52f13bebbb46a3afc7d2dd450765d28a21a
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87393975"
---
# <a name="sysworkload_management_workload_classifier_details-transact-sql"></a>sys. workload_management_workload_classifier_details (Transact-SQL)

[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

  Возвращает сведения для каждого классификатора.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|
|classifier_id|**int**|Идентификатор классификатора.  Не допускает значение NULL.|
|classifier_type|**sysname**|Присоединение к [sys. workload_management_workload_classifiers](sys-workload-management-workload-classifiers-transact-sql.md).|`membername`</br>`wlm_label`</br>`wlm_context`</br>`start_time`</br>`end_time`|
|classifier_value|**sysname**|Значение классификатора. Не допускает значение NULL.||

## <a name="permissions"></a>Разрешения

Необходимо разрешение VIEW SERVER STATE.

## <a name="next-steps"></a>Дальнейшие действия
  
Список всех представлений каталога для хранилища данных SQL и параллельного хранилища данных см. в статье [представления каталога данных SQL и параллельного](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)хранилища данных. Сведения о создании классификатора рабочей нагрузки см. в разделе [Создание классификатора рабочей нагрузки](../../t-sql/statements/create-workload-classifier-transact-sql.md). Дополнительные сведения о классификации рабочей нагрузки см. в разделе [классификация рабочей нагрузки](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification) хранилища данных SQL и [важность рабочей нагрузки](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification) .
