---
title: "Набор строк DISCOVER_COMMANDS | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_COMMANDS rowset
ms.assetid: d228f265-05d9-4d2c-a622-44c73eab7a71
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 49d95852f838c67a34e175ed160c6abdad93bd61
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="discovercommands-rowset"></a>Набор строк DISCOVER_COMMANDS
  Предоставляет сведения об использовании ресурсов и действиях, касающиеся выполняемых в настоящее время или последних выполненных команд в соединениях, открытых на сервере.  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_COMMANDS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Ограничение|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**SESSION_SPID**|**DBTYPE_I4**|Да|Идентификатор сеанса.|  
|**SESSION_COMMAND_COUNT**|**DBTYPE_I4**||Количество команд, выполненных с начала сеанса.|  
|**COMMAND_START_TIME**|**DBTYPE_DBTIMESTAMP**||Дата и время последнего запуска команды, выраженные как время в формате UTC на сервере.|  
|**COMMAND_ELAPSED_TIME_MS**|**DBTYPE_I8**||Общее затраченное время в миллисекундах после начала выполнения команды.|  
|**COMMAND_CPU_TIME_MS**|**DBTYPE_I8**||Время ЦП в миллисекундах, израсходованное командой после начала выполнения команды.|  
|**COMMAND_READS**|**DBTYPE_I8**||Накопленные данные о количестве операций чтения с диска после начала выполнения команды.|  
|**COMMAND_READ_KB**|**DBTYPE_I8**||Накопленные данные о количестве данных в килобайтах, считанных с диска после начала выполнения команды.|  
|**COMMAND_WRITES**|**DBTYPE_I8**||Накопленные данные о количестве операций записей на диск после начала выполнения команды.|  
|**COMMAND_WRITE_KB**|**DBTYPE_I8**||Накопленные данные о количестве данных в килобайтах, записанных на диск после начала выполнения команды.|  
|**COMMAND_TEXT**|**DBTYPE_WSTR**||Текст команды.|  
|**COMMAND_END_TIME**|**DBTYPE_DBTIMESTAMP**||Дата и время сервера в формате UTC на момент завершения выполнения команды.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd34-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|Команды|  
  
## <a name="see-also"></a>См. также:  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

