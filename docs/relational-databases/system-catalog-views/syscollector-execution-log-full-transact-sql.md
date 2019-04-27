---
title: syscollector_execution_log_full (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syscollector_execution_log_full
- syscollector_execution_log_full_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data collector view
- syscollector_execution_log_full view
ms.assetid: 6c8db22d-2e4c-4b7c-ac5a-8762ef1b175b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 99ce8003b70ad41be225a7678c97ed44d9f6c7dd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62760180"
---
# <a name="syscollectorexecutionlogfull-transact-sql"></a>syscollector_execution_log_full (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет сведения о наборе элементов сбора или пакете, если журнал выполнения заполнен.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|log_id|**bigint**|Определяет выполнение каждого набора элементов сбора. Используется для соединения этого представления с другими подробными журналами. Допускает значение NULL.|  
|parent_log_id|**bigint**|Определяет родительский пакет или набор элементов сбора. Не допускает значение NULL. Идентификаторы соединяются в связь типа «родитель-потомок», что позволяет определить, какой пакет был запущен тем или иным набором сбора. Это представление группирует записи журнала по связям типа «родители-потомки» и делает отступ перед именами пакетов, чтобы была ясно видна цепочка вызовов.|  
|name|**nvarchar(4000)**|Имя набора элементов сбора или пакета, который представляет эта запись журнала. Допускает значение NULL.|  
|status|**smallint**|Указывает текущее состояние набора элементов сбора или пакета. Допускает значение NULL.<br /><br /> Возможны следующие значения.<br /><br /> 0 = запущен<br /><br /> 1 = завершен<br /><br /> 2 = ошибка|  
|runtime_execution_mode|**smallint**|Указывает на род деятельности набора элементов сбора: сбор данных или их отправка. Допускает значение NULL.|  
|start_time|**datetime**|Время, когда был задан набор элементов сбора или запущен пакет. Допускает значение NULL.|  
|last_iteration_time|**datetime**|Для непрерывно выполняемых пакетов это время, когда пакет последний раз создал моментальный снимок. Допускает значение NULL.|  
|finish_time|**datetime**|Время окончания выполнения завершенных пакетов и наборов элементов сбора. Допускает значение NULL.|  
|duration|**int**|Время выполнения пакета или набора элементов сбора (в секундах). Допускает значение NULL.|  
|failure_message|**nvarchar(2048)**|Если набор элементов сбора или пакет завершился с ошибкой, содержит самое последнее сообщение об ошибке для данного компонента. Допускает значение NULL. Чтобы получить более подробные сведения об ошибке, используйте [fn_syscollector_get_execution_details &#40;Transact-SQL&#41; ](../../relational-databases/system-functions/fn-syscollector-get-execution-details-transact-sql.md) функции.|  
|оператор|**nvarchar(128)**|Определяет, кто запустил набор элементов сбора или пакет. Допускает значение NULL.|  
|package_execution_id|**uniqueidentifier**|Содержит ссылку на таблицу журнала служб [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Допускает значение NULL.|  
|collection_set_id|**int**|Предоставляет ссылку на таблицу конфигурации сбора данных в базе данных msdb. Допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для **dc_operator**.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры сборщика данных (Transact-SQL)](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Представления сборщика данных (Transact-SQL)](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)  
  
  
