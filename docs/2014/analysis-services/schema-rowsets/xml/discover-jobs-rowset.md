---
title: Набор строк DISCOVER_JOBS | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DISCOVER_JOBS rowset
ms.assetid: b4d83bb6-aed3-4513-b516-cefadf95dad2
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6a23a3e3dae0a03bf31a7b73b8cb505e834cff27
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37246064"
---
# <a name="discoverjobs-rowset"></a>Набор строк DISCOVER_JOBS
  Предоставляет сведения о текущих заданиях, выполняющихся на сервере. Задание представляет собой часть команды, которая осуществляет конкретную задачу в целях выполнения команды.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_JOBS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`JOB_CREATION_TIME`|`DBTYPE_DBTIMESTAMP`||Дата и время создания задания на сервере в формате UTC.|  
|`JOB_DESCRIPTION`|`DBTYPE_WSTR`||Описание задания, назначенного службой сервера.|  
|`JOB_EXECUTION_TIME_MS`|`DBTYPE_I8`||Время в миллисекундах, в течение которого задание является активным.|  
|`JOB_ID`|`DBTYPE_I4`||Уникальный идентификатор задания.|  
|`JOB_START_TIME`|`DBTYPE_DBTIMESTAMP`||Дата и время запуска задания на сервере в формате UTC.|  
|`JOB_THREADPOOL_ID`|`DBTYPE_I4`||Пул потоков, из которого выполнен запуск текущего задания.|  
|`JOB_TOTAL_TIME_MS`|`DBTYPE_I8`||Время в миллисекундах с начала запуска задания.|  
|`SPID`|`DBTYPE_I4`||Идентификатор сеанса.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DISCOVER_JOBS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|SPID|DBTYPE_I4|Необязательный параметр.|  
|JOB_ID|DBTYPE_I4|Необязательный параметр.|  
|JOB_DESCRIPTION|DBTYPE_WSTR|Необязательный параметр.|  
|JOB_THREADPOOL_ID|DBTYPE_I4|Необязательный параметр.|  
|JOB_MIN TOTAL_TIME_MS|DBTYPE_I8|Необязательный параметр.|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы XML для аналитики](xml-for-analysis-schema-rowsets.md)  
  
  
