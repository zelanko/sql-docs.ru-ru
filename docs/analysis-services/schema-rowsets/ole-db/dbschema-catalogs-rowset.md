---
title: Набор строк DBSCHEMA_CATALOGS | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 61e4de1591752919a5916d6044591bda49b14992
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="dbschemacatalogs-rowset"></a>Набор строк DBSCHEMA_CATALOGS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет физические атрибуты, связанные с каталогами, доступными из системы управления базами данных (СУБД).  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DBSCHEMA_CATALOGS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
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
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы OLE DB](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  
