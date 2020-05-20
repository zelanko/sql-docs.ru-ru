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
author: rothja
ms.author: jroth
ms.openlocfilehash: cb004c33ae413c93506bc1c90b331494b7e56adc
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765435"
---
# <a name="schemaenum"></a>SchemaEnum
Указывает тип **набора записей** схемы, извлекаемый методом [OpenSchema](../../../ado/reference/ado-api/openschema-method.md) .  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о функции и столбцах, возвращаемых для каждой константы ADO, можно найти в подразделах [приложения б: наборы строк схемы](https://msdn.microsoft.com/2b5fbf03-e50d-44ee-bc57-5a57666c55f1) справочника по OLE DB программисту. Имя каждого раздела указано в скобках в разделе Описание следующей таблицы.  
  
 Дополнительные сведения о функции и столбцах, возвращаемых для каждой объекты данных ActiveX (MD)ной константы, можно найти в разделах [OLE DB для объектов OLAP и наборов строк схемы](https://msdn.microsoft.com/d20bb2a6-68bd-423f-9ec8-eb930cd0c144) в OLE DB документации по аналитической обработке в Интернете (OLAP). Имя каждого раздела указано в скобках в столбце Описание следующей таблицы.  
  
 Типы данных столбцов в OLE DBной документации можно преобразовать в типы данных ADO, обратившись к столбцу Description в разделе ADO [дататипинум](../../../ado/reference/ado-api/datatypeenum.md) . Например, тип данных OLE DB **DBTYPE_WSTR** эквивалентен типу данных ADO **адвчар**.  
  
 ADO создает аналогичные схеме результаты для констант, **адсчемадбинфокэйвордс** и **адсчемадбинфолитералс**. ADO создает **набор записей**, а затем заполняет каждую строку значениями, возвращаемыми соответственно методам **IDBInfo::** IDBInfo и **:: жетлитералинфо** . Дополнительные сведения об этих методах можно найти в разделе [IDBInfo](https://msdn.microsoft.com/3f5ad97f-3fc6-4f21-b691-f6911e4007f3) справочника по программисту OLE DB.  
  
|Константа|Значение|Описание|Столбцы ограничений|  
|--------------|-----------|-----------------|------------------------|  
|**адсчемаассертс**|0|Возвращает утверждения, определенные в каталоге и принадлежащие данному пользователю.<br /><br /> (Набор строк УТВЕРЖДЕНий)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME|  
|**адсчемакаталогс**|1|Возвращает физические атрибуты, связанные с каталогами, доступными из СУБД.<br /><br /> (Набор строк каталога)|CATALOG_NAME|  
|**адсчемачарактерсетс**|2|Возвращает наборы символов, определенные в каталоге и доступные для данного пользователя.<br /><br /> (CHARACTER_SETS набор строк)|CHARACTER_SET_CATALOG CHARACTER_SET_SCHEMA CHARACTER_SET_NAME|  
|**адсчемачеккконстраинтс**|5|Возвращает проверочные ограничения, определенные в каталоге и принадлежащие данному пользователю.<br /><br /> (CHECK_CONSTRAINTS) Набора строк|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME|  
|**адсчемаколлатионс**|3|Возвращает параметры сортировки символов, определенные в каталоге и доступные для данного пользователя.<br /><br /> (Набор строк для параметров сортировки)|COLLATION_CATALOG COLLATION_SCHEMA COLLATION_NAME|  
|**адсчемаколумнпривилежес**|13|Возвращает привилегии для столбцов таблиц, определенных в каталоге, доступных для данного пользователя или предоставленных ему.<br /><br /> (COLUMN_PRIVILEGES набор строк)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME GRANTOR GRANTEE|  
|**адсчемаколумнс**|4|Возвращает столбцы таблиц (включая представления), определенные в каталоге и доступные для данного пользователя.<br /><br /> (Набор строк COLUMNs)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME|  
|**адсчемаколумнсдомаинусаже**|11|Возвращает столбцы, определенные в каталоге и зависящие от домена, определенного в каталоге и принадлежащего указанному пользователю.<br /><br /> (COLUMN_DOMAIN_USAGE набор строк)|DOMAIN_CATALOG DOMAIN_SCHEMA DOMAIN_NAME COLUMN_NAME|  
|**адсчемаконстраинтколумнусаже**|6|Возвращает столбцы, используемые ссылочными ограничениями, уникальными ограничениями, ограничениями проверки и утверждениями, определенными в каталоге и принадлежащими указанному пользователю.<br /><br /> (CONSTRAINT_COLUMN_USAGE набор строк)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME|  
|**адсчемаконстраинттаблеусаже**|7|Возвращает таблицы, используемые ссылочными ограничениями, уникальными ограничениями, ограничениями проверки и утверждениями, определенными в каталоге и принадлежащими указанному пользователю.<br /><br /> (CONSTRAINT_TABLE_USAGE набор строк)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|**адсчемакубес**|32|Возвращает сведения о доступных кубах в схеме (или каталоге, если поставщик не поддерживает схемы).<br /><br /> (Набор строк CUBEs *)|CATALOG_NAME SCHEMA_NAME CUBE_NAME|  
|**адсчемадбинфокэйвордс**|30|Возвращает список ключевых слов, специфичных для конкретного поставщика.<br /><br /> (IDBInfo:: "Ключевые слова")|\<Нет>|  
|**адсчемадбинфолитералс**|31|Возвращает список литералов, используемых в текстовых командах и специфичных для конкретного поставщика.<br /><br /> (IDBInfo:: Жетлитералинфо)|\<Нет>|  
|**адсчемадименсионс**|33|Возвращает сведения об измерениях в заданном кубе. Он содержит по одной строке для каждого измерения.<br /><br /> (Набор строк измерений)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_NAME DIMENSION_UNIQUE_NAME|  
|**адсчемафореигнкэйс**|27|Возвращает столбцы внешнего ключа, определенные в каталоге данным пользователем.<br /><br /> (FOREIGN_KEYS набор строк)|PK_TABLE_CATALOG PK_TABLE_SCHEMA PK_TABLE_NAME FK_TABLE_CATALOG FK_TABLE_SCHEMA FK_TABLE_NAME|  
|**adSchemaHierarchies**|34|Возвращает сведения о иерархиях, доступных в измерении.<br /><br /> (Наборы строк ИЕРАРХИй)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_NAME HIERARCHY_UNIQUE_NAME|  
|**адсчемаиндексес**|12|Возвращает индексы, определенные в каталоге и принадлежащие данному пользователю.<br /><br /> (Набор строк INDEXES)|TABLE_CATALOG ТИП INDEX_NAME TABLE_SCHEMA TABLE_NAME|  
|**адсчемакэйколумнусаже**|8|Возвращает столбцы, определенные в каталоге и ограниченные ключами данного пользователя.<br /><br /> (KEY_COLUMN_USAGE набор строк)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME|  
|**adSchemaLevels**|35|Возвращает сведения о уровнях, доступных в измерении.<br /><br /> (Набор строк уровня)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME LEVEL_NAME LEVEL_UNIQUE_NAME|  
|**адсчемамеасурес**|36|Возвращает сведения о доступных мерах.<br /><br /> (Наборы строк мер)|CATALOG_NAME SCHEMA_NAME CUBE_NAME MEASURE_NAME MEASURE_UNIQUE_NAME|  
|**adSchemaMembers**|38|Возвращает сведения о доступных элементах.<br /><br /> (Набор строк MEMBERs)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME LEVEL_UNIQUE_NAME LEVEL_NUMBER MEMBER_NAME MEMBER_UNIQUE_NAME MEMBER_CAPTION MEMBER_TYPE оператора Tree. Дополнительные сведения см. в разделе OLE DB для оперативной аналитической обработки (OLAP).|  
|**адсчемапримарикэйс**|28|Возвращает столбцы первичного ключа, определенные в каталоге данным пользователем.<br /><br /> (PRIMARY_KEYS набор строк)|PK_TABLE_CATALOG PK_TABLE_SCHEMA PK_TABLE_NAME|  
|**адсчемапроцедуреколумнс**|29|Возвращает информацию о столбцах наборов строк, возвращаемых процедурами.<br /><br /> (PROCEDURE_COLUMNS набор строк)|PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME COLUMN_NAME|  
|**адсчемапроцедурепараметерс**|26|Возвращает информацию о параметрах и кодах возврата процедур.<br /><br /> (PROCEDURE_PARAMETERS набор строк)|PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME PARAMETER_NAME|  
|**адсчемапроцедурес**|16|Возвращает процедуры, определенные в каталоге и принадлежащие данному пользователю.<br /><br /> (Набор строк процедур)|PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME PROCEDURE_TYPE|  
|**адсчемапропертиес**|37|Возвращает сведения о доступных свойствах для каждого уровня измерения.<br /><br /> (Набор строк свойств)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME LEVEL_UNIQUE_NAME MEMBER_UNIQUE_NAME PROPERTY_TYPE PROPERTY_NAME|  
|**адсчемапровидерспеЦифик**|-1|Используется, если поставщик определяет собственные нестандартные запросы схемы.|\<> конкретного поставщика|  
|**адсчемапровидертипес**|22|Возвращает типы данных (базовые), поддерживаемые поставщиком данных.<br /><br /> (PROVIDER_TYPES набор строк)|DATA_TYPE BEST_MATCH|  
|**адсчемареферентиалконстраинтс**|9|Возвращает ссылочные ограничения, определенные в каталоге и принадлежащие данному пользователю.<br /><br /> (REFERENTIAL_CONSTRAINTS набор строк)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME|  
|**адсчемасчемата**|17|Возвращает схемы (объекты базы данных), принадлежащие данному пользователю.<br /><br /> (Набор строк SCHEMATA)|CATALOG_NAME SCHEMA_NAME SCHEMA_OWNER|  
|**адсчемаскллангуажес**|18|Возвращает уровни соответствия, параметры и диалекты, поддерживаемые данными обработки реализации SQL, которые определены в каталоге.<br /><br /> (SQL_LANGUAGES набор строк)|\<Нет>|  
|**адсчемастатистикс**|19|Возвращает статистику, определенную в каталоге, принадлежащую данному пользователю.<br /><br /> (Набор строк статистики)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|**адсчематаблеконстраинтс**|10|Возвращает ограничения таблицы, определенные в каталоге и принадлежащие данному пользователю.<br /><br /> (TABLE_CONSTRAINTS набор строк)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME TABLE_CATALOG TABLE_SCHEMA TABLE_NAME CONSTRAINT_TYPE|  
|**адсчематаблепривилежес**|14|Возвращает привилегии для таблиц, определенных в каталоге и доступных указанному пользователю или предоставленных им.<br /><br /> (TABLE_PRIVILEGES набор строк)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME GRANTOR GRANTEE|  
|**адсчематаблес**|20|Возвращает таблицы (включая представления), определенные в каталоге и доступные указанному пользователю.<br /><br /> (Набор строк таблицы)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME TABLE_TYPE|  
|**адсчематранслатионс**|21|Возвращает переводы символов, определенные в каталоге и доступные указанному пользователю.<br /><br /> (Наборы строк ПЕРЕВОДов)|TRANSLATION_CATALOG TRANSLATION_SCHEMA TRANSLATION_NAME|  
|**адсчематрустис**|39|Зарезервировано для последующего использования.||  
|**адсчемаусажепривилежес**|15|Возвращает привилегии на использование для объектов, определенных в каталоге и доступных для данного пользователя или предоставленных ему.<br /><br /> (USAGE_PRIVILEGES набор строк)|OBJECT_CATALOG OBJECT_SCHEMA OBJECT_NAME OBJECT_TYPE ПРЕДОСТАВИЛ УЧАСТНИК|  
|**адсчемавиевколумнусаже**|24|Возвращает столбцы, от которых зависят просматриваемые таблицы, определенные в каталоге и принадлежащие данному пользователю.<br /><br /> (VIEW_COLUMN_USAGE набор строк)|VIEW_CATALOG VIEW_SCHEMA VIEW_NAME|  
|**адсчемавиевс**|23|Возвращает представления, определенные в каталоге и доступные для данного пользователя.<br /><br /> (Наборы строк ПРЕДСТАВЛЕНИЙ)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|**адсчемавиевтаблеусаже**|25|Возвращает таблицы, от которых зависят просматриваемые таблицы, определенные в каталоге и принадлежащие данному пользователю.<br /><br /> (VIEW_TABLE_USAGE набор строк)|VIEW_CATALOG VIEW_SCHEMA VIEW_NAME|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. Schema. ASSERTs|  
|Адоенумс. Schema. CATALOGs|  
|Адоенумс. Schema. ЧАРАКТЕРСЕТС|  
|Адоенумс. Schema. CHECKCONSTRAINTS|  
|Адоенумс. Schema. Collation|  
|Адоенумс. Schema. КОЛУМНПРИВИЛЕЖЕС|  
|Адоенумс. Schema. COLUMNs|  
|Адоенумс. Schema. КОЛУМНСДОМАИНУСАЖЕ|  
|Адоенумс. Schema. КОНСТРАИНТКОЛУМНУСАЖЕ|  
|Адоенумс. Schema. КОНСТРАИНТТАБЛЕУСАЖЕ|  
|Адоенумс. Schema. CUBEs|  
|Адоенумс. Schema. ДБИНФОКЭЙВОРДС|  
|Адоенумс. Schema. ДБИНФОЛИТЕРАЛС|  
|Адоенумс. Schema. DIMENSIONs|  
|Адоенумс. Schema. ФОРЕИГНКЭЙС|  
|Адоенумс. Schema. ИЕРАРХИИ|  
|Адоенумс. Schema. INDEXES|  
|Адоенумс. Schema. КЭЙКОЛУМНУСАЖЕ|  
|Адоенумс. Schema. LEVELs|  
|Адоенумс. Schema. MEASUREs|  
|Адоенумс. Schema. MEMBERs|  
|Адоенумс. Schema. ПРИМАРИКЭЙС|  
|Адоенумс. Schema. ПРОЦЕДУРЕКОЛУМНС|  
|Адоенумс. Schema. ПРОЦЕДУРЕПАРАМЕТЕРС|  
|Адоенумс. Schema. процедуры|  
|Адоенумс. Schema. PROPERTIES|  
|Адоенумс. Schema. ПРОВИДЕРСПЕЦИФИК|  
|Адоенумс. Schema. ПРОВИДЕРТИПЕС|  
|Адоенумс. Schema. РЕФЕРЕНТИАЛКОНТРАИНТС|  
|Адоенумс. Schema. SCHEMATA|  
|Адоенумс. Schema. СКЛЛАНГУАЖЕС|  
|Адоенумс. Schema. STATISTICS|  
|Адоенумс. Schema. ТАБЛЕКОНСТРАИНТС|  
|Адоенумс. Schema. ТАБЛЕПРИВИЛЕЖЕС|  
|Адоенумс. Schema. TABLEs|  
|Адоенумс. Schema. TRANSLATIONs|  
|Адоенумс. Schema. ДОВЕРЕНные лица|  
|Адоенумс. Schema. УСАЖЕПРИВИЛЕЖЕС|  
|Адоенумс. Schema. ВИЕВКОЛУМНУСАЖЕ|  
|Адоенумс. Schema. VIEWs|  
|Адоенумс. Schema. ВИЕВТАБЛЕУСАЖЕ|  
  
## <a name="applies-to"></a>Применяется к  
 [Метод OpenSchema](../../../ado/reference/ado-api/openschema-method.md)
