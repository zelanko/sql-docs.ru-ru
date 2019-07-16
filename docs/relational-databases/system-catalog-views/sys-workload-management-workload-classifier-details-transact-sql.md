---
title: sys.workload_management_workload_classifier_details (Transact-SQL) | Документация Майкрософт
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
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: f9314b9297af7e8156ed86b2bfa2dadd18896bb9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68061294"
---
# <a name="sysworkloadmanagementworkloadclassifierdetails-transact-sql"></a>sys.workload_management_workload_classifier_details (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

  Возвращает сведения для каждого классификатора.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|
|classifier_id|**int**|Идентификатор классификатора. Присоединяемые к [sys.workload_management_workload_classifiers](sys-workload-management-workload-classifiers-transact-sql.md). Не допускает значение NULL.|
|classifier_type|**sysname**|Сущность, на котором выполняется классификации. Не допускает значение NULL.|ИМЯ ПОЛЬЗОВАТЕЛЯ|
|classifier_value|**sysname**|Значение классификатора. Не допускает значение NULL.||

## <a name="permissions"></a>Разрешения

Необходимо разрешение VIEW SERVER STATE.

## <a name="next-steps"></a>Следующие шаги
  
 Список всех представлений каталога для хранилища данных SQL и Parallel Data Warehouse, см. в разделе [хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md). Чтобы создать классификатор рабочей нагрузки, см. в разделе [СОЗДАНИЯ КЛАССИФИКАТОРА рабочей НАГРУЗКИ](../../t-sql/statements/create-workload-classifier-transact-sql.md). Дополнительные сведения о классификации рабочей нагрузки, см. в разделе хранилища данных SQL [классификации рабочей нагрузки](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification) и [важность рабочих нагрузок](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)
