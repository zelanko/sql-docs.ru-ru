---
title: MDSCHEMA_MEASUREGROUP_DIMENSIONS, набор строк | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 817507a53e327c6fdb16f73d3b0eb0fb5c264f24
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34032925"
---
# <a name="mdschemameasuregroupdimensions-rowset"></a>MDSCHEMA_MEASUREGROUP_DIMENSIONS, набор строк
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Перечисляет измерения группы мер.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **MDSCHEMA_MEASUREGROUP_DIMENSIONS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||Имя каталога, которому принадлежит группа мер. Имеет значение**NULL** , если поставщик не поддерживает каталоги.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||Не поддерживается.|  
|**CUBE_NAME**|**DBTYPE_WSTR**||Имя куба, которому принадлежит группа мер.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**||Имя группы мер.|  
|**MEASUREGROUP_CARDINALITY**|**DBTYPE_WSTR**||Число экземпляров, которое мера в группе мер может иметь для одного элемента измерения. Возможные значения.<br /><br /> **ОДИН**<br /><br /> **МНОГИЕ**|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**||Уникальное имя для измерения.|  
|**DIMENSION_CARDINALITY**|**DBTYPE_WSTR**||Количество экземпляров, которое элемент измерения может иметь для одного экземпляра меры групп мер. Возможные значения.<br /><br /> **ОДИН**<br /><br /> **МНОГИЕ**|  
|**DIMENSION_IS_VISIBLE**|**DBTYPE_BOOL**||Логическое значение, указывающее, видимы ли иерархии в измерении.<br /><br /> Возвращает значение **TRUE** , если одна или несколько иерархий в измерении видимы, в противном случае — значение **FALSE**.|  
|**DIMENSION_IS_FACT_DIMENSION**|**DBTYPE_BOOL**||Логическое значение, указывающее, является ли измерение измерением фактов.<br /><br /> Возвращает значение **TRUE** , если измерение является измерением фактов, в противном случае — значение **FALSE**.|  
|**DIMENSION_PATH**|**DBTYPE_HCHAPTER**||Список измерений для ссылочного измерения.|  
|**DIMENSION_GRANULARITY**|**DBTYPE_WSTR**||Уникальное имя иерархии гранулярности.|  
  
 Набор строк поддерживает сортировку по **CATALOG_NAME**, **SCHEMA_NAME**, **CUBE_NAME**, **MEASUREGROUP_NAME**, **DIMENSION_UNIQUE_NAME**.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **MDSCHEMA_MEASUREGROUP_DIMENSIONS** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**DIMENSION_VISIBILITY**|**DBTYPE_UI2**|Битовая карта с одним из следующих допустимых значений (необязательно).<br /><br /> 1 Отображается<br /><br /> 2 Не отображается<br /><br /> Значение по умолчанию для ограничения — 1.|  
  
## <a name="see-also"></a>См. также  
 [OLE DB для OLAP наборы строк схемы](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
