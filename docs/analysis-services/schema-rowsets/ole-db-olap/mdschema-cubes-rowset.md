---
title: Набор строк MDSCHEMA_CUBES | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 82a07fda14984582ae9461d861df0fa47920b527
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mdschemacubes-rowset"></a>Набор строк MDSCHEMA_CUBES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Описывает структуру кубов в базе данных.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **MDSCHEMA_CUBES** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Описание|  
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
  
## <a name="see-also"></a>См. также  
 [OLE DB для OLAP наборы строк схемы](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
