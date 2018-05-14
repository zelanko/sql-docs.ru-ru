---
title: Набор строк MDSCHEMA_DIMENSIONS | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e1e509ad466a0d173fe67a8fd1f3ac5190647eb7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="mdschemadimensions-rowset"></a>Набор строк MDSCHEMA_DIMENSIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Описывает общие и закрытые измерения в базе данных.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **MDSCHEMA_DIMENSIONS** набор строк содержит следующие столбцы:  
  
|Имя столбца|Индикатор типа|Описание|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Имя базы данных.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Не поддерживается.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Имя куба.|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**|Имя измерения. Если измерение является частью нескольких кубов или групп мер, тогда имеется одна строка для каждого уникального сочетания измерения, группы мер и куба.|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|Уникальное имя измерения.|  
|**DIMENSION_GUID**|**DBTYPE_GUID**|Не поддерживается.|  
|**DIMENSION_CAPTION**|**DBTYPE_WSTR**|Заголовок измерения. Он должен использоваться при отображении имени измерения для пользователя, такого как пользовательский интерфейс или отчеты.|  
|**DIMENSION_ORDINAL**|**DBTYPE_UI4**|Позиция измерения в кубе.|  
|**DIMENSION_TYPE**|**DBTYPE_I2**|Тип измерения. Допустимы следующие значения.<br /><br /> **MD_DIMTYPE_UNKNOWN** (**0**)<br /><br /> **MD_DIMTYPE_TIME** (**1**)<br /><br /> **MD_DIMTYPE_MEASURE** (**2**)<br /><br /> **MD_DIMTYPE_OTHER** (**3**)<br /><br /> **MD_DIMTYPE_QUANTITATIVE** (**5**)<br /><br /> **MD_DIMTYPE_ACCOUNTS** (**6**)<br /><br /> **MD_DIMTYPE_CUSTOMERS** (**7**)<br /><br /> **MD_DIMTYPE_PRODUCTS** (**8**)<br /><br /> **MD_DIMTYPE_SCENARIO** (**9**)<br /><br /> **MD_DIMTYPE_UTILIY** (**10**)<br /><br /> **MD_DIMTYPE_CURRENCY** (**11**)<br /><br /> **MD_DIMTYPE_RATES** (**12**)<br /><br /> **MD_DIMTYPE_CHANNEL** (**13**)<br /><br /> **MD_DIMTYPE_PROMOTION** (**14**)<br /><br /> **MD_DIMTYPE_ORGANIZATION** (**15**)<br /><br /> **MD_DIMTYPE_BILL_OF_MATERIALS** (**16**)<br /><br /> **MD_DIMTYPE_GEOGRAPHY** (**17**)|  
|**DIMENSION_CARDINALITY**|**DBTYPE_UI4**|Количество элементов является ключевым атрибутом.|  
|**DEFAULT_HIERARCHY**|**DBTYPE_WSTR**|Иерархия из измерения. Сохранена для обратной совместимости.|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Понятное описание измерения.|  
|**IS_VIRTUAL**|**DBTYPE_BOOL**|Всегда **FALSE**.|  
|**IS_READWRITE**|**DBTYPE_BOOL**|Логическое значение, указывающее, доступно ли измерение для записи.<br /><br /> **Значение TRUE,** Если измерение доступно для записи.|  
|**DIMENSION_UNIQUE_SETTINGS**|**DBTYPE_I4**|Битовая карта, указывающая столбцы, которые содержат уникальные значения, если измерение содержит только элементы с уникальными именами. В файле Msmd.h определены следующие битовые константы для этой битовой карты:<br /><br /> **MDDIMENSIONS_MEMBER_KEY_UNIQUE**|  
|**DIMENSION_MASTER_UNIQUE_NAME**|**DBTYPE_WSTR**|Всегда **NULL**.|  
|**DIMENSION_IS_VISIBLE**|**DBTYPE_BOOL**|Всегда **TRUE**.<br /><br /> Примечание:. Если один или несколько иерархий в измерении видимы в измерение не отображается.|  
  
 Набор строк отсортирован по **CATALOG_NAME**, **имя_схемы**, **CUBE_NAME**, **DIMENSION_NAME**.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 **MDSCHEMA_DIMENSIONS** строк может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(Необязательно) Ограничение по умолчанию имеет значение 1. Битовая карта с одним из следующих допустимых значений:<br /><br /> 1 CUBE<br /><br /> 2 DIMENSION|  
|**DIMENSION_VISIBILITY**|**DBTYPE_UI2**|(Необязательно) Ограничение по умолчанию имеет значение 1. Битовая карта с одним из следующих допустимых значений:<br /><br /> 1 Отображается<br /><br /> 2 Не отображается|  
  
## <a name="see-also"></a>См. также  
 [OLE DB для OLAP наборы строк схемы](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
