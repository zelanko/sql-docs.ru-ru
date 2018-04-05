---
title: MDSCHEMA_MEASUREGROUP_DIMENSIONS, набор строк | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- MDSCHEMA_MEASUREGROUP_DIMENSIONS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MDSCHEMA_MEASUREGROUP_DIMENSIONS rowset
ms.assetid: c731c06a-7382-4e50-ba0e-d8cee3ab4f28
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 62ee9e17d9f53d981e5e44918ec690c9abceddbb
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="mdschemameasuregroupdimensions-rowset"></a>MDSCHEMA_MEASUREGROUP_DIMENSIONS, набор строк
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Перечисляет измерения группы мер.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **MDSCHEMA_MEASUREGROUP_DIMENSIONS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
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
|**CATALOG_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**DIMENSION_VISIBILITY**|**DBTYPE_UI2**|Битовая карта с одним из следующих допустимых значений (необязательно).<br /><br /> 1 Отображается<br /><br /> 2 Не отображается<br /><br /> Значение по умолчанию для ограничения — 1.|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы OLE DB для OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
