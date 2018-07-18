---
title: Набор строк MDSCHEMA_HIERARCHIES | Документация Майкрософт
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
- MDSCHEMA_HIERARCHIES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_HIERARCHIES rowset
ms.assetid: 2e5b2a81-366e-4d5b-af1e-1d372bf596d9
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a38dd03023fc266c5b8505979766d90979d16f05
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37321224"
---
# <a name="mdschemahierarchies-rowset"></a>Набор строк MDSCHEMA_HIERARCHIES
  Описывает каждую иерархию в конкретном измерении.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `MDSCHEMA_HIERARCHIES` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Имя каталога, которому принадлежит эта иерархия. Имеет значение `NULL`, если поставщик не поддерживает каталоги.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Не поддерживается|  
|`CUBE_NAME`|`DBTYPE_WSTR`||(Обязательно) Имя куба, которому принадлежит эта иерархия.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Уникальное имя измерения, которому принадлежит эта иерархия. Для поставщиков, формирующих уникальные имена путем использования квалификаторов, компоненты имени разделяются между собой.|  
|`HIERARCHY_NAME`|`DBTYPE_WSTR`||Имя иерархии. Пустое, если имеется только одна иерархия в измерении. Это всегда будет иметь значение [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`||Уникальное имя иерархии.|  
|`HIERARCHY_GUID`|`DBTYPE_GUID`||Не поддерживается|  
|`HIERARCHY_CAPTION`|`DBTYPE_WSTR`||Метка или заголовок, связанный с иерархией. В основном используется в целях отображения. Если заголовок не существует, возвращается `HIERARCHY_NAME`. Если измерение не содержит иерархию или имеет только одну иерархию, то этот столбец будет содержать имя измерения.|  
|`DIMENSION_TYPE`|`DBTYPE_I2`||Тип измерения. К допустимым значениям относятся:<br /><br /> -   `MD_DIMTYPE_UNKNOWN` (`0`)<br />-   `MD_DIMTYPE_TIME` (`1`)<br />-   `MD_DIMTYPE_MEASURE` (`2`)<br />-   `MD_DIMTYPE_OTHER` (`3`)<br />-   `MD_DIMTYPE_QUANTITATIVE` (`5`)<br />-   `MD_DIMTYPE_ACCOUNTS` (`6`)<br />-   `MD_DIMTYPE_CUSTOMERS` (`7`)<br />-   `MD_DIMTYPE_PRODUCTS` (`8`)<br />-   `MD_DIMTYPE_SCENARIO` (`9`)<br />-   `MD_DIMTYPE_UTILIY` (`10`)<br />-   `MD_DIMTYPE_CURRENCY` (`11`)<br />-   `MD_DIMTYPE_RATES` (`12`)<br />-   `MD_DIMTYPE_CHANNEL` (`13`)<br />-   `MD_DIMTYPE_PROMOTION` (`14`)<br />-   `MD_DIMTYPE_ORGANIZATION` (`15`)<br />-   `MD_DIMTYPE_BILL_OF_MATERIALS` (`16`)<br />-   `MD_DIMTYPE_GEOGRAPHY` (`17`)|  
|`HIERARCHY_CARDINALITY`|`DBTYPE_UI4`||Количество элементов в иерархии.|  
|`DEFAULT_MEMBER`|`DBTYPE_WSTR`||Элемент по умолчанию для этой иерархии. Это уникальное имя. Каждая иерархия должна иметь элемент по умолчанию.|  
|`ALL_MEMBER`|`DBTYPE_WSTR`||Элемент на самом высоком уровне свертки.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Возвращает понятное описание иерархии. Имеет значение `NULL`, если описание отсутствует.|  
|`STRUCTURE`|`DBTYPE_I2`||Структура иерархии. К допустимым значениям относятся:<br /><br /> -   `MD_STRUCTURE_FULLYBALANCED` (`0`)<br />-   `MD_STRUCTURE_RAGGEDBALANCED` (`1`)<br />-   `MD_STRUCTURE_UNBALANCED` (`2`)<br />-   `MD_STRUCTURE_NETWORK` (`3`)|  
|`IS_VIRTUAL`|`DBTYPE_BOOL`||Всегда возвращает `False`.|  
|`IS_READWRITE`|`DBTYPE_BOOL`||Логическое значение, указывающее, включен ли режим обратной записи в столбец измерения.<br /><br /> Возвращает `TRUE`, если включен столбец `Write Back to dimension`, который представляет эту иерархию.|  
|`DIMENSION_UNIQUE_SETTINGS`|`DBTYPE_I4`||Всегда возвращает `MDDIMENSIONS_MEMBER_KEY_UNIQUE` (`1`).|  
|`DIMENSION_MASTER_UNIQUE_NAME`|`DBTYPE_WSTR`||Всегда возвращает `NULL`.|  
|`DIMENSION_IS_VISIBLE`|`DBTYPE_BOOL`||Всегда возвращает `true`. Если измерение невидимо, то оно не отображается в наборе строк схемы.|  
|`HIERARCHY_ORDINAL`|`DBTYPE_UI4`||Порядковый номер иерархии во всех иерархиях куба.|  
|`DIMENSION_IS_SHARED`|`DBTYPE_BOOL`||Всегда возвращает `TRUE`.|  
|`HIERARCHY_IS_VISIBLE`|`DBTYPE_BOOL`||Логическое значение, указывающее, видима ли иерархия.<br /><br /> Возвращает значение `TRUE`, если иерархия видима, в противном случае — `FALSE`.|  
|`HIERARCHY_ORIGIN`|`DBTYPE_UI2`||Битовая маска, определяющая источник иерархии.<br /><br /> -   `MD_USER_DEFINED` Определяет пользовательские иерархии и имеет значение `0x0000001`.<br />-   `MD_SYSTEM_ENABLED` Определяет иерархии атрибутов и имеет значение `0x0000002`.<br />-   `MD_SYSTEM_INTERNAL` Определяет атрибуты без иерархий атрибутов и имеет значение **0x0000004**.<br /><br /> Иерархия родительских/дочерних атрибутов является и `MD_USER_DEFINED`, и `MD_SYSTEM_ENABLED`.|  
|`HIERARCHY_DISPLAY_FOLDER`|`DBTYPE_WSTR`||Путь, используемый при отображении иерархии в пользовательском интерфейсе. Имена папок разделяются символом точки с запятой (;). Вложенные папки указываются символами обратной косой черты (\\).|  
|`INSTANCE_SELECTION`|`DBTYPE_UI2`||Указание иерархии для клиентского приложения по методу отображения. К допустимым значениям относятся:<br /><br /> -   `MD_INSTANCE_SELECTION_NONE`<br />-   `MD_INSTANCE_SELECTION_DROPDOWN`<br />-   `MD_INSTANCE_SELECTION_LIST`<br />-   `MD_INSTANCE_SELECTION_FILTEREDLIST`<br />-   `MD_INSTANCE_SELECTION_MANDATORYFILTER`|  
|`GROUPING_BEHAVIOR`|`DBTYPE_I2`||Перечисление, определяющее ожидаемый режим группирования клиентов для этой иерархии. Возможны следующие значения:<br /><br /> -   **EncourageGrouping** (1)<br />-   **DiscourageGrouping** (2)|  
|`STRUCTURE_TYPE`|`DBTYPE_WSTR`||Указывает тип иерархии. К допустимым значениям относятся:<br /><br /> -   `Natural`<br />-   `Unnatural`<br />-   `Unknown`|  
  
 Набор строк отсортирован по полям `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `DIMENSION_UNIQUE_NAME`, `HIERARCHY_NAME`.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `MDSCHEMA_HIERARCHIES` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`HIERARCHY_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`HIERARCHY_ORIGIN`|`DBTYPE_UI2`|(Необязательно) Ограничение по умолчанию действует на MD_USER_DEFINED и MD_SYSTEM_ENABLED.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|Битовая карта с одним из следующих допустимых значений (необязательно).<br /><br /> -КУБ 1<br />— ИЗМЕРЕНИЯ 2<br /><br /> Значение по умолчанию для ограничения — 1.|  
|`HIERARCHY_VISIBILITY`|`DBTYPE_UI2`|Битовая карта с одним из следующих допустимых значений (необязательно).<br /><br /> -1 Visible<br />-2 не отображается<br /><br /> Значение по умолчанию для ограничения — 1.|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы OLE DB для OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
