---
title: "Набор строк DISCOVER_JOBS | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_JOBS rowset
ms.assetid: b4d83bb6-aed3-4513-b516-cefadf95dad2
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e1f7ac112f3fcae70751f02038d0257231600b56
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="discoverjobs-rowset"></a>Набор строк DISCOVER_JOBS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Сведения о текущих заданиях, выполняющихся на сервере. Задание представляет собой часть команды, которая осуществляет конкретную задачу в целях выполнения команды.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_JOBS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
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
|SPID|DBTYPE_I4|Необязательный параметр.|  
|JOB_ID|DBTYPE_I4|Необязательный параметр.|  
|JOB_DESCRIPTION|DBTYPE_WSTR|Необязательный параметр.|  
|JOB_THREADPOOL_ID|DBTYPE_I4|Необязательный параметр.|  
|JOB_MIN TOTAL_TIME_MS|DBTYPE_I8|Необязательно.|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы XML для аналитики](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
