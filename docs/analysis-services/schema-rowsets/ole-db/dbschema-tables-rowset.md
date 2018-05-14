---
title: Набор строк DBSCHEMA_TABLES | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 06fc718e4d4bde23bfee4240e89d77bcde3bbf50
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="dbschematables-rowset"></a>Набор строк DBSCHEMA_TABLES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет группы мер и измерения, представленные в виде таблиц в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **DBSCHEMA_TABLES** набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
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
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы OLE DB](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  
