---
description: sys.dm_pdw_request_steps (Transact-SQL)
title: sys.dm_pdw_request_steps (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/28/2020
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
ms.openlocfilehash: e653d8f468587558c5bbe59c5c028b71002b2533
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/13/2020
ms.locfileid: "91988746"
---
# <a name="sysdm_pdw_request_steps-transact-sql"></a>sys.dm_pdw_request_steps (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Содержит сведения обо всех шагах, составляющих данный запрос или запрос в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] . В нем отображается одна строка для каждого шага запроса.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|request_id и step_index сделать ключ для этого представления.<br /><br /> Уникальный числовой идентификатор, связанный с запросом.|См. request_id в [sys.dm_pdw_exec_requests &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|request_id и step_index сделать ключ для этого представления.<br /><br /> Расположение этого шага в последовательности шагов, составляющих запрос.|от 0 до (n – 1) для запроса с n шагами.|  
|plan_node_id|**int**|Идентификатор узла, соответствующий ИДЕНТИФИКАТОРу оператора этого шага в плане выполнения.|Нет|  
|operation_type|**nvarchar(35)**|Тип операции, представленной этим шагом.|**Операции с планом запросов DMS:** "ReturnOperation", "PartitionMoveOperation", "MoveOperation", "BroadcastMoveOperation", "ShuffleMoveOperation", "TrimMoveOperation", "CopyOperation", "Дистрибутерепликатедтаблемовеоператион"<br /><br /> **Операции плана запроса SQL:** "OnOperation", "RemoteOperation"<br /><br /> **Другие операции плана запроса:** "Метадатакреатеоператион", "Рандомидоператион"<br /><br /> **Внешние операции для операций чтения:** "Хадупшуффлеоператион", "Хадупраундробиноператион", "Хадупброадкастоператион"<br /><br /> **Внешние операции для MapReduce:** "Хадупжобоператион", "Хдфсделетеоператион"<br /><br /> **Внешние операции записи:** "Екстерналекспортдистрибутедоператион", "Екстерналекспортрепликатедоператион", "Екстерналекспортконтролоператион"<br /><br /> Дополнительные сведения см. в разделе «Основные сведения о планах запросов» в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)] . <br /><br />  На план запроса также могут повлиять параметры базы данных.  Проверьте [Параметры ALTER DATABASE SET](../../t-sql/statements/alter-database-transact-sql-set-options.md?bc=%252fazure%252fsql-data-warehouse%252fbreadcrumb%252ftoc.json&toc=%252fazure%252fsql-data-warehouse%252ftoc.json&view=azure-sqldw-latest) для получения дополнительных сведений.|  
|distribution_type|**nvarchar(32)**|Тип распространения, который будет подвергнут этому шагу.|"AllNodes", "Аллдистрибутионс", "Аллкомпутенодес", "ComputeNode", "Distribution", "Субсетнодес", "Distribution", "Unspecified"|  
|location_type|**nvarchar(32)**|Место выполнения шага.|"COMPUTE", "Control", "DMS"|  
|status|**nvarchar(32)**|Состояние этого шага.|Ожидание, выполнение, завершение, сбой, Ундофаилед, Пендингканцел, отменено, Отмена, прервано|  
|error_id|**nvarchar (36)**|Уникальный идентификатор ошибки, связанной с этим шагом, если таковой имеется.|См. error_id [sys.dm_pdw_errors &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md). Значение NULL, если ошибка не возникла.|  
|start_time|**datetime**|Время начала выполнения этапа.|Меньше или равно текущему времени и больше или равно end_compile_time запроса, к которому относится этот шаг. Дополнительные сведения о запросах см. в разделе [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|end_time|**datetime**|Время, когда выполнение этого шага было завершено, было отменено или завершилось сбоем.|Меньше или равно текущему времени и больше или равно start_time. Задайте значение NULL для шагов, выполняемых в данный момент или в очереди.|  
|total_elapsed_time|**int**|Общее количество времени выполнения шага запроса (в миллисекундах).|Между 0 и разностью между end_time и start_time. 0 для шагов в очереди.<br /><br /> Если total_elapsed_time превышает максимальное значение для целого числа, total_elapsed_time будет продолжать быть максимальным значением. Это условие выдаст предупреждение "превышено максимальное значение".<br /><br /> Максимальное значение в миллисекундах эквивалентно 24,8 дням.|  
|row_count|**bigint**|Общее число строк, измененных или возвращенных этим запросом.|Число строк, затронутых шагом.  Для шагов операций с данными больше или равно нулю.  -1 для действий, которые не работают с данными.|  
|estimated_rows|**bigint**|Общее число строк работы, вычисленных во время компиляции запроса.|Количество строк, предполагаемое на шаге.  Для шагов операций с данными больше или равно нулю.  -1 для действий, которые не работают с данными.|  
|.|**nvarchar(4000)**|Содержит полный текст команды этого шага.|Любая допустимая строка запроса для шага. Значение NULL, если операция имеет тип Метадатакреатеоператион. Усекается, если длиннее 4000 символов.|  
  
 Сведения о максимальном объеме строк, хранящихся в этом представлении, см. в разделе Максимальное значение системного представления раздела "минимальное и максимальное значения" в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления хранилища данных SQL и параллельного хранилища данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
