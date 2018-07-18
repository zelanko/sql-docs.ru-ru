---
title: Набор строк MDSCHEMA_LEVELS | Документация Майкрософт
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
- MDSCHEMA_LEVELS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_LEVELS rowset
ms.assetid: 4313e268-33f4-4e99-96d7-2ec26775c580
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ff9d359bb82c0197c4ebdc1b9c088ca50556b9d9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312444"
---
# <a name="mdschemalevels-rowset"></a>Набор строк MDSCHEMA_LEVELS
  Описывает каждый уровень в конкретной иерархии.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `MDSCHEMA_LEVELS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Имя каталога, которому принадлежит этот уровень. Имеет значение `NULL`, если поставщик не поддерживает каталоги.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Имя схемы, которой принадлежит этот уровень. Имеет значение `NULL`, если поставщик не поддерживает схемы.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Имя куба, которому принадлежит этот уровень.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Уникальное имя измерения, которому принадлежит этот уровень. Для поставщиков, формирующих уникальные имена путем использования квалификаторов, компоненты имени разделяются между собой.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`||Уникальное имя иерархии. Если уровень принадлежит к нескольким иерархиям, то каждой из этих иерархий будет соответствовать одна строка. Для поставщиков, формирующих уникальные имена путем использования квалификаторов, компоненты имени разделяются между собой.|  
