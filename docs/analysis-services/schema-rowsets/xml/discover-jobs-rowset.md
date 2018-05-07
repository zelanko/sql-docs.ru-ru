---
title: Набор строк DISCOVER_JOBS | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f262e4d0b486676eb9f541fbd7d5c0e2866a07ae
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="discoverjobs-rowset"></a>Набор строк DISCOVER_JOBS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Предоставляет сведения о текущих заданиях, выполняющихся на сервере. Задание представляет собой часть команды, которая осуществляет конкретную задачу в целях выполнения команды.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_JOBS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|**JOB_CREATION_TIME**|**DBTYPE_DBTIMESTAMP**||Дата и время создания задания на сервере в формате UTC.|  
|**JOB_DESCRIPTION**|**DBTYPE_WSTR**||Описание задания, назначенного службой сервера.|  
|**JOB_EXECUTION_TIME_MS**|**DBTYPE_I8**||Время в миллисекундах, в течение которого задание является активным.|  
|**АРГУМЕНТ JOB_ID**|**DBTYPE_I4**||Уникальный идентификатор задания.|  
|**JOB_START_TIME**|**DBTYPE_DBTIMESTAMP**||Дата и время запуска задания на сервере в формате UTC.|  
|**JOB_THREADPOOL_ID**|**DBTYPE_I4**||Пул потоков, из которого выполнен запуск текущего задания.|  
|**JOB_TOTAL_TIME_MS**|**DBTYPE_I8**||Время в миллисекундах с начала запуска задания.|  
|**SPID**|**DBTYPE_I4**||Идентификатор сеанса.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DISCOVER_JOBS** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|SPID|DBTYPE_I4|Необязательно.|  
|JOB_ID|DBTYPE_I4|Необязательно.|  
|JOB_DESCRIPTION|DBTYPE_WSTR|Необязательно.|  
|JOB_THREADPOOL_ID|DBTYPE_I4|Необязательно.|  
|JOB_MIN TOTAL_TIME_MS|DBTYPE_I8|Необязательно.|  
  
## <a name="see-also"></a>См. также  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
