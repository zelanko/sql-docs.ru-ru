---
title: "Набор строк MDSCHEMA_DIMENSIONS | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: MDSCHEMA_DIMENSIONS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: MDSCHEMA_DIMENSIONS rowset
ms.assetid: a0fd94bb-359a-4df6-93a6-d60d50223944
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5cf0198759485452fc3fd6d82cdd2642df92b440
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="mdschemadimensions-rowset"></a>Набор строк MDSCHEMA_DIMENSIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Описывает общие и закрытые измерения в базе данных.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **MDSCHEMA_DIMENSIONS** набор строк содержит следующие столбцы:  
  
|Имя столбца|Индикатор типа|Description|  
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
|**CATALOG_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(Необязательно) Ограничение по умолчанию имеет значение 1. Битовая карта с одним из следующих допустимых значений:<br /><br /> 1 CUBE<br /><br /> 2 DIMENSION|  
|**DIMENSION_VISIBILITY**|**DBTYPE_UI2**|(Необязательно) Ограничение по умолчанию имеет значение 1. Битовая карта с одним из следующих допустимых значений:<br /><br /> 1 Отображается<br /><br /> 2 Не отображается|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы OLE DB для OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
