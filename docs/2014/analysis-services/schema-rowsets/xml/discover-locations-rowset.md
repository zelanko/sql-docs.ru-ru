---
title: Набор строк DISCOVER_LOCATIONS | Документы Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6d3a1171-8e4d-4022-ade0-b785cf795d70
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: cfcc451a3369a3f15e29381df3d21e7275a90f7f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190083"
---
# <a name="discoverlocations-rowset"></a>Набор строк DISCOVER_LOCATIONS
  Возвращает сведения о содержимом файла резервной копии. Необходимо иметь разрешение на доступ к папке с резервными файлами.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_LOCATIONS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Ограничение|Описание|  
|-----------------|--------------------|-----------------|-----------------|  
|`LOCATION_BACKUP_FILE_PATHNAME`|`DBTYPE_WSTR`|Обязательно, см. ниже.|Расположение файла резервной копии.|  
|`LOCATION_PARTITION_OBJECTPATH`|`DBTYPE_WSTR`||Путь к секции относительно папки данных.|  
|`LOCATION_PARTITION_DATASOURCEID`|`DBTYPE_WSTR`||Идентификатор источника данных, используемый для обработки секции.|  
|`LOCATION_PARTITION_DATASOURCENAME`|`DBTYPE_WSTR`||Имя источника данных, используемого для обработки.|  
|`LOCATION_PARTITION_NAME`|`DBTYPE_WSTR`||Имя секции.|  
|`LOCATION_PARTITION_SIZE`|`DBTYPE_WSTR`||Приблизительный размер секции.|  
|`LOCATION_CONNECTION_STRING`|`DBTYPE_WSTR`||Строка подключения для источника данных, используемого в обработке.|  
|`LOCATION_PARTITION_FOLDER`|`DBTYPE_WSTR`||Исходное расположение этой секции при создании файла резервной копии.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DISCOVER_LOCATIONS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`LOCATION_BACKUP_FILE_PATHNAME`|`DBTYPE_WSTR`|Обязательно|  
|`LOCATION_PASSWORD PF_DBTYPE`|`DBTYPE_WSTR`|Требуется, если был указан во время резервного копирования. Это ограничение не используется для ограничения возвращаемых строк. Оно используется для задания пароля для доступа к папке.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd92-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|Расположения|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы XML для аналитики](xml-for-analysis-schema-rowsets.md)  
  
  