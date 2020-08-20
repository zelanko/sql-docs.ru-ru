---
description: sys. dm_pdw_request_steps (Transact-SQL)
title: sys. dm_pdw_request_steps (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/19/2020
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: cc563e88-0d34-436e-b914-b60d6ee0d50b
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 4144e068354d43e2e8a5f9ea5bd6af7ad40a0e6d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489767"
---
# <a name="sysdm_pdw_request_steps-transact-sql"></a>sys. dm_pdw_request_steps (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Содержит сведения обо всех шагах, составляющих данный запрос или запрос в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] . В нем отображается одна строка для каждого шага запроса.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|request_id и step_index сделать ключ для этого представления.<br /><br /> Уникальный числовой идентификатор, связанный с запросом.|См. раздел request_id в [sys. dm_pdw_exec_requests &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|request_id и step_index сделать ключ для этого представления.<br /><br /> Расположение этого шага в последовательности шагов, составляющих запрос.|от 0 до (n – 1) для запроса с n шагами.|  
|operation_type|**nvarchar(35)**|Тип операции, представленной этим шагом.|**Операции с планом запросов DMS:** "ReturnOperation", "PartitionMoveOperation", "MoveOperation", "BroadcastMoveOperation", "ShuffleMoveOperation", "TrimMoveOperation", "CopyOperation", "Дистрибутерепликатедтаблемовеоператион"<br /><br /> **Операции плана запроса SQL:** "OnOperation", "RemoteOperation"<br /><br /> **Другие операции плана запроса:** "Метадатакреатеоператион", "Рандомидоператион"<br /><br /> **Внешние операции для операций чтения:** "Хадупшуффлеоператион", "Хадупраундробиноператион", "Хадупброадкастоператион"<br /><br /> **Внешние операции для MapReduce:** "Хадупжобоператион", "Хдфсделетеоператион"<br /><br /> **Внешние операции записи:** "Екстерналекспортдистрибутедоператион", "Екстерналекспортрепликатедоператион", "Екстерналекспортконтролоператион"<br /><br /> Дополнительные сведения см. в разделе «Основные сведения о планах запросов» в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)] . <br /><br />  На план запроса также могут повлиять параметры базы данных.  Проверьте [Параметры ALTER DATABASE SET](https://docs.microsoft.com/sql/t-sql/statements/alter-database-transact-sql-set-options?toc=/azure/sql-data-warehouse/toc.json&bc=/azure/sql-data-warehouse/breadcrumb/toc.json&view=azure-sqldw-latest) для получения дополнительных сведений.|  
|distribution_type|**nvarchar(32)**|Тип распространения, который будет подвергнут этому шагу.|"AllNodes", "Аллдистрибутионс", "Аллкомпутенодес", "ComputeNode", "Distribution", "Субсетнодес", "Distribution", "Unspecified"|  
|location_type|**nvarchar(32)**|Место выполнения шага.|"COMPUTE", "Control", "DMS"|  
|status|**nvarchar(32)**|Состояние этого шага.|Ожидание, выполнение, завершение, сбой, Ундофаилед, Пендингканцел, отменено, Отмена, прервано|  
|error_id|**nvarchar (36)**|Уникальный идентификатор ошибки, связанной с этим шагом, если таковой имеется.|См. раздел error_id из [sys. dm_pdw_errors &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md). Значение NULL, если ошибка не возникла.|  
|start_time|**datetime**|Время начала выполнения этапа.|Меньше или равно текущему времени и больше или равно end_compile_time запроса, к которому относится этот шаг. Дополнительные сведения о запросах см. в разделе [sys. dm_pdw_exec_requests &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|end_time|**datetime**|Время, когда выполнение этого шага было завершено, было отменено или завершилось сбоем.|Меньше или равно текущему времени и больше или равно start_time. Задайте значение NULL для шагов, выполняемых в данный момент или в очереди.|  
|total_elapsed_time|**int**|Общее количество времени выполнения шага запроса (в миллисекундах).|Между 0 и разностью между end_time и start_time. 0 для шагов в очереди.<br /><br /> Если total_elapsed_time превышает максимальное значение для целого числа, total_elapsed_time будет продолжать быть максимальным значением. Это условие выдаст предупреждение "превышено максимальное значение".<br /><br /> Максимальное значение в миллисекундах эквивалентно 24,8 дням.|  
|row_count|**bigint**|Общее число строк, измененных или возвращенных этим запросом.|Число строк, затронутых шагом.  Для шагов операций с данными больше или равно нулю.  -1 для действий, которые не работают с данными.|  
|.|**nvarchar(4000)**|Содержит полный текст команды этого шага.|Любая допустимая строка запроса для шага. Значение NULL, если операция имеет тип Метадатакреатеоператион. Усекается, если длиннее 4000 символов.|  
  
 Сведения о максимальном объеме строк, хранящихся в этом представлении, см. в разделе Максимальное значение системного представления раздела "минимальное и максимальное значения" в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления хранилища данных SQL и параллельного хранилища данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
