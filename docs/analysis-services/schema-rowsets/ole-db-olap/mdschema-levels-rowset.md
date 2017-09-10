---
title: "Набор строк MDSCHEMA_LEVELS | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MDSCHEMA_LEVELS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MDSCHEMA_LEVELS rowset
ms.assetid: 4313e268-33f4-4e99-96d7-2ec26775c580
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8d9a56387365489615b6b7665dedb3edc7f367f6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="mdschemalevels-rowset"></a>Набор строк MDSCHEMA_LEVELS
  Описывает каждый уровень в конкретной иерархии.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **MDSCHEMA_LEVELS** набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Имя каталога, которому принадлежит этот уровень. Имеет значение**NULL** , если поставщик не поддерживает каталоги.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Имя схемы, которой принадлежит этот уровень. **Значение NULL** Если поставщик не поддерживает схемы.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Имя куба, которому принадлежит этот уровень.|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|Уникальное имя измерения, которому принадлежит этот уровень. Для поставщиков, формирующих уникальные имена путем использования квалификаторов, компоненты имени разделяются между собой.|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|Уникальное имя иерархии. Если уровень принадлежит к нескольким иерархиям, то каждой из этих иерархий будет соответствовать одна строка. Для поставщиков, формирующих уникальные имена путем использования квалификаторов, компоненты имени разделяются между собой.|  
