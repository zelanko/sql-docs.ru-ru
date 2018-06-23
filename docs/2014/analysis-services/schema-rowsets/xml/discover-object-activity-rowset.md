---
title: Набор строк DISCOVER_OBJECT_ACTIVITY | Документы Microsoft
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
- DISCOVER_OBJECT_ACTIVITY rowset
ms.assetid: 100f7de1-ad5c-4973-b863-3c10df1245c4
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b5ab904cff026149194c3bd2d242ab448da4be89
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195025"
---
# <a name="discoverobjectactivity-rowset"></a>Набор строк DISCOVER_OBJECT_ACTIVITY
  Предоставляет сведения об использовании ресурсов каждым объектом с начала работы службы.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_OBJECT_ACTIVITY` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`OBJECT_AGGREGATION_HIT`|`DBTYPE_I8`||Количество случаев обнаружения в кэше результатов статистической обработки объекта с начала работы службы.|  
|`OBJECT_AGGREGATION_MISS`|`DBTYPE_I8`||Количество случаев, в которых не произошло обращение в кэш за существующими результатами статистической обработки объекта (т.е. в которых эти результаты не были использованы) с начала работы службы.|  
|`OBJECT_CPU_TIME_MS`|`DBTYPE_I8`||Время ЦП в миллисекундах, израсходованное объектом с начала работы службы.|  
|`OBJECT_DATA_VERSION`|`DBTYPE_I4`||Номер в журнале обращений и преобразований для данных этого объекта; этот номер возрастает после каждой обработки объекта.|  
|`OBJECT_HIT`|`DBTYPE_I8`||Количество случаев обнаружения объекта в кэше с начала работы службы.|  
|`OBJECT_ID`|`DBTYPE_WSTR`||Идентификатор объекта, определенный во время создания|  
|`OBJECT_MISS`|`DBTYPE_I8`||Количество случаев, в которых объект не был обнаружен в кэше с начала работы службы.|  
|`OBJECT_PARENT_PATH`|`DBTYPE_WSTR`||Путь к родительскому объекту текущего объекта.|  
|`OBJECT_READ_KB`|`DBTYPE_I8`||Накопленные данные о количестве данных в килобайтах, считанных объектом с начала работы службы.|  
|`OBJECT_READS`|`DBTYPE_I8`||Накопленные данные о количестве операций чтения, выполненных объектом с начала работы службы.|  
|`OBJECT_ROWS_RETURNED`|`DBTYPE_I8`||Количество строк, возвращенных объектом вызывающему объекту с начала работы службы.|  
|`OBJECT_ROWS_SCANNED`|`DBTYPE_I8`||Количество строк, просмотренных объектом с начала работы службы.|  
|`OBJECT_VERSION`|`DBTYPE_I4`||Номер версии метаданных для объекта. Этот номер изменяется при каждом изменении объекта.|  
|`OBJECT_WRITE_KB`|`DBTYPE_I8`||Накопленные данные о количестве данных в килобайтах, записанных объектом с начала работы службы.|  
|`OBJECT_WRITES`|`DBTYPE_I8`||Накопленные данные о количестве операций записи, выполненных объектом с начала работы службы.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DISCOVER_OBJECT_ACTIVTY` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|OBJECT_PARENT_PATH|DBTYPE_WSTR|Необязательный параметр.|  
|OBJECT_ID|DBTYPE_WSTR|Необязательный параметр.|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы XML для аналитики](xml-for-analysis-schema-rowsets.md)  
  
  