---
title: Набор строк MDSCHEMA_DIMENSIONS | Документы Microsoft
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
- MDSCHEMA_DIMENSIONS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_DIMENSIONS rowset
ms.assetid: a0fd94bb-359a-4df6-93a6-d60d50223944
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b00b617adf90e1dba8eac94a9872ce07c0773e7c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095806"
---
# <a name="mdschemadimensions-rowset"></a>Набор строк MDSCHEMA_DIMENSIONS
  Описывает общие и закрытые измерения в базе данных.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк `MDSCHEMA_DIMENSIONS` содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Имя базы данных.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Не поддерживается.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Имя куба.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||Имя измерения. Если измерение является частью нескольких кубов или групп мер, тогда имеется одна строка для каждого уникального сочетания измерения, группы мер и куба.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Уникальное имя измерения.|  
|`DIMENSION_GUID`|`DBTYPE_GUID`||Не поддерживается.|  
|`DIMENSION_CAPTION`|`DBTYPE_WSTR`||Заголовок измерения. Он должен использоваться при отображении имени измерения для пользователя, такого как пользовательский интерфейс или отчеты.|  
|`DIMENSION_ORDINAL`|`DBTYPE_UI4`||Позиция измерения в кубе.|  
|`DIMENSION_TYPE`|`DBTYPE_I2`||Тип измерения. Допустимы следующие значения.<br /><br /> -   `MD_DIMTYPE_UNKNOWN` (`0`)<br />-   `MD_DIMTYPE_TIME` (`1`)<br />-   `MD_DIMTYPE_MEASURE` (`2`)<br />-   `MD_DIMTYPE_OTHER` (`3`)<br />-   `MD_DIMTYPE_QUANTITATIVE` (`5`)<br />-   `MD_DIMTYPE_ACCOUNTS` (`6`)<br />-   `MD_DIMTYPE_CUSTOMERS` (`7`)<br />-   `MD_DIMTYPE_PRODUCTS` (`8`)<br />-   `MD_DIMTYPE_SCENARIO` (`9`)<br />-   `MD_DIMTYPE_UTILIY` (`10`)<br />-   `MD_DIMTYPE_CURRENCY` (`11`)<br />-   `MD_DIMTYPE_RATES` (`12`)<br />-   `MD_DIMTYPE_CHANNEL` (`13`)<br />-   `MD_DIMTYPE_PROMOTION` (`14`)<br />-   `MD_DIMTYPE_ORGANIZATION` (`15`)<br />-   `MD_DIMTYPE_BILL_OF_MATERIALS` (`16`)<br />-   `MD_DIMTYPE_GEOGRAPHY` (`17`)|  
|`DIMENSION_CARDINALITY`|`DBTYPE_UI4`||Количество элементов является ключевым атрибутом.|  
|`DEFAULT_HIERARCHY`|`DBTYPE_WSTR`||Иерархия из измерения. Сохранена для обратной совместимости.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Понятное описание измерения.|  
|`IS_VIRTUAL`|`DBTYPE_BOOL`||Всегда возвращает значение `FALSE`.|  
|`IS_READWRITE`|`DBTYPE_BOOL`||Логическое значение, указывающее, доступно ли измерение для записи.<br /><br /> Значение `TRUE`, если измерение доступно для записи.|  
|`DIMENSION_UNIQUE_SETTINGS`|`DBTYPE_I4`||Битовая карта, указывающая столбцы, которые содержат уникальные значения, если измерение содержит только элементы с уникальными именами. В файле Msmd.h определены следующие битовые константы для этой битовой карты:<br /><br /> -   `MDDIMENSIONS_MEMBER_KEY_UNIQUE`|  
|`DIMENSION_MASTER_UNIQUE_NAME`|`DBTYPE_WSTR`||Всегда возвращает значение `NULL`.|  
|`DIMENSION_IS_VISIBLE`|`DBTYPE_BOOL`||Всегда возвращает значение `TRUE`. **Примечание:** измерение не отображается, если не видны один или несколько иерархий в измерении.|  
  
 Набор строк отсортирован по полям `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `DIMENSION_NAME`.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `MDSCHEMA_DIMENSIONS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|Битовая карта с одним из следующих допустимых значений (необязательно).<br /><br /> -КУБ 1<br />-2 ИЗМЕРЕНИЯ.<br /><br /> Значение по умолчанию для ограничения — 1.|  
|`DIMENSION_VISIBILITY`|`DBTYPE_UI2`|Битовая карта с одним из следующих допустимых значений (необязательно).<br /><br /> — Visible 1<br />-2 не отображается<br /><br /> Значение по умолчанию для ограничения — 1.|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы OLE DB для OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  