---
title: Набор строк MDSCHEMA_CUBES | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_CUBES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_CUBES rowset
ms.assetid: 5f1b63d4-aa3f-48c6-b866-7ffd91675044
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7282ceaacc4778c205c27e6ef226855f94398be1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048404"
---
# <a name="mdschemacubes-rowset"></a>Набор строк MDSCHEMA_CUBES
  Описывает структуру кубов в базе данных.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `MDSCHEMA_CUBES` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Имя базы данных.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Не поддерживается.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Имя куба или измерения. Перед именами измерений указывается знак доллара ($). **Примечание:** только администраторы базы данных сервера и иметь разрешения на просмотр кубов, созданных из измерения.|  
|`CUBE_TYPE`|`DBTYPE_WSTR`||Тип куба. Допустимые значения:<br /><br /> -   `CUBE`<br />-   `DIMENSION`|  
|`CUBE_GUID`|`DBTYPE_GUID`||Не поддерживается.|  
|`CREATED_ON`|`DBTYPE_DBTIMESTAMP`||Не поддерживается.|  
|`LAST_SCHEMA_UPDATE`|`DBTYPE_DBTIMESTAMP`||Время последней обработки куба.|  
|`SCHEMA_UPDATED_BY`|`DBTYPE_WSTR`||Не поддерживается.|  
|`LAST_DATA_UPDATE`|`DBTYPE_DBTIMESTAMP`||Время последней обработки куба.|  
|`DATA_UPDATED_BY`|`DBTYPE_WSTR`||Не поддерживается.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Понятное описание куба.|  
|`IS_DRILLTHROUGH_ENABLED`|`DBTYPE_BOOL`||Логическое значение, всегда возвращается true.|  
|`IS_LINKABLE`|`DBTYPE_BOOL`||Логическое значение, указывающее, можно ли использовать куб в связанном кубе.|  
|`IS_WRITE_ENABLED`|`DBTYPE_BOOL`||Логическое значение, указывающее, доступен ли куб для записи.|  
|`IS_SQL_ENABLED`|`DBTYPE_BOOL`||Логическое значение, указывающее, может ли использоваться SQL в кубе.|  
|`CUBE_CAPTION`|`DBTYPE_WSTR`||Заголовок куба.|  
|`BASE_CUBE_NAME`|`DBTYPE_WSTR`||Имя исходного куба, если этот куб является кубом перспективы.|  
|`ANNOTATIONS`|`DBTYPE_WSTR`||Набор примечаний в формате XML (необязательно).|  
  
 Набор строк отсортирован по `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `MDSCHEMA_CUBES` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Необязательно) Битовая карта с одним из этих допустимых значений.<br /><br /> -КУБ 1<br />— ИЗМЕРЕНИЯ 2<br /><br /> Значение по умолчанию для ограничения — 1.|  
|`Base Cube_Name`|`DBTYPE_WSTR`|Необязательный параметр.|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы OLE DB для OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
