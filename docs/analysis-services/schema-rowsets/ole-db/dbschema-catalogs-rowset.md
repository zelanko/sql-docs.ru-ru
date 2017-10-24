---
title: "Набор строк DBSCHEMA_CATALOGS | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DBSCHEMA_CATALOGS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DBSCHEMA_CATALOGS rowset
ms.assetid: f02dc75d-5442-4eea-b33a-567dc816be7a
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0632d90765112ee54de8e78a66fdefa1ff27334f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="dbschemacatalogs-rowset"></a>Набор строк DBSCHEMA_CATALOGS
  Определяет физические атрибуты, связанные с каталогами, доступными из системы управления базами данных (СУБД).  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DBSCHEMA_CATALOGS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|255|Имя каталога. Не может иметь значение null.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Понятное описание таблицы.|  
|**РОЛИ**|**DBTYPE_WSTR**||Разделенный запятыми список ролей, к которым относится текущий пользователь.<br /><br /> Символ звездочки (\*) включается как роль, если текущий пользователь является сервера или администратор базы данных.<br /><br /> **Username** присоединяется к **ROLES** , если одна из ролей использует динамическую безопасность.|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**||Дата последнего изменения каталога.|  
  
 Набор строк отсортирован по полю **CATALOG_NAME**.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DBSCHEMA_CATALOGS** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Необязательно|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы OLE DB](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  

