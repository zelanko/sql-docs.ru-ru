---
title: syscollector_execution_log (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syscollector_execution_log_TSQL
- syscollector_execution_log
dev_langs:
- TSQL
helpviewer_keywords:
- data collector view
- syscollector_execution_log view
ms.assetid: 11554d64-0426-42ce-b7ce-5591f67864d2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 31270da81f0951702aeef0427e70c6a66db5ff0e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68060350"
---
# <a name="syscollector_execution_log-transact-sql"></a>syscollector_execution_log (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает сведения из журнала выполнения для набора элементов сбора или пакета.   
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|log_id|**bigint**|Определяет выполнение каждого набора элементов сбора. Используется для соединения этого представления с другими подробными журналами. Не допускает значение NULL.|  
|parent_log_id|**bigint**|Определяет родительский пакет или набор элементов сбора. Не допускает значение NULL. Идентификаторы соединяются в связь типа «родитель-потомок», что позволяет определить, какой пакет был запущен тем или иным набором сбора. Данное представление группирует записи журналов по признаку связей типа «родитель-потомок» и разделяет имена пакетов пробелами, давая четкое отображение цепочки вызова.|  
|collection_set_id|**int**|Определяет набор элементов сбора или пакет, соответствующий данной записи журнала. Не допускает значение NULL.|  
|collection_item_id|**int**|Определяет элемент сбора. Допускает значение NULL.|  
|start_time|**datetime**|Время, когда был задан набор элементов сбора или запущен пакет. Не допускает значение NULL.|  
|last_iteration_time|**datetime**|Для непрерывно выполняемых пакетов это время, когда пакет последний раз создал моментальный снимок. Допускает значение NULL.|  
|finish_time|**datetime**|Время окончания выполнения завершенных пакетов и наборов элементов сбора. Допускает значение NULL.|  
|runtime_execution_mode|**smallint**|Указывает на род деятельности набора элементов сбора: сбор данных или их отправка. Допускает значение NULL.<br /><br /> Возможны следующие значения.<br /><br /> 0 = сбор<br /><br /> 1 = передача|  
|status|**smallint**|Указывает текущее состояние набора элементов сбора или пакета. Не допускает значение NULL.<br /><br /> Возможны следующие значения.<br /><br /> 0 = запущен<br /><br /> 1 = завершен<br /><br /> 2 = ошибка|  
|оператор|**nvarchar(128)**|Определяет, кто запустил набор элементов сбора или пакет. Не допускает значение NULL.|  
|package_id|**uniqueidentifier**|Определяет набор элементов сбора или пакет, создавший данную запись журнала. Допускает значение NULL.|  
|package_name|**nvarchar(4000)**|Имя пакета, сформировавшего этот журнал. Допускает значение NULL.|  
|package_execution_id|**uniqueidentifier**|Содержит ссылку на таблицу журнала служб [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Допускает значение NULL.|  
|failure_message|**nvarchar (2048)**|Если набор элементов сбора или пакет завершился с ошибкой, содержит самое последнее сообщение об ошибке для данного компонента. Допускает значение NULL. Чтобы получить более подробные сведения об ошибке, используйте функцию [&#41;fn_syscollector_get_execution_details &#40;Transact-SQL](../../relational-databases/system-functions/fn-syscollector-get-execution-details-transact-sql.md) .|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для роли dc_operator.  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры сборщика данных &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Представления сборщика данных &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)  
  
  
