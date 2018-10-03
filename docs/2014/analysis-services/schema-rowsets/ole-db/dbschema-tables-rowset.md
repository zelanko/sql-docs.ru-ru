---
title: Набор строк DBSCHEMA_TABLES | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DBSCHEMA_TABLES
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_TABLES rowset
ms.assetid: 14c16e6b-0aff-4ad1-b98f-cdb7df0f8d73
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 66780a650e3187f3ec62831fd2badf331a1fca4d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48153164"
---
# <a name="dbschematables-rowset"></a>Набор строк DBSCHEMA_TABLES
  Показывает группы мер и измерения, представленные в виде таблиц в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DBSCHEMA_TABLES` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`TABLE_CATALOG`|`DBTYPE_WSTR`|255|Имя каталога, которому принадлежит этот объект.|  
|`TABLE_SCHEMA`|`DBTYPE_WSTR`|255|Имя куба, которому принадлежит этот объект.|  
|`TABLE_NAME`|`DBTYPE_WSTR`|255|Имя объекта, если `TABLE_TYPE` является `TABLE`.|  
|`TABLE_TYPE`|`DBTYPE_WSTR`||Тип таблицы.<br /><br /> `TABLE` Указывает, что объект является группой мер.<br /><br /> Параметр `SYSTEM TABLE` указывает, что объект является измерением.|  
|`TABLE_GUID`|`DBTYPE_GUID`||Не поддерживается.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Понятное описание объекта.|  
|`TABLE_PROPID`|`DBTYPE_UI4`||Не поддерживается.|  
|`DATE_CREATED`|`DBTYPE_DBTIMESTAMP`||Не поддерживается.|  
|`DATE_MODIFIED`|`DBTYPE_DBTIMESTAMP`||Дата последнего изменения объекта.|  
|`TABLE_OLAP_TYPE`|`DBTYPE_WSTR`||Тип OLAP объекта.<br /><br /> **MEASURE_GROUP** указывает, является объект группы мер.<br /><br /> Параметр `CUBE_DIMENSION` указывает, что объект является измерением.|  
  
 Набор строк отсортирован по `TABLE_TYPE`, `TABLE_CATALOG`, `TABLE_SCHEMA` и `TABLE_NAME`.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DBSCHEMA_TABLES` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`TABLE_CATALOG`|`DBTYPE_WSTR`|Необязательно|  
|`TABLE_SCHEMA`|`DBTYPE_WSTR`|Необязательно|  
|`TABLE_NAME`|`DBTYPE_WSTR`|Необязательно|  
|`TABLE_TYPE`|`DBTYPE_WSTR`|Необязательно|  
|`TABLE_OLAP_TYPE`|`DBTYPE_WSTR`|Необязательно|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы OLE DB](ole-db-schema-rowsets.md)  
  
  
