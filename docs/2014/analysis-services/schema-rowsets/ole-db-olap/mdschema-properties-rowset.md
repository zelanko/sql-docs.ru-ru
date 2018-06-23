---
title: Набор строк MDSCHEMA_PROPERTIES | Документы Microsoft
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
api_name:
- MDSCHEMA_PROPERTIES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_PROPERTIES rowset
ms.assetid: 95c480f7-c525-44ba-a59b-cd36f5855a4f
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7c0e0506be8f531018285bba9145a587448e743e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096945"
---
# <a name="mdschemaproperties-rowset"></a>Набор строк MDSCHEMA_PROPERTIES
  Описывает свойства элементов в базе данных.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `MDSCHEMA_PROPERTIES` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Имя базы данных.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Имя схемы, которой принадлежит это свойство. Имеет значение `NULL`, если поставщик не поддерживает схемы.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Имя куба.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Уникальное имя измерения. Для поставщиков, формирующих уникальные имена путем использования квалификаторов, компоненты имени разделяются между собой.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`||Уникальное имя иерархии. Для поставщиков, формирующих уникальные имена путем использования квалификаторов, компоненты имени разделяются между собой.|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`||Уникальное имя уровня, которому принадлежит это свойство. Если поставщик не поддерживает именованные уровни, он должен вернуть для этого поля значение `DIMENSION_UNIQUE_NAME`. Для поставщиков, формирующих уникальные имена путем использования квалификаторов, компоненты имени разделяются между собой.|  
