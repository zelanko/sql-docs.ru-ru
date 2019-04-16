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
ms.openlocfilehash: 9afd00a887244c02849d40eed635500b06533709
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582727"
---
# <a name="sysworkloadmanagementworkloadclassifierdetails-transact-sql-preview"></a>sys.workload_management_workload_classifier_details (Transact-SQL) (Предварительная версия)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

> [!Note]
> Классификации рабочей нагрузки доступна в предварительной версии для Gen2 хранилище данных SQL. Предварительный просмотр рабочей нагрузки управления классификации и важность — для сборок с датой выпуска от 9 апреля 2019 г. или более поздней версии.  Пользователям не следует использовать сборки до этой даты для тестирования управления рабочей нагрузки.  Чтобы определить, если построение является возможность управления рабочими нагрузками, выполните select @@version при подключении к экземпляру хранилища данных SQL.

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
