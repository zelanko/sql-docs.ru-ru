---
title: "Набор строк DISCOVER_STORAGE_TABLE_COLUMNS | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
ms.assetid: 24abb88e-33a9-4ae2-829d-cdef0ff22ec1
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6ca81b54546e3ff69c42ea60484e462513443c5e
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="discoverstoragetablecolumns-rowset"></a>Набор строк DISCOVER_STORAGE_TABLE_COLUMNS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Предоставляет сведения на уровне столбцов о таблицах хранилища, используемых в базе данных служб Analysis Services в SharePoint или Табличный режим.  
  
 **Применимо к:** табличные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **DISCOVER_STORAGE_TABLE_COLUMNS** набор строк содержит следующие столбцы.  
  
|**Имя столбца**|**Индикатор типа**|**Ограничение**|**Description**|  
|---------------------|------------------------|---------------------|---------------------|  
|**ИМЯ_БАЗЫ_ДАННЫХ**|**DBTYPE_WSTR**|Да|Указывает имя базы данных, содержащей эти таблицы. Если отсутствует, используется текущая база данных.<br /><br /> **DISCOVER_STORAGE_TABLE_COLUMNS** строк может быть ограничен с помощью этого столбца.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Да|Указывает куб или модель, содержащие эти таблицы.<br /><br /> С помощью этого столбца можно ограничить набор строк **DISCOVER_STORAGE_TABLES** .|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**|Да|Имя группы мер.|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**||Имя измерения.|  
|**ATTRIBUTE_NAME**|**DBTYPE_WSTR**||Имя атрибута.|  
|**TABLE_ID**|**DBTYPE_WSTR**||Идентификатор таблицы.|  
|**ИДЕНТИФИКАТОР COLUMN_ID**|**DBTYPE_ WSTR**||Идентификатор столбца. Идентификатор столбца является внутренним для подсистемы VertiPaq аналитики в памяти xVelocity и используется только в справочных целях.|  
|**COLUMN_TYPE**|**DBTYPE_WSTR**||Тип столбца. Тип столбца является внутренним для подсистемы VertiPaq аналитики в памяти xVelocity и используется только в справочных целях.<br /><br /> BASIC_DATA<br /><br /> HIERARCHY_DATAID_TO_POSITION<br /><br /> HIERARCHY_POSITION_TO_DATAID<br /><br /> RELATIONSHIP|  
|**COLUMN_ENCODING**|**DBTYPE_UI8**||Целое число, представляющее тип кодировки, применяемой для столбца данных.<br /><br /> **0**вместе с **COLUMN_TYPE**: HIERARCHY_DATAID_TO_POSITION HIERARCHY_POSITION_TO_DATAID, СВЯЗИ<br /><br /> **1**вместе с **COLUMN_TYPE**: BASIC_DATA<br /><br /> **2**вместе с **COLUMN_TYPE**: BASIC_DATA|  
|**ТИП ДАННЫХ**|**DBTYPE_WSTR**||Тип данных столбца. Имеет следующие возможные значения:<br /><br /> DBTYPE_BOOL<br /><br /> DBTYPE_CY<br /><br /> DBTYPE_DATE<br /><br /> DBTYPE_I4<br /><br /> DBTYPE_I8<br /><br /> DBTYPE_R8<br /><br /> DBTYPE_WSTR<br /><br /> Недоступно|  
|**ISKEY**|**DBTYPE_BOOL**||**Значение true,** Если столбец используется в качестве первичного или внешнего ключа; в противном случае **false**.|  
|**ISUNIQUE**|**DBTYPE_BOOL**||**Значение true,** Если значения в столбце уникальных; в противном случае **false**.|  
|**ISNULLABLE**|**DBTYPE_BOOL**||**Значение true,** Если столбец допускает значения NULL; в противном случае **false**.|  
|**ISROWNUMBER**|**DBTYPE_BOOL**||**Значение true,** Если столбец является столбцом номеров строк. Столбцы с номерами строк для внутреннего использования подсистемой аналитики в памяти xVelocity.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd44-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|StorageTableColumns|  
  
## <a name="example"></a>Пример  
 В следующем образце кода используется запрос динамического административного представления для возврата результирующего набора.  
  
```  
SELECT *  
FROM $System.DISCOVER_STORAGE_TABLE_COLUMNS  
ORDER BY TABLE_ID DESC  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы служб Analysis Services](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
