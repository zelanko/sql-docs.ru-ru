---
title: MDSCHEMA_MEASUREGROUP_DIMENSIONS, набор строк | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MDSCHEMA_MEASUREGROUP_DIMENSIONS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_MEASUREGROUP_DIMENSIONS rowset
ms.assetid: c731c06a-7382-4e50-ba0e-d8cee3ab4f28
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: f607b966099f71acee460a5a343c557e2a81857e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097356"
---
# <a name="mdschemameasuregroupdimensions-rowset"></a>MDSCHEMA_MEASUREGROUP_DIMENSIONS, набор строк
  Перечисляет измерения группы мер.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `MDSCHEMA_MEASUREGROUP_DIMENSIONS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Имя каталога, которому принадлежит группа мер. Имеет значение `NULL`, если поставщик не поддерживает каталоги.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Не поддерживается.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Имя куба, которому принадлежит группа мер.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`||Имя группы мер.|  
|`MEASUREGROUP_CARDINALITY`|`DBTYPE_WSTR`||Число экземпляров, которое мера в группе мер может иметь для одного элемента измерения. Возможные значения.<br /><br /> -   `ONE`<br />-   `MANY`|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Уникальное имя для измерения.|  
|`DIMENSION_CARDINALITY`|`DBTYPE_WSTR`||Количество экземпляров, которое элемент измерения может иметь для одного экземпляра меры групп мер.<br /><br /> Возможные значения.<br /><br /> -   `ONE`<br />-   `MANY`|  
|`DIMENSION_IS_VISIBLE`|`DBTYPE_BOOL`||Логическое значение, указывающее, видимы ли иерархии в измерении.<br /><br /> Возвращает значение `TRUE`, если одна или несколько иерархий в измерении видимы, в противном случае — значение `FALSE`.|  
|`DIMENSION_IS_FACT_DIMENSION`|`DBTYPE_BOOL`||Логическое значение, указывающее, является ли измерение измерением фактов.<br /><br /> Возвращает значение `TRUE`, если измерение является измерением фактов, в противном случае — значение `FALSE`.|  
|`DIMENSION_PATH`|`DBTYPE_HCHAPTER`||Список измерений для ссылочного измерения.|  
|`DIMENSION_GRANULARITY`|`DBTYPE_WSTR`||Уникальное имя иерархии гранулярности.|  
  
 Набор строк поддерживает сортировку по `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `MEASUREGROUP_NAME`, `DIMENSION_UNIQUE_NAME`.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `MDSCHEMA_MEASUREGROUP_DIMENSIONS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`DIMENSION_VISIBILITY`|`DBTYPE_UI2`|Битовая карта с одним из следующих допустимых значений (необязательно).<br /><br /> — Visible 1<br />-2 не отображается<br />-Ограничение по умолчанию имеет значение 1.|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы OLE DB для OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  