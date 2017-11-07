---
title: "Набор строк MDSCHEMA_PROPERTIES | Документы Microsoft"
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
apiname:
- MDSCHEMA_PROPERTIES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MDSCHEMA_PROPERTIES rowset
ms.assetid: 95c480f7-c525-44ba-a59b-cd36f5855a4f
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6f77505e9daa9efc330bfcd358a37982eace8935
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="mdschemaproperties-rowset"></a>Набор строк MDSCHEMA_PROPERTIES
  Описывает свойства элементов в базе данных.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **MDSCHEMA_PROPERTIES** набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||Имя базы данных.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||Имя схемы, которой принадлежит это свойство. **Значение NULL** Если поставщик не поддерживает схемы.|  
|**CUBE_NAME**|**DBTYPE_WSTR**||Имя куба.|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**||Уникальное имя измерения. Для поставщиков, формирующих уникальные имена путем использования квалификаторов, компоненты имени разделяются между собой.|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**||Уникальное имя иерархии. Для поставщиков, формирующих уникальные имена путем использования квалификаторов, компоненты имени разделяются между собой.|  
|**LEVEL_UNIQUE_NAME**|**DBTYPE_WSTR**||Уникальное имя уровня, которому принадлежит это свойство. Если поставщик не поддерживает именованные уровни, он должен возвращать **DIMENSION_UNIQUE_NAME** значение для этого поля. Для поставщиков, формирующих уникальные имена путем использования квалификаторов, компоненты имени разделяются между собой.|  
|**MEMBER_UNIQUE_NAME**|**DBTYPE_WSTR**||Уникальное имя элемента, которому принадлежит свойство. Используется для хранилищ данных, которые не поддерживают именованные уровни или имеют свойства, применяемые отдельно для каждого элемента. Если свойство применяется ко всем элементам на уровне, этот столбец имеет **NULL**. Для поставщиков, формирующих уникальные имена путем использования квалификаторов, компоненты имени разделяются между собой.|  
|**PROPERTY_TYPE**|**DBTYPE_I2**||Битовая карта, указывающая тип свойства.<br /><br /> **MDPROP_MEMBER** (**1**) определяет свойство элемента. Это свойство может использоваться в предложении DIMENSION PROPERTIES инструкции SELECT.<br /><br /> **MDPROP_CELL** (**2**) определяет свойство ячейки. Это свойство может использоваться в предложении CELL PROPERTIES, которое присутствует в конце инструкции SELECT.<br /><br /> **MDPROP_SYSTEM** (**4**) определяет внутреннее свойство.<br /><br /> **MDPROP_BLOB** (**8**) определяет свойство, которое содержит большой двоичный объект (blob).|  
|**PROPERTY_NAME**|**DBTYPE_WSTR**||Имя свойства. Если ключ для свойства совпадает с именем свойства, **PROPERTY_NAME** будет пустым.|  
|**PROPERTY_CAPTION**|**DBTYPE_WSTR**||Метка или заголовок, связанный со свойством, используемым в основном в целях отображения. Возвращает **PROPERTY_NAME** Если заголовок не существует.|  
|**ТИП ДАННЫХ**|**DBTYPE_UI2**||Тип данных свойства.|  
|**CHARACTER_MAXIMUM_LENGTH**|**DBTYPE_UI4**||Максимально возможная длина свойства, если оно имеет символьный, двоичный или битовый тип.<br /><br /> Ноль указывает, что максимальная длина не определена.<br /><br /> Возвращает **NULL** для всех других типов данных.|  
|**CHARACTER_OCTET_LENGTH**|**DBTYPE_UI4**||Максимально возможная длина (в байтах) свойства, если оно имеет символьный или двоичный тип.<br /><br /> Ноль указывает, что максимальная длина не определена.<br /><br /> Возвращает **NULL** для всех других типов данных.|  
|**NUMERIC_PRECISION**|**DBTYPE_UI2**||Максимальная точность свойства, если оно имеет числовой тип данных.<br /><br /> Возвращает **NULL** для всех других типов данных.|  
|**NUMERIC_SCALE**|**DBTYPE_I2**||Количество цифр справа от десятичной запятой, если это **DBTYPE_NUMERIC** или **DBTYPE_DECIMAL** типа.<br /><br /> Возвращает **NULL** для всех других типов данных.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Понятное описание свойства. **Значение NULL** Если описания не существует.|  
|**PROPERTY_CONTENT_TYPE**|**DBTYPE_I2**||Тип свойства. Перечисление может быть одним из следующих.<br /><br /> **MD_PROPTYPE_REGULAR** (**0x00**)<br /><br /> **MD_PROPTYPE_ID** (**0x01**)<br /><br /> **MD_PROPTYPE_RELATION_TO_PARENT** (**0x02**)<br /><br /> **MD_PROPTYPE_ROLLUP_OPERATOR** (**0x03**)<br /><br /> **MD_PROPTYPE_ORG_TITLE** (**0x11**)<br /><br /> **MD_PROPTYPE_CAPTION** (**0x21**)<br /><br /> **MD_PROPTYPE_CAPTION_SHORT** (**0x22**)<br /><br /> **MD_PROPTYPE_CAPTION_DESCRIPTION** (**0x23**)<br /><br /> **MD_PROPTYPE_CAPTION_ABREVIATION** (**0x24**)<br /><br /> **MD_PROPTYPE_WEB_URL** (**0x31**)<br /><br /> **MD_PROPTYPE_WEB_HTML** (**0x32**)<br /><br /> **MD_PROPTYPE_WEB_XML_OR_XSL** (**0x33**)<br /><br /> **MD_PROPTYPE_WEB_MAIL_ALIAS** (**0x34**)<br /><br /> **MD_PROPTYPE_ADDRESS** (**0x41**)<br /><br /> **MD_PROPTYPE_ADDRESS_STREET** (**0x42**)<br /><br /> **MD_PROPTYPE_ADDRESS_HOUSE** (**0x43**)<br /><br /> **MD_PROPTYPE_ADDRESS_CITY** (**0x44**)<br /><br /> **MD_PROPTYPE_ADDRESS_STATE_OR_PROVINCE** (**0x45**)<br /><br /> **MD_PROPTYPE_ADDRESS_ZIP** (**0x46**)<br /><br /> **MD_PROPTYPE_ADDRESS_QUARTER** (**0x47**)<br /><br /> **MD_PROPTYPE_ADDRESS_COUNTRY** (**0x48**)<br /><br /> **MD_PROPTYPE_ADDRESS_BUILDING** (**0x49**)<br /><br /> **MD_PROPTYPE_ADDRESS_ROOM** (**0x4A**)<br /><br /> **MD_PROPTYPE_ADDRESS_FLOOR** (**0x4B**)<br /><br /> **MD_PROPTYPE_ADDRESS_FAX** (**0x4C**)<br /><br /> **MD_PROPTYPE_ADDRESS_PHONE** (**0x4D**)<br /><br /> **MD_PROPTYPE_GEO_CENTROID_X** (**0x61**)<br /><br /> **MD_PROPTYPE_GEO_CENTROID_Y** (**0x62**)<br /><br /> **MD_PROPTYPE_GEO_CENTROID_Z** (**0x63**)<br /><br /> **MD_PROPTYPE_GEO_BOUNDARY_TOP** (**0x64**)<br /><br /> **MD_PROPTYPE_GEO_BOUNDARY_LEFT** (**0x65**)<br /><br /> **MD_PROPTYPE_GEO_BOUNDARY_BOTTOM** (**0x66**)<br /><br /> **MD_PROPTYPE_GEO_BOUNDARY_RIGHT** (**0x67**)<br /><br /> **MD_PROPTYPE_GEO_BOUNDARY_FRONT** (**0x68**)<br /><br /> **MD_PROPTYPE_GEO_BOUNDARY_REAR** (**0x69**)<br /><br /> **MD_PROPTYPE_GEO_BOUNDARY_POLYGON** (**0x6A**)<br /><br /> **MD_PROPTYPE_PHYSICAL_SIZE** (**0x71**)<br /><br /> **MD_PROPTYPE_PHYSICAL_COLOR** (**0x72**)<br /><br /> **MD_PROPTYPE_PHYSICAL_WEIGHT** (**0x73**)<br /><br /> **MD_PROPTYPE_PHYSICAL_HEIGHT** (**0х74 —**)<br /><br /> **MD_PROPTYPE_PHYSICAL_WIDTH** (**0x75**)<br /><br /> **MD_PROPTYPE_PHYSICAL_DEPTH** (**0x76**)<br /><br /> **MD_PROPTYPE_PHYSICAL_VOLUME** (**0x77**)<br /><br /> **MD_PROPTYPE_PHYSICAL_DENSITY** (**0x78**)<br /><br /> **MD_PROPTYPE_PERSON_FULL_NAME** (**0x82**)<br /><br /> **MD_PROPTYPE_PERSON_FIRST_NAME** (**0x83**)<br /><br /> **MD_PROPTYPE_PERSON_LAST_NAME** (**0x84**)<br /><br /> **MD_PROPTYPE_PERSON_MIDDLE_NAME** (**0x85**)<br /><br /> **MD_PROPTYPE_PERSON_DEMOGRAPHIC** (**0x86**)<br /><br /> **MD_PROPTYPE_PERSON_CONTACT** (**0x87**)<br /><br /> **MD_PROPTYPE_QTY_RANGE_LOW** (**0x91**)<br /><br /> **MD_PROPTYPE_QTY_RANGE_HIGH** (**0x92**)<br /><br /> **MD_PROPTYPE_FORMATTING_COLOR** (**0xA1**)<br /><br /> **MD_PROPTYPE_FORMATTING_ORDER** (**0xA2**)<br /><br /> **MD_PROPTYPE_FORMATTING_FONT** (**0xA3**)<br /><br /> **MD_PROPTYPE_FORMATTING_FONT_EFFECTS** (**0xA4**)<br /><br /> **MD_PROPTYPE_FORMATTING_FONT_SIZE** (**0xA5**)<br /><br /> **MD_PROPTYPE_FORMATTING_SUB_TOTAL** (**0xA6**)<br /><br /> **MD_PROPTYPE_DATE** (**0xB1**)<br /><br /> **MD_PROPTYPE_DATE_START** (**0xB2**)<br /><br /> **MD_PROPTYPE_DATE_ENDED** (**0xB3**)<br /><br /> **MD_PROPTYPE_DATE_CANCELED** (**0xB4**)<br /><br /> **MD_PROPTYPE_DATE_MODIFIED** (**0xB5**)<br /><br /> **MD_PROPTYPE_DATE_DURATION** (**0xB6**)<br /><br /> **MD_PROPTYPE_VERSION** (**0xC1**)|  
|**SQL_COLUMN_NAME**|**DBTYPE_WSTR**||Имя свойства, используемого в SQL-запросах из измерения куба или базы данных dDimension.|  
|**LANGUAGE**|**DBTYPE_UI2**||Перевод, выражаемый как **LCID**. Допустимо только для переводов свойств.|  
|**PROPERTY_ORIGIN**|**DBTYPE_UI2**||Определяет тип иерархии, к которой применяется свойство.<br /><br /> **MD_USER_DEFINED** (**1**) указывает свойство в пользовательской иерархии<br /><br /> **MD_SYSTEM_ENABLED** (**2**) указывает свойство в иерархии атрибутов<br /><br /> **MD_SYSTEM_DISABLED** (**4**) указывает свойство в иерархии атрибутов, не включен.|  
|**PROPERTY_ATTRIBUTE_HIERARCHY_NAME**|**DBTYPE_WSTR**||Имя иерархии атрибутов, являющейся источником для этого свойства.|  
|**PROPERTY_CARDINALITY**|**DBTYPE_WSTR**||Количество элементов свойства. Возможными значениями являются следующие строки:<br /><br /> **ОДИН**<br /><br /> **МНОГИЕ**|  
|**MIME_TYPE**|**DBTYPE_WSTR**||Тип MIME для больших двоичных объектов (BLOB).|  
|**PROPERTY_IS_VISIBLE**|**DBTYPE_BOOL**||Логическое значение, показывающее, является ли свойство видимым.<br /><br /> **Значение TRUE,** Если свойство является видимым; в противном случае — **FALSE**.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 **MDSCHEMA_PROPERTIES** строк может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Обязательный|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Необязательно|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Необязательно|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|Необязательно|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|Необязательно|  
|**LEVEL_UNIQUE_NAME**|**DBTYPE_WSTR**|Необязательно|  
|**MEMBER_UNIQUE_NAME**|**DBTYPE_WSTR**|Необязательно|  
|**PROPERTY_TYPE**|**DBTYPE_I2**|Необязательно|  
|**PROPERTY_NAME**|**DBTYPE_WSTR**|Необязательно|  
|**PROPERTY_CONTENT_TYPE**|**DBTYPE_I2**|(Необязательно) Ограничение по умолчанию включен в месте **MDPROP_MEMBER** или **MDPROP_CELL**.|  
|**PROPERTY_ORIGIN**|**DBTYPE_UI2**|(Необязательно) Ограничение по умолчанию включен в месте **MD_USER_DEFINED** или **MD_SYSTEM_ENABLED**.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(Необязательно) Ограничение по умолчанию имеет значение 1.  Битовая карта с одним из следующих допустимых значений:<br /><br /> 1 CUBE<br /><br /> 2 DIMENSION|  
|**PROPERTY_VISIBILITY**|**DBTYPE_UI2**|(Необязательно) Ограничение по умолчанию имеет значение 1. Битовая карта с одним из следующих допустимых значений:<br /><br /> 1 Отображается<br /><br /> 2 Не отображается|  
  
## <a name="see-also"></a>См. также:  
 [OLE DB для OLAP наборы строк схемы](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  

