---
title: sys.workload_management_workload_classifier_details (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/26/2019
ms.prod: ''
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: ed7694f087a8e1b10697ed2083dbae8bf879528c
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58513311"
---
# <a name="sysworkloadmanagementworkloadclassifierdetails-transact-sql-preview"></a>sys.workload_management_workload_classifier_details (Transact-SQL) (Предварительная версия)

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
