---
title: Набор строк MDSCHEMA_MEASUREGROUPS | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: df2bfe8aecc32c8f046d18fff4e72cd15409fdc8
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34029045"
---
# <a name="mdschemameasuregroups-rowset"></a>Набор строк MDSCHEMA_MEASUREGROUPS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Описывает группы мер в базе данных.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **MDSCHEMA_MEASUREGROUPS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
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
  
## <a name="see-also"></a>См. также  
 [OLE DB для OLAP наборы строк схемы](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
