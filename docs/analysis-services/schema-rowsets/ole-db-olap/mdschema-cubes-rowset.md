---
title: "Набор строк MDSCHEMA_CUBES | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: MDSCHEMA_CUBES
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: MDSCHEMA_CUBES rowset
ms.assetid: 5f1b63d4-aa3f-48c6-b866-7ffd91675044
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3ff85f0461a9ca0abc7c9acdfdd4cb2b23722c41
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="mdschemacubes-rowset"></a>Набор строк MDSCHEMA_CUBES
  Описывает структуру кубов в базе данных.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **MDSCHEMA_CUBES** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Имя базы данных.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Не поддерживается.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Имя куба или измерения. Перед именами измерений указывается знак доллара ($).<br /><br /> Примечание: Только администраторы сервера и базы данных имеют разрешения для просмотра кубов, созданных из измерения.|  
|**CUBE_TYPE**|**DBTYPE_WSTR**|Тип куба. Допустимые значения:<br /><br /> **КУБ**<br /><br /> **ИЗМЕРЕНИЯ**|  
|**CUBE_GUID**|**DBTYPE_GUID**|Не поддерживается.|  
|**CREATED_ON**|**DBTYPE_DBTIMESTAMP**|Не поддерживается.|  
|**LAST_SCHEMA_UPDATE**|**DBTYPE_DBTIMESTAMP**|Время последней обработки куба.|  
|**SCHEMA_UPDATED_BY**|**DBTYPE_WSTR**|Не поддерживается.|  
|**LAST_DATA_UPDATE**|**DBTYPE_DBTIMESTAMP**|Время последней обработки куба.|  
|**DATA_UPDATED_BY**|**DBTYPE_WSTR**|Не поддерживается.|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Понятное описание куба.|  
|**IS_DRILLTHROUGH_ENABLED**|**DBTYPE_BOOL**|Логическое значение, всегда возвращается true.|  
|**IS_LINKABLE**|**DBTYPE_BOOL**|Логическое значение, указывающее, можно ли использовать куб в связанном кубе.|  
|**IS_WRITE_ENABLED**|**DBTYPE_BOOL**|Логическое значение, указывающее, доступен ли куб для записи.|  
|**IS_SQL_ENABLED**|**DBTYPE_BOOL**|Логическое значение, указывающее, может ли использоваться SQL в кубе.|  
|**CUBE_CAPTION**|**DBTYPE_WSTR**|Заголовок куба.|  
|**BASE_CUBE_NAME**|**DBTYPE_WSTR**|Имя исходного куба, если этот куб является кубом перспективы.|  
|**ЗАМЕТКИ**|**DBTYPE_WSTR**|Набор примечаний в формате XML (необязательно).|  
  
 Набор строк отсортирован по **CATALOG_NAME**, **SCHEMA_NAME**, **CUBE_NAME**.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **MDSCHEMA_CUBES** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(Необязательно) Ограничение по умолчанию имеет значение 1. Битовая карта с одним из следующих допустимых значений:<br /><br /> 1 CUBE<br /><br /> 2 DIMENSION|  
|**Базовый Cube_Name**|**DBTYPE_WSTR**|Необязательно.|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы OLE DB для OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
