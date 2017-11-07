---
title: "Набор строк DBSCHEMA_TABLES | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DBSCHEMA_TABLES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DBSCHEMA_TABLES rowset
ms.assetid: 14c16e6b-0aff-4ad1-b98f-cdb7df0f8d73
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1bc193f33395521c62e1b5e998c2098721313d9b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="dbschematables-rowset"></a>Набор строк DBSCHEMA_TABLES
  Определяет группы мер и измерения, представленные в виде таблиц в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **DBSCHEMA_TABLES** набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
|-----------------|--------------------|------------|-----------------|  
|**ЗНАЧЕНИЯМ TABLE_CATALOG**|**DBTYPE_WSTR**|255|Имя каталога, которому принадлежит этот объект.|  
|**TABLE_SCHEMA**|**DBTYPE_WSTR**|255|Имя куба, которому принадлежит этот объект.|  
|**ИМЯ_ТАБЛИЦЫ**|**DBTYPE_WSTR**|255|Имя объекта, если **TABLE_TYPE** — **таблицы**.|  
|**TABLE_TYPE**|**DBTYPE_WSTR**||Тип таблицы.<br /><br /> **Таблица** указывает объект группы мер.<br /><br /> **СИСТЕМНАЯ таблица** указывает объект является измерением.|  
|**TABLE_GUID**|**DBTYPE_GUID**||Не поддерживается.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Понятное описание объекта.|  
|**TABLE_PROPID**|**DBTYPE_UI4**||Не поддерживается.|  
|**DATE_CREATED**|**DBTYPE_DBTIMESTAMP**||Не поддерживается.|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**||Дата последнего изменения объекта.|  
|**TABLE_OLAP_TYPE**|**DBTYPE_WSTR**||Тип OLAP объекта.<br /><br /> **MEASURE_GROUP** указывает объект группы мер.<br /><br /> **CUBE_DIMENSION** указанный объект является измерением.|  
  
 Набор строк отсортирован по **TABLE_TYPE**, **значениям TABLE_CATALOG**, **TABLE_SCHEMA**, и **TABLE_NAME**.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 **DBSCHEMA_TABLES** строк может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**ЗНАЧЕНИЯМ TABLE_CATALOG**|**DBTYPE_WSTR**|Необязательно|  
|**TABLE_SCHEMA**|**DBTYPE_WSTR**|Необязательно|  
|**ИМЯ_ТАБЛИЦЫ**|**DBTYPE_WSTR**|Необязательно|  
|**TABLE_TYPE**|**DBTYPE_WSTR**|Необязательно|  
|**TABLE_OLAP_TYPE**|**DBTYPE_WSTR**|Необязательно|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы OLE DB](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  

