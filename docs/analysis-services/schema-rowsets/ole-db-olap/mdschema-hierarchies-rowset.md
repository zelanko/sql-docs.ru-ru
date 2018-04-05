---
title: Набор строк MDSCHEMA_HIERARCHIES | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- MDSCHEMA_HIERARCHIES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MDSCHEMA_HIERARCHIES rowset
ms.assetid: 2e5b2a81-366e-4d5b-af1e-1d372bf596d9
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7ecdc6817c5a2d7e1e88b909080a3156c55f40eb
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="mdschemahierarchies-rowset"></a>Набор строк MDSCHEMA_HIERARCHIES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Описывает каждую иерархию в конкретном измерении.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **MDSCHEMA_HIERARCHIES** набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Имя каталога, которому принадлежит эта иерархия. Имеет значение**NULL** , если поставщик не поддерживает каталоги.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Не поддерживается|  
|**CUBE_NAME**|**DBTYPE_WSTR**|(Обязательно) Имя куба, которому принадлежит эта иерархия.|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|Уникальное имя измерения, которому принадлежит эта иерархия. Для поставщиков, формирующих уникальные имена путем использования квалификаторов, компоненты имени разделяются между собой.|  
|**HIERARCHY_NAME**|**DBTYPE_WSTR**|Имя иерархии. Пустое, если имеется только одна иерархия в измерении. Это всегда будет иметь значение [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|Уникальное имя иерархии.|  
|**HIERARCHY_GUID**|**DBTYPE_GUID**|Не поддерживается|  
|**HIERARCHY_CAPTION**|**DBTYPE_WSTR**|Метка или заголовок, связанный с иерархией. В основном используется в целях отображения. Если заголовок не существует, **HIERARCHY_NAME** возвращается. Если измерение не содержит иерархию или имеет только одну иерархию, то этот столбец будет содержать имя измерения.|  
|**DIMENSION_TYPE**|**DBTYPE_I2**|Тип измерения. К допустимым значениям относятся:<br /><br /> **MD_DIMTYPE_UNKNOWN** (**0**)<br /><br /> **MD_DIMTYPE_TIME** (**1**)<br /><br /> **MD_DIMTYPE_MEASURE** (**2**)<br /><br /> **MD_DIMTYPE_OTHER** (**3**)<br /><br /> **MD_DIMTYPE_QUANTITATIVE** (**5**)<br /><br /> **MD_DIMTYPE_ACCOUNTS** (**6**)<br /><br /> **MD_DIMTYPE_CUSTOMERS** (**7**)<br /><br /> **MD_DIMTYPE_PRODUCTS** (**8**)<br /><br /> **MD_DIMTYPE_SCENARIO** (**9**)<br /><br /> **MD_DIMTYPE_UTILIY** (**10**)<br /><br /> **MD_DIMTYPE_CURRENCY** (**11**)<br /><br /> **MD_DIMTYPE_RATES** (**12**)<br /><br /> **MD_DIMTYPE_CHANNEL** (**13**)<br /><br /> **MD_DIMTYPE_PROMOTION** (**14**)<br /><br /> **MD_DIMTYPE_ORGANIZATION** (**15**)<br /><br /> **MD_DIMTYPE_BILL_OF_MATERIALS** (**16**)<br /><br /> **MD_DIMTYPE_GEOGRAPHY** (**17**)|  
|**HIERARCHY_CARDINALITY**|**DBTYPE_UI4**|Количество элементов в иерархии.|  
|**DEFAULT_MEMBER**|**DBTYPE_WSTR**|Элемент по умолчанию для этой иерархии. Это уникальное имя. Каждая иерархия должна иметь элемент по умолчанию.|  
|**ALL_MEMBER**|**DBTYPE_WSTR**|Элемент на самом высоком уровне свертки.|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Возвращает понятное описание иерархии. **Значение NULL** Если описания не существует.|  
|**СТРУКТУРА**|**DBTYPE_I2**|Структура иерархии. К допустимым значениям относятся:<br /><br /> **MD_STRUCTURE_FULLYBALANCED** (**0**)<br /><br /> **MD_STRUCTURE_RAGGEDBALANCED** (**1**)<br /><br /> **MD_STRUCTURE_UNBALANCED** (**2**)<br /><br /> **MD_STRUCTURE_NETWORK** (**3**)|  
|**IS_VIRTUAL**|**DBTYPE_BOOL**|Всегда возвращает **False**.|  
|**IS_READWRITE**|**DBTYPE_BOOL**|Логическое значение, указывающее, включен ли режим обратной записи в столбец измерения.<br /><br /> Возвращает **TRUE** Если **режим обратной записи в измерение** включен столбец, который представляет эту иерархию.|  
|**DIMENSION_UNIQUE_SETTINGS**|**DBTYPE_I4**|Всегда возвращает **MDDIMENSIONS_MEMBER_KEY_UNIQUE** (**1**).|  
|**DIMENSION_MASTER_UNIQUE_NAME**|**DBTYPE_WSTR**|Всегда возвращает **NULL**.|  
|**DIMENSION_IS_VISIBLE**|**DBTYPE_BOOL**|Всегда возвращает **true**. Если измерение невидимо, то оно не отображается в наборе строк схемы.|  
|**HIERARCHY_ORDINAL**|**DBTYPE_UI4**|Порядковый номер иерархии во всех иерархиях куба.|  
|**DIMENSION_IS_SHARED**|**DBTYPE_BOOL**|Всегда возвращает **TRUE**.|  
|**HIERARCHY_IS_VISIBLE**|**DBTYPE_BOOL**|Логическое значение, указывающее, видима ли иерархия.<br /><br /> Возвращает **TRUE** Если иерархии является видимым; в противном случае — **FALSE**.|  
|**HIERARCHY_ORIGIN**|**DBTYPE_UI2**|Битовая маска, определяющая источник иерархии.<br /><br /> **MD_USER_DEFINED** определяет пользовательские иерархии и имеет значение **0x0000001**.<br /><br /> **MD_SYSTEM_ENABLED** определяет иерархии атрибутов и имеет значение **0x0000002**.<br /><br /> **MD_SYSTEM_INTERNAL** определяет атрибуты без иерархий атрибутов и имеет значение **0x0000004**.<br /><br /> <br /><br /> Обратите внимание, что атрибут иерархии родители потомки оба **MD_USER_DEFINED** и **MD_SYSTEM_ENABLED**.|  
|**HIERARCHY_DISPLAY_FOLDER**|**DBTYPE_WSTR**|Путь, используемый при отображении иерархии в пользовательском интерфейсе. Имена папок разделяются символом точки с запятой (;). Вложенные папки указываются обратная косая черта (\\).|  
|**INSTANCE_SELECTION**|**DBTYPE_UI2**|Указание иерархии для клиентского приложения по методу отображения. К допустимым значениям относятся:<br /><br /> **MD_INSTANCE_SELECTION_NONE**<br /><br /> **MD_INSTANCE_SELECTION_DROPDOWN**<br /><br /> **MD_INSTANCE_SELECTION_LIST**<br /><br /> **MD_INSTANCE_SELECTION_FILTEREDLIST**<br /><br /> **MD_INSTANCE_SELECTION_MANDATORYFILTER**|  
|**GROUPING_BEHAVIOR**|**DBTYPE_I2**|Перечисление, определяющее ожидаемый режим группирования клиентов для этой иерархии. Возможны следующие значения:<br /><br /> **EncourageGrouping** (1)<br /><br /> **DiscourageGrouping** (2)|  
|**STRUCTURE_TYPE**|**DBTYPE_WSTR**|Указывает тип иерархии. К допустимым значениям относятся:<br /><br /> **Естественное**<br /><br /> **Искусственных**<br /><br /> **Unknown**|  
  
 Набор строк отсортирован по **CATALOG_NAME**, **имя_схемы**, **CUBE_NAME**, **DIMENSION_UNIQUE_NAME**, **HIERARCHY_ ИМЯ**.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 **MDSCHEMA_HIERARCHIES** строк может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**HIERARCHY_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**HIERARCHY_ORIGIN**|**DBTYPE_UI2**|(Необязательно) Ограничение по умолчанию действует на MD_USER_DEFINED и MD_SYSTEM_ENABLED.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(Необязательно) Ограничение по умолчанию имеет значение 1. Битовая карта с одним из следующих допустимых значений:<br /><br /> 1 CUBE<br /><br /> 2 DIMENSION|  
|**HIERARCHY_VISIBILITY**|**DBTYPE_UI2**|(Необязательно) Ограничение по умолчанию имеет значение 1. Битовая карта с одним из следующих допустимых значений:<br /><br /> 1 Отображается<br /><br /> 2 Не отображается|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы OLE DB для OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