|`LEVEL_NAME`|`DBTYPE_WSTR`||Имя уровня.|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`||Правильно экранированное уникальное имя уровня.|  
|`LEVEL_GUID`|`DBTYPE_GUID`||Не поддерживается.|  
|`LEVEL_CAPTION`|`DBTYPE_WSTR`||Метка или заголовок, связанный с иерархией. В основном используется в целях отображения. Если заголовок не существует, возвращается `LEVEL_NAME`.|  
|`LEVEL_NUMBER`|`DBTYPE_UI4`||Расстояние от корня иерархии до данного уровня. Корневой уровень является нулевым (`0)`.|  
|`LEVEL_CARDINALITY`|`DBTYPE_UI4`||Число элементов уровня.|  
|`LEVEL_TYPE`|`DBTYPE_I4`||Тип уровня.<br /><br /> -   `MDLEVEL_TYPE_GEO_CONTINENT` (`0x2001`)<br />-   `MDLEVEL_TYPE_GEO_REGION` (`0x2002`)<br />-   `MDLEVEL_TYPE_GEO_COUNTRY` (`0x2003`)<br />-   `MDLEVEL_TYPE_GEO_STATE_OR_PROVINCE` (`0x2004`)<br />-   `MDLEVEL_TYPE_GEO_COUNTY` (`0x2005`)<br />-   `MDLEVEL_TYPE_GEO_CITY` (`0x2006`)<br />-   `MDLEVEL_TYPE_GEO_POSTALCODE` (`0x2007`)<br />-   `MDLEVEL_TYPE_GEO_POINT` (`0x2008`)<br />-   `MDLEVEL_TYPE_ORG_UNIT` (`0x1011`)<br />-   `MDLEVEL_TYPE_BOM_RESOURCE` (`0x1012`)<br />-   **MDLEVEL_TYPE_QUANTITATIVE** (`0x1013`)<br />-   `MDLEVEL_TYPE_ACCOUNT` (`0x1014`)<br />-   `MDLEVEL_TYPE_CUSTOMER` (`0x1021`)<br />-   `MDLEVEL_TYPE_CUSTOMER_GROUP` (`0x1022`)<br />-   `MDLEVEL_TYPE_CUSTOMER_HOUSEHOLD` (`0x1023`)<br />-   `MDLEVEL_TYPE_PRODUCT` (`0x1031`)<br />-   `MDLEVEL_TYPE_PRODUCT_GROUP` (`0x1032`)<br />-   `MDLEVEL_TYPE_SCENARIO` (`0x1015`)<br />-   `MDLEVEL_TYPE_UTILITY` (`0x1016`)<br />-   `MDLEVEL_TYPE_PERSON` (`0x1041`)<br />-   `MDLEVEL_TYPE_COMPANY` (`0x1042`)<br />-   `MDLEVEL_TYPE_CURRENCY_SOURCE` (`0x1051`)<br />-   `MDLEVEL_TYPE_CURRENCY_DESTINATION` (`0x1052`)<br />-   `MDLEVEL_TYPE_CHANNEL` (`0x1061`)<br />-   `MDLEVEL_TYPE_REPRESENTATIVE` (`0x1062`)<br />-   `MDLEVEL_TYPE_PROMOTION` (`0x1071`)|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Понятное описание уровня. Имеет значение NULL, если описание отсутствует.|  
|`CUSTOM_ROLLUP_SETTINGS`|`DBTYPE_I4`||Битовая карта, в которой показаны параметры пользовательской свертки:<br /><br /> -   `MDLEVELS_CUSTOM_ROLLUP_EXPRESSION` (`0x01`) указывает выражение существует на данном уровне. (Устаревшее)<br />-   `MDLEVELS_CUSTOM_ROLLUP_COLUMN` (`0x02`) указывает, что столбец пользовательской свертки для данного уровня.<br />-   `MDLEVELS_SKIPPED_LEVELS` (`0x04`) указывает, что пропущенные уровень, связанный с элементы этого уровня.<br />-   `MDLEVELS_CUSTOM_MEMBER_PROPERTIES` (`0x08`) указывает, что элементы уровня имеют пользовательские свойства элементов.<br />-   `MDLEVELS_UNARY_OPERATOR` (`0x10`) показывает, что элементы на уровне имеют унарные операторы.|  
|`LEVEL_UNIQUE_SETTINGS`|`DBTYPE_I4`||Битовая карта, в которой показано, какие столбцы содержат уникальные значения, если на уровне есть только элементы с уникальными именами или ключами. В файле Msmd.h определены следующие битовые константы для этой битовой карты.<br /><br /> -   `MDDIMENSIONS_MEMBER_KEY_UNIQUE` (`1`)<br />-   `MDDIMENSIONS_MEMBER_NAME_UNIQUE` (`2`)<br /><br /> Ключ всегда уникален в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Имя будет уникальным, если атрибуту присвоено значение `UniqueInDimension` или `UniqueInAttribute`|  
|`LEVEL_IS_VISIBLE`|`DBTYPE_BOOL`||Логическое значение, показывающее, является ли уровень видимым.<br /><br /> Всегда возвращает True. Если уровень невидим, то не включается в набор строк схемы.|  
|`LEVEL_ORDERING_PROPERTY`|`DBTYPE_WSTR`||Идентификатор атрибута, по которому отсортирован уровень.|  
|`LEVEL_DBTYPE`|`DBTYPE_I4`||Перечисление `DBTYPE` ключевого столбца элемента, которое используется в качестве атрибута уровня.<br /><br /> Принимает значение NULL, если объединенные элементы используются в качестве ключевого столбца элемента.|  
|`LEVEL_MASTER_UNIQUE_NAME`|`DBTYPE_WSTR`||Всегда возвращает значение NULL.|  
|`LEVEL_NAME_SQL_COLUMN_NAME`|`DBTYPE_WSTR`||SQL-представление имен элемента уровня.|  
|`LEVEL_KEY_SQL_COLUMN_NAME`|`DBTYPE_WSTR`||SQL-представление ключевых значений элемента уровня.|  
|`LEVEL_UNIQUE_NAME_SQL_COLUMN_NAME`|`DBTYPE_WSTR`||SQL-представление уникальных имен элемента уровня.|  
|`LEVEL_ATTRIBUTE_HIERARCHY_NAME`|`DBTYPE_WSTR`||Имя иерархии атрибута, предоставляющей источник для уровня.|  
|`LEVEL_KEY_CARDINALITY`|`DBTYPE_UI2`||Число столбцов в ключе уровня.|  
|`LEVEL_ORIGIN`|`DBTYPE_UI2`||Битовая карта, в которой показано, каким образом был получен уровень.<br /><br /> -   `MD_ORIGIN_USER_DEFINED` обозначает уровни в пользовательской иерархии.<br />-   `MD_ORIGIN_ATTRIBUTE` обозначает уровни в иерархии атрибутов.<br />-   `MD_ORIGIN_KEY_ATTRIBUTE` обозначает уровни в иерархии ключевых атрибутов.<br />-   `MD_ORIGIN_INTERNAL` обозначает уровни в иерархиях атрибутов, которые не включены.|  
  
 Набор строк отсортирован по `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `DIMENSION_UNIQUE_NAME`, `HIERARCHY_UNIQUE_NAME`, `LEVEL_NUMBER`.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `MDSCHEMA_LEVELS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`LEVEL_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`LEVEL_ORIGIN`|`DBTYPE_UI2`|Ограничение по умолчанию действует на `MD_USER_DEFINED` и `MD_SYSTEM_ENABLED` (необязательно)|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|Битовая карта с одним из следующих допустимых значений (необязательно).<br /><br /> -КУБ 1<br />— ИЗМЕРЕНИЯ 2<br /><br /> Значение по умолчанию для ограничения — 1.|  
|`LEVEL_VISIBILITY`|`DBTYPE_UI2`|Битовая карта с одним из следующих значений (необязательно):<br /><br /> -1 Visible<br />-2 не отображается<br /><br /> Значение по умолчанию для ограничения — 1.|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы OLE DB для OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