|`MEMBER_UNIQUE_NAME`|`DBTYPE_WSTR`||Уникальное имя элемента, которому принадлежит свойство. Используется для хранилищ данных, которые не поддерживают именованные уровни или имеют свойства, применяемые отдельно для каждого элемента. Если свойство применяется ко всем элементам на уровне, то этот столбец имеет значение `NULL`. Для поставщиков, формирующих уникальные имена путем использования квалификаторов, компоненты имени разделяются между собой.|  
|`PROPERTY_TYPE`|`DBTYPE_I2`||Битовая карта, указывающая тип свойства.<br /><br /> -   `MDPROP_MEMBER` (`1`) определяет свойство элемента. Это свойство может использоваться в предложении DIMENSION PROPERTIES инструкции SELECT.<br />-   `MDPROP_CELL` (`2`) определяет свойство ячейки. Это свойство может использоваться в предложении CELL PROPERTIES, которое присутствует в конце инструкции SELECT.<br />-   `MDPROP_SYSTEM` (`4`) определяет внутреннее свойство.<br />-   `MDPROP_BLOB` (`8`) определяет свойство, которое содержит большой двоичный объект (blob).|  
|`PROPERTY_NAME`|`DBTYPE_WSTR`||Имя свойства. Если ключ для свойства аналогичен имени для свойства, то `PROPERTY_NAME` будет пустым.|  
|`PROPERTY_CAPTION`|`DBTYPE_WSTR`||Метка или заголовок, связанный со свойством, используемым в основном в целях отображения. Возвращает `PROPERTY_NAME`, если заголовок не существует.|  
|`DATA_TYPE`|`DBTYPE_UI2`||Тип данных свойства.|  
|`CHARACTER_MAXIMUM_LENGTH`|`DBTYPE_UI4`||Максимально возможная длина свойства, если оно имеет символьный, двоичный или битовый тип.<br /><br /> Ноль указывает, что максимальная длина не определена.<br /><br /> Для всех других типов данных возвращается значение `NULL`.|  
|`CHARACTER_OCTET_LENGTH`|`DBTYPE_UI4`||Максимально возможная длина (в байтах) свойства, если оно имеет символьный или двоичный тип.<br /><br /> Ноль указывает, что максимальная длина не определена.<br /><br /> Для всех других типов данных возвращается значение `NULL`.|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||Максимальная точность свойства, если оно имеет числовой тип данных.<br /><br /> Для всех других типов данных возвращается значение `NULL`.|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||Количество цифр справа от запятой, если это тип данных `DBTYPE_NUMERIC` или `DBTYPE_DECIMAL`.<br /><br /> Для всех других типов данных возвращается значение `NULL`.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Понятное описание свойства. Имеет значение `NULL`, если описание отсутствует.|  
|`PROPERTY_CONTENT_TYPE`|`DBTYPE_I2`||Тип свойства. Перечисление может быть одним из следующих.<br /><br /> -   **MD_PROPTYPE_REGULAR** (`0x00`)<br />-   **MD_PROPTYPE_ID** (`0x01`)<br />-   **MD_PROPTYPE_RELATION_TO_PARENT** (`0x02`)<br />-   **MD_PROPTYPE_ROLLUP_OPERATOR** (`0x03`)<br />-   **MD_PROPTYPE_ORG_TITLE** (`0x11`)<br />-   **MD_PROPTYPE_CAPTION** (`0x21`)<br />-   **MD_PROPTYPE_CAPTION_SHORT** (`0x22`)<br />-   **MD_PROPTYPE_CAPTION_DESCRIPTION** (`0x23`)<br />-   **MD_PROPTYPE_CAPTION_ABREVIATION** (`0x24`)<br />-   **MD_PROPTYPE_WEB_URL** (`0x31`)<br />-   **MD_PROPTYPE_WEB_HTML** (`0x32`)<br />-   **MD_PROPTYPE_WEB_XML_OR_XSL** (`0x33`)<br />-   **MD_PROPTYPE_WEB_MAIL_ALIAS** (`0x34`)<br />-   **MD_PROPTYPE_ADDRESS** (`0x41`)<br />-   **MD_PROPTYPE_ADDRESS_STREET** (`0x42`)<br />-   **MD_PROPTYPE_ADDRESS_HOUSE** (`0x43`)<br />-   **MD_PROPTYPE_ADDRESS_CITY** (`0x44`)<br />-   **MD_PROPTYPE_ADDRESS_STATE_OR_PROVINCE** (`0x45`)<br />-   **MD_PROPTYPE_ADDRESS_ZIP** (`0x46`)<br />-   **MD_PROPTYPE_ADDRESS_QUARTER** (`0x47`)<br />-   **MD_PROPTYPE_ADDRESS_COUNTRY** (`0x48`)<br />-   **MD_PROPTYPE_ADDRESS_BUILDING** (`0x49`)<br />-   **MD_PROPTYPE_ADDRESS_ROOM** (`0x4A`)<br />-   **MD_PROPTYPE_ADDRESS_FLOOR** (`0x4B`)<br />-   **MD_PROPTYPE_ADDRESS_FAX** (`0x4C`)<br />-   **MD_PROPTYPE_ADDRESS_PHONE** (`0x4D`)<br />-   **MD_PROPTYPE_GEO_CENTROID_X** (`0x61`)<br />-   **MD_PROPTYPE_GEO_CENTROID_Y** (`0x62`)<br />-   **MD_PROPTYPE_GEO_CENTROID_Z** (`0x63`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_TOP** (`0x64`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_LEFT** (`0x65`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_BOTTOM** (`0x66`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_RIGHT** (`0x67`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_FRONT** (`0x68`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_REAR** (`0x69`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_POLYGON** (`0x6A`)<br />-   **MD_PROPTYPE_PHYSICAL_SIZE** (`0x71`)<br />-   **MD_PROPTYPE_PHYSICAL_COLOR** (`0x72`)<br />-   **MD_PROPTYPE_PHYSICAL_WEIGHT** (`0x73`)<br />-   **MD_PROPTYPE_PHYSICAL_HEIGHT** (`0x74`)<br />-   **MD_PROPTYPE_PHYSICAL_WIDTH** (`0x75`)<br />-   **MD_PROPTYPE_PHYSICAL_DEPTH** (`0x76`)<br />-   **MD_PROPTYPE_PHYSICAL_VOLUME** (`0x77`)<br />-   **MD_PROPTYPE_PHYSICAL_DENSITY** (`0x78`)<br />-   **MD_PROPTYPE_PERSON_FULL_NAME** (`0x82`)<br />-   **MD_PROPTYPE_PERSON_FIRST_NAME** (`0x83`)<br />-   **MD_PROPTYPE_PERSON_LAST_NAME** (`0x84`)<br />-   **MD_PROPTYPE_PERSON_MIDDLE_NAME** (`0x85`)<br />-   **MD_PROPTYPE_PERSON_DEMOGRAPHIC** (`0x86`)<br />-   **MD_PROPTYPE_PERSON_CONTACT** (`0x87`)<br />-   **MD_PROPTYPE_QTY_RANGE_LOW** (`0x91`)<br />-   **MD_PROPTYPE_QTY_RANGE_HIGH** (`0x92`)<br />-   **MD_PROPTYPE_FORMATTING_COLOR** (`0xA1`)<br />-   **MD_PROPTYPE_FORMATTING_ORDER** (`0xA2`)<br />-   **MD_PROPTYPE_FORMATTING_FONT** (`0xA3`)<br />-   **MD_PROPTYPE_FORMATTING_FONT_EFFECTS** (`0xA4`)<br />-   **MD_PROPTYPE_FORMATTING_FONT_SIZE** (`0xA5`)<br />-   **MD_PROPTYPE_FORMATTING_SUB_TOTAL** (`0xA6`)<br />-   **MD_PROPTYPE_DATE** (`0xB1`)<br />-   **MD_PROPTYPE_DATE_START** (`0xB2`)<br />-   **MD_PROPTYPE_DATE_ENDED** (`0xB3`)<br />-   **MD_PROPTYPE_DATE_CANCELED** (`0xB4`)<br />-   **MD_PROPTYPE_DATE_MODIFIED** (`0xB5`)<br />-   **MD_PROPTYPE_DATE_DURATION** (`0xB6`)<br />-   **MD_PROPTYPE_VERSION** (`0xC1`)|  
|`SQL_COLUMN_NAME`|`DBTYPE_WSTR`||Имя свойства, используемого в SQL-запросах из измерения куба или базы данных dDimension.|  
|`LANGUAGE`|`DBTYPE_UI2`||Перевод, выражаемый как `LCID`. Допустимо только для переводов свойств.|  
|`PROPERTY_ORIGIN`|`DBTYPE_UI2`||Определяет тип иерархии, к которой применяется свойство.<br /><br /> -   `MD_USER_DEFINED` (`1`) указывает свойство в пользовательской иерархии<br />-   `MD_SYSTEM_ENABLED` (`2`) указывает свойство в иерархии атрибутов<br />-   `MD_SYSTEM_DISABLED` (`4`) указывает свойство в иерархии атрибутов, не включен.|  
|`PROPERTY_ATTRIBUTE_HIERARCHY_NAME`|`DBTYPE_WSTR`||Имя иерархии атрибутов, являющейся источником для этого свойства.|  
|`PROPERTY_CARDINALITY`|`DBTYPE_WSTR`||Количество элементов свойства. Возможными значениями являются следующие строки:<br /><br /> -   `ONE`<br />-   `MANY`|  
|`MIME_TYPE`|`DBTYPE_WSTR`||Тип MIME для больших двоичных объектов (BLOB).|  
|`PROPERTY_IS_VISIBLE`|`DBTYPE_BOOL`||Логическое значение, показывающее, является ли свойство видимым.<br /><br /> Значение `TRUE`, если свойство является видимым. В противном случае — значение `FALSE`.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `MDSCHEMA_PROPERTIES` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Обязательный|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Необязательно|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Необязательно|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Необязательно|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|Необязательно|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`|Необязательно|  
|`MEMBER_UNIQUE_NAME`|`DBTYPE_WSTR`|Необязательно|  
|`PROPERTY_TYPE`|`DBTYPE_I2`|Необязательно|  
|`PROPERTY_NAME`|`DBTYPE_WSTR`|Необязательно|  
|`PROPERTY_CONTENT_TYPE`|`DBTYPE_I2`|(Необязательно) Задано ограничение по умолчанию для `MDPROP_MEMBER` ИЛИ `MDPROP_CELL`.|  
|`PROPERTY_ORIGIN`|`DBTYPE_UI2`|(Необязательно) Задано ограничение по умолчанию для `MD_USER_DEFINED` ИЛИ `MD_SYSTEM_ENABLED`.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|Битовая карта с одним из следующих допустимых значений (необязательно).<br /><br /> -КУБ 1<br />-2 ИЗМЕРЕНИЯ.<br /><br /> Значение по умолчанию для ограничения — 1.|  
|`PROPERTY_VISIBILITY`|`DBTYPE_UI2`|Битовая карта с одним из следующих допустимых значений (необязательно).<br /><br /> — Visible 1<br />-2 не отображается<br /><br /> Значение по умолчанию для ограничения — 1.|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы OLE DB для OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  