---
title: Набор строк DISCOVER_COMMAND_OBJECTS | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- DISCOVER_COMMAND_OBJECTS rowset
ms.assetid: 325114ee-3a50-4504-9782-dbf7c1a44778
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e2bebb8f25bcf8c38b6422ad27ffa865d328be45
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48177994"
---
# <a name="discovercommandobjects-rowset"></a>Набор строк DISCOVER_COMMAND_OBJECTS
  Предоставляет сведения по использованию ресурсов и активности для объектов, которые используются указанной командой.  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_COMMAND_OBJECTS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Ограничение|Описание|  
|-----------------|--------------------|-----------------|-----------------|  
|`SESSION_SPID`|`DBTYPE_I4`|Да|Идентификатор сеанса.|  
|`SESSION_ID`|`DBTYPE_WSTR`|Да|Уникальный идентификатор сеанса в виде идентификатора GUID.|  
|`SESSION_COMMAND_COUNT`|`DBTYPE_I4`||Порядковый номер команды.|  
|`OBJECT_PARENT_PATH`|`DBTYPE_WSTR`|Да|Путь к родительскому объекту для текущего объекта.|  
|`OBJECT_ID`|`DBTYPE_WSTR`|Да|Идентификатор объекта, заданный при его создании.|  
|`OBJECT_VERSION`|`DBTYPE_I4`||Номер версии метаданных для объекта. Этот номер изменяется при каждом изменении объекта.|  
|`OBJECT_DATA_VERSION`|`DBTYPE_I4`||Номер журнала обращений и преобразований для данных в объекте. Этот номер увеличивается каждый раз при обработке объекта.|  
|`OBJECT_CPU_TIME_MS`|`DBTYPE_I8`||Время ЦП в миллисекундах, израсходованное объектом с момента запуска команды.|  
|`OBJECT_READ_KB`|`DBTYPE_I8`||Общий объем данных (в килобайтах), считанных объектом с момента запуска команды.|  
|`OBJECT_READS`|`DBTYPE_I8`||Общее число операций считывания, выполненных объектом с момента запуска команды.|  
|`OBJECT_WRITE_KB`|`DBTYPE_I8`||Общий объем данных в килобайтах, записанный объектом с момента запуска команды.|  
|`OBJECT_WRITES`|`DBTYPE_I8`||Общее число операций записи, выполненных объектом с момента запуска команды.|  
|`OBJECT_ROWS_RETURNED`|`DBTYPE_I8`||Число строк, возвращенное объектом вызывающему объекту с момента запуска команды.|  
|`OBJECT_ROWS_SCANNED`|`DBTYPE_I8`||Число строк, которые просмотрел объект с момента запуска команды.|  
  
 Этот набор строк схемы не отсортирован.  
  
> [!IMPORTANT]  
>  Набор строк схемы DISCOVER_COMMAND_OBJECTS не сообщает о действиях через запросы динамического административного представления.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd35-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|CommandObjects|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы XML для аналитики](xml-for-analysis-schema-rowsets.md)  
  
  
