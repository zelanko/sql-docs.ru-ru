---
title: SchemaEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SchemaEnum
helpviewer_keywords:
- SchemaEnum enumeration [ADO]
ms.assetid: 21c97651-297f-469f-b5b5-c48af72b62a8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c064120e3c658cafd88a96953ff00e18fbaa9b88
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931110"
---
# <a name="schemaenum"></a>SchemaEnum
Указывает тип схемы **записей** , [OpenSchema](../../../ado/reference/ado-api/openschema-method.md) методом.  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о функции и столбцы, возвращаемые для каждой константы ADO см. в разделах [приложении б: Наборы строк схемы](https://msdn.microsoft.com/2b5fbf03-e50d-44ee-bc57-5a57666c55f1) справочника программиста OLE DB. Имя каждого раздела указывается в скобках в разделе "Описание" в следующей таблице.  
  
 Дополнительные сведения о функции и столбцы, возвращаемые для каждой константы ADO MD можно найти в разделах [OLE DB для OLAP-объекты и наборы строк схемы](https://msdn.microsoft.com/d20bb2a6-68bd-423f-9ec8-eb930cd0c144) в OLE DB для документации оперативной аналитической обработки (OLAP). Имя каждого раздела указывается в скобках в столбце "Описание" в следующей таблице.  
  
 Может преобразовывать типы данных столбцов в документации по OLE DB для типов данных ADO, ссылаясь на столбец из ADO [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) раздела. Например, тип данных OLE DB из **DBTYPE_WSTR** эквивалентно типу данных ADO из **adWChar**.  
  
 ADO выдает результаты наподобие схемы для констант, **adSchemaDBInfoKeywords** и **adSchemaDBInfoLiterals**. Создает ADO **записей**и затем заполняет каждую строку значения, возвращаемые соответственно **IDBInfo::GetKeywords** и **IDBInfo::GetLiteralInfo** методы. Дополнительные сведения об этих методах можно найти в [IDBInfo](https://msdn.microsoft.com/3f5ad97f-3fc6-4f21-b691-f6911e4007f3) разделе руководства по программированию OLE DB.  
  
|Константа|Значение|Описание|Столбцы с ограничением|  
|--------------|-----------|-----------------|------------------------|  
|**adSchemaAsserts**|0|Возвращает утверждения, определенные в каталоге и принадлежащие данному пользователю.<br /><br /> (Набор строк УТВЕРЖДЕНИЯ)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME|  
|**adSchemaCatalogs**|1|Возвращает физические атрибуты, связанные с каталогами, доступными из СУБД.<br /><br /> (Набор строк КАТАЛОГИ)|CATALOG_NAME|  
|**adSchemaCharacterSets**|2|Возвращает наборы символов, определенные в каталоге и доступные указанному пользователю.<br /><br /> (Набор строк CHARACTER_SETS)|CHARACTER_SET_CATALOG CHARACTER_SET_SCHEMA CHARACTER_SET_NAME|  
|**adSchemaCheckConstraints**|5|Возвращает ограничения проверки, определенные в каталоге и принадлежащие данному пользователю.<br /><br /> (CHECK_CONSTRAINTS) Набор строк)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME|  
|**adSchemaCollations**|3|Возвращает сравнения знаков, определенные в каталоге и доступные указанному пользователю.<br /><br /> (Набор строк с параметрами СОРТИРОВКИ)|COLLATION_CATALOG COLLATION_SCHEMA COLLATION_NAME|  
|**adSchemaColumnPrivileges**|13|Возвращает привилегии для столбцов таблиц, определенные в каталоге, которые доступны или предоставленные указанному пользователю.<br /><br /> (Набор строк COLUMN_PRIVILEGES)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME GRANTOR GRANTEE|  
|**adSchemaColumns**|4|Возвращает столбцы таблиц (включая представления) определены в каталоге, которые доступны для данного пользователя.<br /><br /> (Набор строк COLUMNS)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME|  
|**adSchemaColumnsDomainUsage**|11|Возвращает столбцы, определенные в каталоге и зависящие от домена определены в каталоге и принадлежат данному пользователю.<br /><br /> (Набор строк COLUMN_DOMAIN_USAGE)|COLUMN_NAME ИМЯ_ДОМЕНА DOMAIN_SCHEMA DOMAIN_CATALOG|  
|**adSchemaConstraintColumnUsage**|6|Возвращает столбцы, используемые ссылочные ограничения, ограничения unique, ограничения check и утверждения, определенные в каталоге и принадлежащие данному пользователю.<br /><br /> (Набор строк CONSTRAINT_COLUMN_USAGE)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME|  
|**adSchemaConstraintTableUsage**|7|Возвращает таблицы, которые используются ссылочные ограничения, ограничения unique, ограничения check и утверждения, которые определены в каталоге и принадлежат данному пользователю.<br /><br /> (Набор строк CONSTRAINT_TABLE_USAGE)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|**adSchemaCubes**|32|Возвращает сведения о доступных кубов в схеме (или каталога, если поставщик не поддерживает схемы).<br /><br /> (КУБЫ строк *)|CATALOG_NAME SCHEMA_NAME CUBE_NAME|  
|**adSchemaDBInfoKeywords**|30|Возвращает список ключевых слов конкретного поставщика.<br /><br /> (IDBInfo::GetKeywords)|\<None >|  
|**adSchemaDBInfoLiterals**|31|Возвращает список литералов конкретного поставщика, используемых в текстовых командах.<br /><br /> (IDBInfo::GetLiteralInfo)|\<None >|  
|**adSchemaDimensions**|33|Возвращает сведения об измерениях в данном кубе. Он содержит одну строку для каждого измерения.<br /><br /> (Набор строк ИЗМЕРЕНИЙ)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_NAME DIMENSION_UNIQUE_NAME|  
|**adSchemaForeignKeys**|27|Возвращает столбцы внешнего ключа, определенные в каталоге данным пользователем.<br /><br /> (Набор строк FOREIGN_KEYS)|PK_TABLE_CATALOG PK_TABLE_SCHEMA PK_TABLE_NAME FK_TABLE_CATALOG FK_TABLE_SCHEMA FK_TABLE_NAME|  
|**adSchemaHierarchies**|34|Возвращает сведения об иерархиях, доступных в измерении.<br /><br /> (Набор строк ИЕРАРХИЙ)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_NAME HIERARCHY_UNIQUE_NAME|  
|**adSchemaIndexes**|12|Возвращает индексы, определенные в каталоге и принадлежащие данному пользователю.<br /><br /> (Набор строк ИНДЕКСЫ)|TABLE_CATALOG TABLE_SCHEMA INDEX_NAME TYPE TABLE_NAME|  
|**adSchemaKeyColumnUsage**|8|Возвращает столбцы, определенные в каталоге, которые являются ограниченными как ключи данным пользователем.<br /><br /> (Набор строк KEY_COLUMN_USAGE)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME|  
|**adSchemaLevels**|35|Возвращает сведения об уровнях, доступных в измерении.<br /><br /> (Набор строк УРОВНЕЙ)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME LEVEL_NAME LEVEL_UNIQUE_NAME|  
|**adSchemaMeasures**|36|Возвращает сведения о доступных мер.<br /><br /> (Набор строк меры)|CATALOG_NAME SCHEMA_NAME CUBE_NAME MEASURE_NAME MEASURE_UNIQUE_NAME|  
|**adSchemaMembers**|38|Возвращает сведения о доступных элементов.<br /><br /> (ЭЛЕМЕНТЫ в набор строк)|Оператор CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME LEVEL_UNIQUE_NAME MEMBER_NAME LEVEL_NUMBER MEMBER_UNIQUE_NAME MEMBER_CAPTION дерева MEMBER_TYPE. Дополнительные сведения см. в разделе OLE DB для оперативной аналитической обработки (OLAP).|  
|**adSchemaPrimaryKeys**|28|Возвращает первичные ключевые столбцы, определенные в каталоге данным пользователем.<br /><br /> (Набор строк PRIMARY_KEYS)|PK_TABLE_CATALOG PK_TABLE_SCHEMA PK_TABLE_NAME|  
|**adSchemaProcedureColumns**|29|Возвращает информацию о столбцах наборов строк, возвращаемых процедурами.<br /><br /> (Набор строк PROCEDURE_COLUMNS)|PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME COLUMN_NAME|  
|**adSchemaProcedureParameters**|26|Возвращает информацию о параметрах и кодах возврата процедур.<br /><br /> (Набор строк PROCEDURE_PARAMETERS)|PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME PARAMETER_NAME|  
|**adSchemaProcedures**|16|Возвращает процедуры, определенные в каталоге и принадлежащие данному пользователю.<br /><br /> (Набор строк ПРОЦЕДУР)|PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME PROCEDURE_TYPE|  
|**adSchemaProperties**|37|Возвращает сведения о доступных свойствах для каждого уровня измерения.<br /><br /> (Свойства набора строк)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME LEVEL_UNIQUE_NAME MEMBER_UNIQUE_NAME PROPERTY_TYPE PROPERTY_NAME|  
|**adSchemaProviderSpecific**|-1|Используется, если поставщик определяет свой собственный запросов нестандартные схемы.|\<Зависит от поставщика >|  
|**adSchemaProviderTypes**|22|Возвращает типы (базовый) данных, поддерживаемые поставщиком данных.<br /><br /> (Набор строк PROVIDER_TYPES)|DATA_TYPE BEST_MATCH|  
|**AdSchemaReferentialConstraints**|9|Возвращает ссылочные ограничения, определенные в каталоге, принадлежащие данному пользователю.<br /><br /> (Набор строк REFERENTIAL_CONSTRAINTS)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME|  
|**adSchemaSchemata**|17|Возвращает схемы (объекты базы данных), принадлежащие данному пользователю.<br /><br /> (Набор строк СХЕМЫ)|CATALOG_NAME SCHEMA_NAME SCHEMA_OWNER|  
|**adSchemaSQLLanguages**|18|Возвращает уровни соответствия, параметры и диалекты, поддерживаемые данными обработки реализации SQL, определенные в каталоге.<br /><br /> (Набор строк SQL_LANGUAGES)|\<None >|  
|**adSchemaStatistics**|19|Возвращает статистические данные, определенные в каталоге, принадлежащие данному пользователю.<br /><br /> (Набор строк СТАТИСТИКА)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|**adSchemaTableConstraints**|10|Возвращает ограничения таблицы, определенные в каталоге и принадлежащие данному пользователю.<br /><br /> (Набор строк TABLE_CONSTRAINTS)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME TABLE_CATALOG TABLE_SCHEMA TABLE_NAME CONSTRAINT_TYPE|  
|**adSchemaTablePrivileges**|14|Возвращает привилегии для таблиц, определенные в каталоге, которые доступны или предоставленные указанному пользователю.<br /><br /> (Набор строк TABLE_PRIVILEGES)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME GRANTOR GRANTEE|  
|**adSchemaTables**|20|Возвращает таблицы (включая представления) определены в каталоге, которые доступны для данного пользователя.<br /><br /> (Набор строк таблицы)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME TABLE_TYPE|  
|**adSchemaTranslations**|21|Возвращает преобразования знаков, определенные в каталоге и доступные указанному пользователю.<br /><br /> (Переводы строк)|TRANSLATION_CATALOG TRANSLATION_SCHEMA TRANSLATION_NAME|  
|**adSchemaTrustees**|39|Зарезервировано для будущего использования.||  
|**adSchemaUsagePrivileges**|15|Возвращает привилегии USAGE для объектов, определенные в каталоге, которые доступны или предоставленные указанному пользователю.<br /><br /> (Набор строк USAGE_PRIVILEGES)|OBJECT_CATALOG OBJECT_SCHEMA OBJECT_NAME OBJECT_TYPE GRANTOR УЧАСТНИКА|  
|**adSchemaViewColumnUsage**|24|Возвращает столбцы, по которым просматриваемые таблицы, определенные в каталоге и принадлежащие данному пользователю, зависят.<br /><br /> (Набор строк VIEW_COLUMN_USAGE)|VIEW_CATALOG VIEW_SCHEMA VIEW_NAME|  
|**adSchemaViews**|23|Возвращает представления, определенные в каталоге и доступные указанному пользователю.<br /><br /> (Набор строк ПРЕДСТАВЛЕНИЯ)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|**adSchemaViewTableUsage**|25|Возвращает просматриваемые таблицы, определенные в каталоге и принадлежащие данному пользователю, таблиц, в котором зависят.<br /><br /> (Набор строк VIEW_TABLE_USAGE)|VIEW_CATALOG VIEW_SCHEMA VIEW_NAME|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
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
