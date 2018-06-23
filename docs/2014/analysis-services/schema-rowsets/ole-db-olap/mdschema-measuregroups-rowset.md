---
title: Набор строк MDSCHEMA_MEASUREGROUPS | Документы Microsoft
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
- MDSCHEMA_MEASUREGROUPS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_MEASUREGROUPS rowset
ms.assetid: bab1bbd0-421b-4fad-9aee-e6511e0e1f1b
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 046674dc7c579a99e3d9fd90a86c466001c270c0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101164"
---
# <a name="mdschemameasuregroups-rowset"></a>Набор строк MDSCHEMA_MEASUREGROUPS
  Описывает группы мер в базе данных.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `MDSCHEMA_MEASUREGROUPS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Имя каталога, которому принадлежит группа мер. Имеет значение `NULL`, если поставщик не поддерживает каталоги.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Не поддерживается.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Имя куба, которому принадлежит группа мер.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`||Имя группы мер.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Понятное описание элемента.|  
|`IS_WRITE_ENABLED`|`DBTYPE_BOOL`||Логическое значение, указывающее, доступна ли группа мер для записи.<br /><br /> Возвращает значение `true`, если группа мер доступна для записи.|  
|`MEASUREGROUP_CAPTION`|`DBTYPE_WSTR`||Отображаемый заголовок для группы мер.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `MDSCHEMA_MEASUREGROUPS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы OLE DB для OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  