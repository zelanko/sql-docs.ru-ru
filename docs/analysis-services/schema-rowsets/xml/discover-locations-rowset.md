---
title: Набор строк DISCOVER_LOCATIONS | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 63a3f01b25b189f34df3f328c1709255752f7210
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="discoverlocations-rowset"></a>Набор строк DISCOVER_LOCATIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Возвращает сведения о содержимом файла резервной копии. Необходимо иметь разрешение на доступ к папке с резервными файлами.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_LOCATIONS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Ограничение|Описание|  
|-----------------|--------------------|-----------------|-----------------|  
|**LOCATION_BACKUP_FILE_PATHNAME**|**DBTYPE_WSTR**|Обязательно, см. ниже.|Расположение файла резервной копии.|  
|**LOCATION_PARTITION_OBJECTPATH**|**DBTYPE_WSTR**||Путь к секции относительно папки данных.|  
|**LOCATION_PARTITION_DATASOURCEID**|**DBTYPE_WSTR**||Идентификатор источника данных, используемый для обработки секции.|  
|**LOCATION_PARTITION_DATASOURCENAME**|**DBTYPE_WSTR**||Имя источника данных, используемого для обработки.|  
|**LOCATION_PARTITION_NAME**|**DBTYPE_WSTR**||Имя секции.|  
|**LOCATION_PARTITION_SIZE**|**DBTYPE_WSTR**||Приблизительный размер секции.|  
|**LOCATION_CONNECTION_STRING**|**DBTYPE_WSTR**||Строка подключения для источника данных, используемого в обработке.|  
|**LOCATION_PARTITION_FOLDER**|**DBTYPE_WSTR**||Исходное расположение этой секции при создании файла резервной копии.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DISCOVER_LOCATIONS** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**LOCATION_BACKUP_FILE_PATHNAME**|**DBTYPE_WSTR**|Обязательно|  
|**LOCATION_PASSWORD PF_DBTYPE**|**DBTYPE_WSTR**|Требуется, если был указан во время резервного копирования. Это ограничение не используется для ограничения возвращаемых строк. Оно используется для задания пароля для доступа к папке.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd92-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|Расположения|  
  
## <a name="see-also"></a>См. также  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
