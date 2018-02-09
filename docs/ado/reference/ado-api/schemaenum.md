---
title: "SchemaEnum | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- SchemaEnum
helpviewer_keywords:
- SchemaEnum enumeration [ADO]
ms.assetid: 21c97651-297f-469f-b5b5-c48af72b62a8
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dc84741e1963b2c484e82eea7bc3de08cf12da13
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="schemaenum"></a>SchemaEnum
Указывает тип схемы **записей** , [OpenSchema](../../../ado/reference/ado-api/openschema-method.md) извлекает метод.  
  
## <a name="remarks"></a>Remarks  
 Дополнительные сведения о функции и столбцы, возвращаемые для каждой константы ADO можно найти в разделах [приложение б. наборы строк схемы](http://msdn.microsoft.com/en-us/2b5fbf03-e50d-44ee-bc57-5a57666c55f1) ссылки программиста OLE DB. Имя каждого раздела указывается в скобках в разделе "Описание" в следующей таблице.  
  
 Дополнительные сведения о функции и столбцы, возвращаемые для каждой константы ADO MD можно найти в разделах [OLE DB для OLAP-объекты и наборы строк схемы](http://msdn.microsoft.com/en-us/d20bb2a6-68bd-423f-9ec8-eb930cd0c144) в OLE DB для документации оперативной аналитической обработки (OLAP). Имя каждого раздела указывается в скобках в столбце "Описание" в следующей таблице.  
  
 Можно легко преобразовать типы данных столбцов в документации по OLE DB с типами данных ADO, обратившись к столбцу Описание ADO [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) раздела. Например, тип данных OLE DB из **DBTYPE_WSTR** эквивалентен типу данных ADO **adWChar**.  
  
 ADO формирует результаты по принципу схемы для констант, **adSchemaDBInfoKeywords** и **adSchemaDBInfoLiterals**. Создает ADO **записей**, а затем заполняет каждую строку значения, возвращаемые соответственно **IDBInfo::GetKeywords** и **IDBInfo::GetLiteralInfo** методы. Дополнительные сведения об этих методах, которые можно найти в [IDBInfo](http://msdn.microsoft.com/en-us/3f5ad97f-3fc6-4f21-b691-f6911e4007f3) раздел справочника программиста OLE DB.  
  
|Константа|Значение|Описание|Столбцы с ограничением|  
|--------------|-----------|-----------------|------------------------|  
|**adSchemaAsserts**|0|Возвращает утверждения, определенные в каталоге и принадлежащие данному пользователю.<br /><br /> (УТВЕРЖДЕНИЯ строк)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME|  
|**adSchemaCatalogs**|1|Возвращает физические атрибуты, связанные с каталогами, доступными из СУБД.<br /><br /> (Набор строк КАТАЛОГИ)|CATALOG_NAME|  
|**adSchemaCharacterSets**|2|Возвращает наборы символов, определенные в каталоге, доступных данному пользователю.<br /><br /> (Набор строк CHARACTER_SETS)|CHARACTER_SET_CATALOG CHARACTER_SET_SCHEMA CHARACTER_SET_NAME|  
|**adSchemaCheckConstraints**|5|Возвращает ограничения check, определенные в каталоге и принадлежащие данному пользователю.<br /><br /> (CHECK_CONSTRAINTS) Набор строк)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME|  
|**adSchemaCollations**|3|Возвращает параметров сортировки символов, определенные в каталоге, доступных данному пользователю.<br /><br /> (Параметры СОРТИРОВКИ набора строк)|COLLATION_CATALOG COLLATION_SCHEMA COLLATION_NAME|  
|**adSchemaColumnPrivileges**|13|Возвращает привилегии для столбцов таблиц, определенные в каталоге, которые доступны или предоставленные указанному пользователю.<br /><br /> (Набор строк COLUMN_PRIVILEGES)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME GRANTOR GRANTEE|  
|**adSchemaColumns**|4|Возвращает столбцы таблиц (включая представления) определены в каталоге, доступных данному пользователю.<br /><br /> (СТОЛБЦЫ набора строк)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME|  
|**adSchemaColumnsDomainUsage**|11|Возвращает столбцы, определенные в каталоге, зависимые от домена определены в каталоге и принадлежащие данному пользователю.<br /><br /> (COLUMN_DOMAIN_USAGE Rowset)|COLUMN_NAME ИМЯ_ДОМЕНА DOMAIN_SCHEMA DOMAIN_CATALOG|  
|**adSchemaConstraintColumnUsage**|6|Возвращает столбцы, используемые ссылочные ограничения, ограничения unique, ограничения check и утверждения, определенные в каталоге и принадлежащие данному пользователю.<br /><br /> (Набор строк CONSTRAINT_COLUMN_USAGE)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME|  
|**adSchemaConstraintTableUsage**|7|Возвращает таблицы, используемые ссылочные ограничения, ограничения unique, ограничения check и утверждения, которые определены в каталоге и принадлежащие данному пользователю.<br /><br /> (Набор строк CONSTRAINT_TABLE_USAGE)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|**adSchemaCubes**|32|Возвращает сведения о доступных кубов в схеме (или каталога, если поставщик не поддерживает схемы).<br /><br /> (КУБЫ строк *)|ИМЯ_КАТАЛОГА SCHEMA_NAME CUBE_NAME|  
|**adSchemaDBInfoKeywords**|30|Возвращает список ключевых слов для определенного поставщика.<br /><br /> (IDBInfo::GetKeywords)|\<None >|  
|**adSchemaDBInfoLiterals**|31|Возвращает список литералов конкретного поставщика, используемых в текстовых командах.<br /><br /> (IDBInfo::GetLiteralInfo)|\<None >|  
|**adSchemaDimensions**|33|Возвращает сведения об измерениях в данном кубе. Он содержит одну строку для каждого измерения.<br /><br /> (Набор строк ИЗМЕРЕНИЙ)|ИМЯ_КАТАЛОГА SCHEMA_NAME CUBE_NAME DIMENSION_NAME DIMENSION_UNIQUE_NAME|  
|**adSchemaForeignKeys**|27|Возвращает внешние ключевые столбцы, определенные в каталоге данным пользователем.<br /><br /> (Набор строк FOREIGN_KEYS)|PK_TABLE_CATALOG PK_TABLE_SCHEMA PK_TABLE_NAME FK_TABLE_CATALOG FK_TABLE_SCHEMA FK_TABLE_NAME|  
|**adSchemaHierarchies**|34|Возвращает сведения об иерархиях, доступных в измерении.<br /><br /> (ИЕРАРХИИ строк)|ИМЯ_КАТАЛОГА SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_NAME HIERARCHY_UNIQUE_NAME|  
|**adSchemaIndexes**|12|Возвращает индексы, определенные в каталоге и принадлежащие данному пользователю.<br /><br /> (ИНДЕКСЫ строк)|INDEX_NAME ТИП ЗНАЧЕНИЯМ TABLE_CATALOG TABLE_SCHEMA ИМЯ_ТАБЛИЦЫ|  
|**adSchemaKeyColumnUsage**|8|Возвращает столбцы, определенные в каталоге, ограниченные как ключи данным пользователем.<br /><br /> (KEY_COLUMN_USAGE Rowset)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME ЗНАЧЕНИЯМ TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME|  
|**adSchemaLevels**|35|Возвращает сведения об уровнях, доступных в измерении.<br /><br /> (Набор строк УРОВНЕЙ)|ИМЯ_КАТАЛОГА SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME LEVEL_NAME LEVEL_UNIQUE_NAME|  
|**adSchemaMeasures**|36|Возвращает сведения о доступных мер.<br /><br /> (Набор строк МЕР)|ИМЯ_КАТАЛОГА SCHEMA_NAME CUBE_NAME MEASURE_NAME MEASURE_UNIQUE_NAME|  
|**adSchemaMembers**|38|Возвращает сведения о доступных элементов.<br /><br /> (ЧЛЕНЫ строк)|Оператор имя_каталога SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME LEVEL_UNIQUE_NAME MEMBER_NAME LEVEL_NUMBER MEMBER_UNIQUE_NAME MEMBER_CAPTION дерева MEMBER_TYPE. Дополнительные сведения см. в разделе OLE DB для оперативной аналитической обработки (OLAP).|  
|**adSchemaPrimaryKeys**|28|Возвращает первичные ключевые столбцы, определенные в каталоге данным пользователем.<br /><br /> (Набор строк PRIMARY_KEYS)|PK_TABLE_CATALOG PK_TABLE_SCHEMA PK_TABLE_NAME|  
|**adSchemaProcedureColumns**|29|Возвращает информацию о столбцах наборов строк, возвращаемых процедурами.<br /><br /> (Набор строк PROCEDURE_COLUMNS)|PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME COLUMN_NAME|  
|**adSchemaProcedureParameters**|26|Возвращает информацию о параметрах и кодах возврата процедур.<br /><br /> (Набор строк PROCEDURE_PARAMETERS)|PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME PARAMETER_NAME|  
|**adSchemaProcedures**|16|Возвращает процедуры, определенные в каталоге и принадлежащие данному пользователю.<br /><br /> (Набор строк для ПРОЦЕДУР)|PROCEDURE_CATALOG PROCEDURE_SCHEMA ИМЯ_ПРОЦЕДУРЫ PROCEDURE_TYPE|  
|**adSchemaProperties**|37|Возвращает сведения о доступных свойствах для каждого уровня измерения.<br /><br /> (Свойства набора строк)|ИМЯ_КАТАЛОГА SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME LEVEL_UNIQUE_NAME MEMBER_UNIQUE_NAME PROPERTY_TYPE PROPERTY_NAME|  
|**adSchemaProviderSpecific**|-1|Используется, если поставщик определяет нестандартное схемы запросов.|\<Зависит от поставщика >|  
|**adSchemaProviderTypes**|22|Возвращает данные (базовые) типы, поддерживаемые поставщиком данных.<br /><br /> (Набор строк PROVIDER_TYPES)|DATA_TYPE BEST_MATCH|  
|**AdSchemaReferentialConstraints**|9|Возвращает ссылочные ограничения, определенные в каталоге, принадлежащие данному пользователю.<br /><br /> (Набор строк REFERENTIAL_CONSTRAINTS)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME|  
|**adSchemaSchemata**|17|Возвращает схемы (объекты базы данных), принадлежащих указанному пользователю.<br /><br /> (Набор строк СХЕМЫ)|CATALOG_NAME SCHEMA_NAME SCHEMA_OWNER|  
|**adSchemaSQLLanguages**|18|Возвращает уровни соответствия, параметры и диалекты, поддерживаемые данными обработки реализации SQL, определенные в каталоге.<br /><br /> (SQL_LANGUAGES Rowset)|\<None >|  
|**adSchemaStatistics**|19|Возвращает статистические данные, определенные в каталоге, принадлежащие данному пользователю.<br /><br /> (Набор строк СТАТИСТИКА)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|**adSchemaTableConstraints**|10|Возвращает ограничения таблицы, определенные в каталоге и принадлежащие данному пользователю.<br /><br /> (Набор строк TABLE_CONSTRAINTS)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME TABLE_CATALOG TABLE_SCHEMA TABLE_NAME CONSTRAINT_TYPE|  
|**adSchemaTablePrivileges**|14|Возвращает привилегии для таблицы, определенные в каталоге, которые доступны или предоставленные указанному пользователю.<br /><br /> (Набор строк TABLE_PRIVILEGES)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME GRANTOR GRANTEE|  
|**adSchemaTables**|20|Возвращает таблицы (включая представления) определены в каталоге, доступных данному пользователю.<br /><br /> (Набор строк TABLES)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME TABLE_TYPE|  
|**adSchemaTranslations**|21|Возвращает преобразования символов, определенные в каталоге, доступных данному пользователю.<br /><br /> (Переводы строк)|TRANSLATION_CATALOG TRANSLATION_SCHEMA TRANSLATION_NAME|  
|**adSchemaTrustees**|39|Зарезервировано для последующего использования.||  
|**adSchemaUsagePrivileges**|15|Возвращает использование прав на объекты, определенные в каталоге, доступны или предоставленные указанному пользователю.<br /><br /> (Набор строк USAGE_PRIVILEGES)|OBJECT_CATALOG OBJECT_SCHEMA OBJECT_NAME OBJECT_TYPE GRANTOR УЧАСТНИКА|  
|**adSchemaViewColumnUsage**|24|Возвращает столбцы, по которым просматриваемые таблицы, определенные в каталоге и принадлежащие данному пользователю зависят.<br /><br /> (VIEW_COLUMN_USAGE Rowset)|VIEW_CATALOG VIEW_SCHEMA VIEW_NAME|  
|**adSchemaViews**|23|Возвращает представления, определенные в каталоге, доступных данному пользователю.<br /><br /> (Набор строк ПРЕДСТАВЛЕНИЯ)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|**adSchemaViewTableUsage**|25|Возвращает таблиц, в котором просматриваемые таблицы, определенные в каталоге и принадлежащие данному пользователю зависят.<br /><br /> (VIEW_TABLE_USAGE Rowset)|VIEW_CATALOG VIEW_SCHEMA VIEW_NAME|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.Schema.ASSERTS|  
|AdoEnums.Schema.CATALOGS|  
|AdoEnums.Schema.CHARACTERSETS|  
|AdoEnums.Schema.CHECKCONSTRAINTS|  
|AdoEnums.Schema.COLLATIONS|  
|AdoEnums.Schema.COLUMNPRIVILEGES|  
|AdoEnums.Schema.COLUMNS|  
|AdoEnums.Schema.COLUMNSDOMAINUSAGE|  
|AdoEnums.Schema.CONSTRAINTCOLUMNUSAGE|  
|AdoEnums.Schema.CONSTRAINTTABLEUSAGE|  
|AdoEnums.Schema.CUBES|  
|AdoEnums.Schema.DBINFOKEYWORDS|  
|AdoEnums.Schema.DBINFOLITERALS|  
|AdoEnums.Schema.DIMENSIONS|  
|AdoEnums.Schema.FOREIGNKEYS|  
|AdoEnums.Schema.HIERARCHIES|  
|AdoEnums.Schema.INDEXES|  
|AdoEnums.Schema.KEYCOLUMNUSAGE|  
|AdoEnums.Schema.LEVELS|  
|AdoEnums.Schema.MEASURES|  
|AdoEnums.Schema.MEMBERS|  
|AdoEnums.Schema.PRIMARYKEYS|  
|AdoEnums.Schema.PROCEDURECOLUMNS|  
|AdoEnums.Schema.PROCEDUREPARAMETERS|  
|AdoEnums.Schema.PROCEDURES|  
|AdoEnums.Schema.PROPERTIES|  
|AdoEnums.Schema.PROVIDERSPECIFIC|  
|AdoEnums.Schema.PROVIDERTYPES|  
|AdoEnums.Schema.REFERENTIALCONTRAINTS|  
|AdoEnums.Schema.SCHEMATA|  
|AdoEnums.Schema.SQLLANGUAGES|  
|AdoEnums.Schema.STATISTICS|  
|AdoEnums.Schema.TABLECONSTRAINTS|  
|AdoEnums.Schema.TABLEPRIVILEGES|  
|AdoEnums.Schema.TABLES|  
|AdoEnums.Schema.TRANSLATIONS|  
|AdoEnums.Schema.TRUSTEES|  
|AdoEnums.Schema.USAGEPRIVILEGES|  
|AdoEnums.Schema.VIEWCOLUMNUSAGE|  
|AdoEnums.Schema.VIEWS|  
|AdoEnums.Schema.VIEWTABLEUSAGE|  
  
## <a name="applies-to"></a>Объект применения  
 [Метод OpenSchema](../../../ado/reference/ado-api/openschema-method.md)
