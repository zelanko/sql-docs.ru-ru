---
title: "Набор строк MDSCHEMA_MEASUREGROUPS | Документы Microsoft"
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
apiname: MDSCHEMA_MEASUREGROUPS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: MDSCHEMA_MEASUREGROUPS rowset
ms.assetid: bab1bbd0-421b-4fad-9aee-e6511e0e1f1b
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 736b43b50abe0bcff7aef25fd9791dcf27458e4e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="mdschemameasuregroups-rowset"></a>Набор строк MDSCHEMA_MEASUREGROUPS
  Описывает группы мер в базе данных.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **MDSCHEMA_MEASUREGROUPS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||Имя каталога, которому принадлежит группа мер. Имеет значение**NULL** , если поставщик не поддерживает каталоги.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||Не поддерживается.|  
|**CUBE_NAME**|**DBTYPE_WSTR**||Имя куба, которому принадлежит группа мер.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**||Имя группы мер.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Понятное описание элемента.|  
|**IS_WRITE_ENABLED**|**DBTYPE_BOOL**||Логическое значение, указывающее, доступна ли группа мер для записи.<br /><br /> Возвращает значение **true** , если группа мер доступна для записи.|  
|**MEASUREGROUP_CAPTION**|**DBTYPE_WSTR**||Отображаемый заголовок для группы мер.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **MDSCHEMA_MEASUREGROUPS** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**|Необязательно.|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы OLE DB для OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
