---
title: Набор строк DISCOVER_COMMAND_OBJECTS | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 789f1bf7bb4ba9c85ecc1a09a69d1542255f184b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="discovercommandobjects-rowset"></a>Набор строк DISCOVER_COMMAND_OBJECTS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Предоставляет сведения по использованию ресурсов и активности для объектов, которые используются указанной командой.  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_COMMAND_OBJECTS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Ограничение|Описание|  
|-----------------|--------------------|-----------------|-----------------|  
|**SESSION_SPID**|**DBTYPE_I4**|Да|Идентификатор сеанса.|  
|**SESSION_ID**|**DBTYPE_WSTR**|Да|Уникальный идентификатор сеанса в виде идентификатора GUID.|  
|**SESSION_COMMAND_COUNT**|**DBTYPE_I4**||Порядковый номер команды.|  
|**OBJECT_PARENT_PATH**|**DBTYPE_WSTR**|Да|Путь к родительскому объекту для текущего объекта.|  
|**OBJECT_ID**|**DBTYPE_WSTR**|Да|Идентификатор объекта, заданный при его создании.|  
|**OBJECT_VERSION**|**DBTYPE_I4**||Номер версии метаданных для объекта. Этот номер изменяется при каждом изменении объекта.|  
|**OBJECT_DATA_VERSION**|**DBTYPE_I4**||Номер журнала обращений и преобразований для данных в объекте. Этот номер увеличивается каждый раз при обработке объекта.|  
|**OBJECT_CPU_TIME_MS**|**DBTYPE_I8**||Время ЦП в миллисекундах, израсходованное объектом с момента запуска команды.|  
|**OBJECT_READ_KB**|**DBTYPE_I8**||Общий объем данных (в килобайтах), считанных объектом с момента запуска команды.|  
|**OBJECT_READS**|**DBTYPE_I8**||Общее число операций считывания, выполненных объектом с момента запуска команды.|  
|**OBJECT_WRITE_KB**|**DBTYPE_I8**||Общий объем данных в килобайтах, записанный объектом с момента запуска команды.|  
|**OBJECT_WRITES**|**DBTYPE_I8**||Общее число операций записи, выполненных объектом с момента запуска команды.|  
|**OBJECT_ROWS_RETURNED**|**DBTYPE_I8**||Число строк, возвращенное объектом вызывающему объекту с момента запуска команды.|  
|**OBJECT_ROWS_SCANNED**|**DBTYPE_I8**||Число строк, которые просмотрел объект с момента запуска команды.|  
  
 Этот набор строк схемы не отсортирован.  
  
> [!IMPORTANT]  
>  Набор строк схемы DISCOVER_COMMAND_OBJECTS не сообщает о действиях через запросы динамического административного представления.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd35-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|CommandObjects|  
  
## <a name="see-also"></a>См. также  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
