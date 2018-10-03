---
title: Набор строк DISCOVER_STORAGE_TABLE_COLUMNS | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 24abb88e-33a9-4ae2-829d-cdef0ff22ec1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 240230784860e9484ebc03ba6740eaf5d56387fa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48089074"
---
# <a name="discoverstoragetablecolumns-rowset"></a>Набор строк DISCOVER_STORAGE_TABLE_COLUMNS
  Содержит сведения на уровне столбцов о таблицах хранилища, используемых в базе данных служб Analysis Services в режиме SharePoint или табличном режиме.  
  
 **Применимо к:** табличные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_STORAGE_TABLE_COLUMNS` Набор строк содержит следующие столбцы.  
  
|**Имя столбца**|**Индикатор типа**|**Ограничение**|**Описание**|  
|---------------------|------------------------|---------------------|---------------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Да|Указывает имя базы данных, содержащей эти таблицы. Если отсутствует, используется текущая база данных.<br /><br /> `DISCOVER_STORAGE_TABLE_COLUMNS` Набора строк можно ограничить с помощью этого столбца.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Да|Указывает куб или модель, содержащие эти таблицы.<br /><br /> `DISCOVER_STORAGE_TABLES` Набора строк можно ограничить с помощью этого столбца.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|Да|Имя группы мер.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||Имя измерения.|  
|`ATTRIBUTE_NAME`|`DBTYPE_WSTR`||Имя атрибута.|  
|`TABLE_ID`|`DBTYPE_WSTR`||Идентификатор таблицы.|  
|`COLUMN_ID`|`DBTYPE_ WSTR`||Идентификатор столбца. Идентификатор столбца является внутренним для подсистемы VertiPaq аналитики в памяти xVelocity и используется только в справочных целях.|  
|`COLUMN_TYPE`|`DBTYPE_WSTR`||Тип столбца. Тип столбца является внутренним для подсистемы VertiPaq аналитики в памяти xVelocity и используется только в справочных целях.<br /><br /> -BASIC_DATA<br />-HIERARCHY_DATAID_TO_POSITION<br />-HIERARCHY_POSITION_TO_DATAID<br />-СВЯЗЬ|  
|`COLUMN_ENCODING`|`DBTYPE_UI8`||Целое число, представляющее тип кодировки, применяемой для столбца данных.<br /><br /> -   **0**, которое используется с `COLUMN_TYPE`: HIERARCHY_DATAID_TO_POSITION, HIERARCHY_POSITION_TO_DATAID, СВЯЗИ<br />-   **1**, которое используется с `COLUMN_TYPE`: BASIC_DATA<br />-   **2**, которое используется с `COLUMN_TYPE`: BASIC_DATA|  
|`DATATYPE`|`DBTYPE_WSTR`||Тип данных столбца. Имеет следующие возможные значения:<br /><br /> -DBTYPE_BOOL<br />-DBTYPE_CY<br />— DBTYPE_DATE<br />-DBTYPE_I4<br />-DBTYPE_I8<br />-DBTYPE_R8<br />-DBTYPE_WSTR<br />-Н/Д|  
|`ISKEY`|`DBTYPE_BOOL`||`True`, если столбец используется как первичный или внешний ключ. В противном случае — `false`.|  
|`ISUNIQUE`|`DBTYPE_BOOL`||`True`, если значения в столбце уникальны. В противном случае — `false`.|  
|`ISNULLABLE`|`DBTYPE_BOOL`||`True`, если столбец имеет значение NULL. В противном случае — `false`.|  
|`ISROWNUMBER`|`DBTYPE_BOOL`||Значение `True`, если столбец является столбцом номеров строк. Столбцы с номерами строк для внутреннего использования подсистемой аналитики в памяти xVelocity.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
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
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы служб Analysis Services](../analysis-services-schema-rowsets.md)  
  
  