|**LEVEL_NAME**|**DBTYPE_WSTR**|Имя уровня.|  
|**LEVEL_UNIQUE_NAME**|**DBTYPE_WSTR**|Правильно экранированное уникальное имя уровня.|  
|**LEVEL_GUID**|**DBTYPE_GUID**|Не поддерживается.|  
|**LEVEL_CAPTION**|**DBTYPE_WSTR**|Метка или заголовок, связанный с иерархией. В основном используется в целях отображения. Если заголовок не существует, **LEVEL_NAME** возвращается.|  
|**LEVEL_NUMBER**|**DBTYPE_UI4**|Расстояние от корня иерархии до данного уровня. Корневой уровень является нулевым (**0)**.|  
|**LEVEL_CARDINALITY**|**DBTYPE_UI4**|Число элементов уровня.|  
|**LEVEL_TYPE**|**DBTYPE_I4**|Тип уровня.<br /><br /> **MDLEVEL_TYPE_GEO_CONTINENT** (**0x2001**)<br /><br /> **MDLEVEL_TYPE_GEO_REGION** (**0x2002**)<br /><br /> **MDLEVEL_TYPE_GEO_COUNTRY** (**0x2003**)<br /><br /> **MDLEVEL_TYPE_GEO_STATE_OR_PROVINCE** (**0x2004**)<br /><br /> **MDLEVEL_TYPE_GEO_COUNTY** (**0x2005**)<br /><br /> **MDLEVEL_TYPE_GEO_CITY** (**0x2006**)<br /><br /> **MDLEVEL_TYPE_GEO_POSTALCODE** (**0x2007**)<br /><br /> **MDLEVEL_TYPE_GEO_POINT** (**0x2008**)<br /><br /> **MDLEVEL_TYPE_ORG_UNIT** (**0x1011**)<br /><br /> **MDLEVEL_TYPE_BOM_RESOURCE** (**0x1012**)<br /><br /> **MDLEVEL_TYPE_QUANTITATIVE** (**0x1013**)<br /><br /> **MDLEVEL_TYPE_ACCOUNT** (**0x1014**)<br /><br /> **MDLEVEL_TYPE_CUSTOMER** (**0x1021**)<br /><br /> **MDLEVEL_TYPE_CUSTOMER_GROUP** (**0x1022**)<br /><br /> **MDLEVEL_TYPE_CUSTOMER_HOUSEHOLD** (**0x1023**)<br /><br /> **MDLEVEL_TYPE_PRODUCT** (**0x1031**)<br /><br /> **MDLEVEL_TYPE_PRODUCT_GROUP** (**0x1032**)<br /><br /> **MDLEVEL_TYPE_SCENARIO** (**0x1015**)<br /><br /> **MDLEVEL_TYPE_UTILITY** (**0x1016**)<br /><br /> **MDLEVEL_TYPE_PERSON** (**0x1041**)<br /><br /> **MDLEVEL_TYPE_COMPANY** (**0x1042**)<br /><br /> **MDLEVEL_TYPE_CURRENCY_SOURCE** (**0x1051**)<br /><br /> **MDLEVEL_TYPE_CURRENCY_DESTINATION** (**0x1052**)<br /><br /> **MDLEVEL_TYPE_CHANNEL** (**0x1061**)<br /><br /> **MDLEVEL_TYPE_REPRESENTATIVE** (**0x1062**)<br /><br /> **MDLEVEL_TYPE_PROMOTION** (**0x1071**)|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Понятное описание уровня. Имеет значение NULL, если описание отсутствует.|  
|**CUSTOM_ROLLUP_SETTINGS**|**DBTYPE_I4**|Битовая карта, в которой показаны параметры пользовательской свертки:<br /><br /> **MDLEVELS_CUSTOM_ROLLUP_EXPRESSION** (**0x01**) указывает, что выражение существует для данного уровня. (Устаревшее)<br /><br /> **MDLEVELS_CUSTOM_ROLLUP_COLUMN** (**0x02**) указывает, что столбец пользовательской свертки для данного уровня.<br /><br /> **MDLEVELS_SKIPPED_LEVELS** (**0x04**) указывает, что пропущенные уровень, связанных с элементами этого уровня.<br /><br /> **MDLEVELS_CUSTOM_MEMBER_PROPERTIES** (**0x08**) означает, что элементы уровня имеют пользовательские свойства элемента.<br /><br /> **MDLEVELS_UNARY_OPERATOR** (**0x10**) означает, что элементы на данном уровне имеют унарные операторы.|  
|**LEVEL_UNIQUE_SETTINGS**|**DBTYPE_I4**|Битовая карта, в которой показано, какие столбцы содержат уникальные значения, если на уровне есть только элементы с уникальными именами или ключами. В файле Msmd.h определены следующие битовые константы для этой битовой карты.<br /><br /> **MDDIMENSIONS_MEMBER_KEY_UNIQUE** (**1**)<br /><br /> **MDDIMENSIONS_MEMBER_NAME_UNIQUE** (**2**)<br /><br /> <br /><br /> Обратите внимание, что ключ всегда уникален в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Имя будет уникальным, если значение атрибута — **UniqueInDimension** или **UniqueInAttribute**|  
|**LEVEL_IS_VISIBLE**|**DBTYPE_BOOL**|Логическое значение, показывающее, является ли уровень видимым.<br /><br /> Всегда возвращает True. Если уровень невидим, то не включается в набор строк схемы.|  
|**LEVEL_ORDERING_PROPERTY**|**DBTYPE_WSTR**|Идентификатор атрибута, по которому отсортирован уровень.|  
|**LEVEL_DBTYPE**|**DBTYPE_I4**|**DBTYPE** перечисление ключевой столбец, используемый в качестве атрибута уровня элемента.<br /><br /> Принимает значение NULL, если объединенные элементы используются в качестве ключевого столбца элемента.|  
|**LEVEL_MASTER_UNIQUE_NAME**|**DBTYPE_WSTR**|Всегда возвращает значение NULL.|  
|**LEVEL_NAME_SQL_COLUMN_NAME**|**DBTYPE_WSTR**|SQL-представление имен элемента уровня.|  
|**LEVEL_KEY_SQL_COLUMN_NAME**|**DBTYPE_WSTR**|SQL-представление ключевых значений элемента уровня.|  
|**LEVEL_UNIQUE_NAME_SQL_COLUMN_NAME**|**DBTYPE_WSTR**|SQL-представление уникальных имен элемента уровня.|  
|**LEVEL_ATTRIBUTE_HIERARCHY_NAME**|**DBTYPE_WSTR**|Имя иерархии атрибута, предоставляющей источник для уровня.|  
|**LEVEL_KEY_CARDINALITY**|**DBTYPE_UI2**|Число столбцов в ключе уровня.|  
|**LEVEL_ORIGIN**|**DBTYPE_UI2**|Битовая карта, в которой показано, каким образом был получен уровень.<br /><br /> **MD_ORIGIN_USER_DEFINED** обозначает уровни в пользовательской иерархии.<br /><br /> **MD_ORIGIN_ATTRIBUTE** обозначает уровни в иерархии атрибутов.<br /><br /> **MD_ORIGIN_KEY_ATTRIBUTE** обозначает уровни в иерархии ключевых атрибутов.<br /><br /> **MD_ORIGIN_INTERNAL** обозначает уровни в иерархии атрибутов, которые не были включены.|  
  
 Набор строк отсортирован по **CATALOG_NAME**, **имя_схемы**, **CUBE_NAME**, **DIMENSION_UNIQUE_NAME**, **HIERARCHY_ UNIQUE_NAME**, **LEVEL_NUMBER**.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 **MDSCHEMA_LEVELS** строк может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**LEVEL_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**LEVEL_UNIQUE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**LEVEL_ORIGIN**|**DBTYPE_UI2**|(Необязательно) Ограничение по умолчанию действует на **MD_USER_DEFINED** и **MD_SYSTEM_ENABLED**|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(Необязательно) Ограничение по умолчанию имеет значение 1. Битовая карта с одним из следующих допустимых значений:<br /><br /> 1 CUBE<br /><br /> 2 DIMENSION|  
|**LEVEL_VISIBILITY**|**DBTYPE_UI2**|(Необязательно) Ограничение по умолчанию имеет значение 1. Битовая карта с одним из следующих значений:<br /><br /> 1 Отображается<br /><br /> 2 Не отображается|  
  
## <a name="see-also"></a>См. также:  
 [OLE DB для OLAP наборы строк схемы](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
