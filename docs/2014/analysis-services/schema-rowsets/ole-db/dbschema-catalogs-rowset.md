---
title: Набор строк DBSCHEMA_CATALOGS | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DBSCHEMA_CATALOGS
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_CATALOGS rowset
ms.assetid: f02dc75d-5442-4eea-b33a-567dc816be7a
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: df3b146d3e1015fd4a78254be0d8a7a6083991d8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087948"
---
# <a name="dbschemacatalogs-rowset"></a>Набор строк DBSCHEMA_CATALOGS
  Определяет физические атрибуты, связанные с каталогами, доступными из системы управления базами данных (СУБД).  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DBSCHEMA_CATALOGS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|255|Имя каталога. Не может иметь значение null.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Понятное описание таблицы.|  
|`ROLES`|`DBTYPE_WSTR`||Разделенный запятыми список ролей, к которым относится текущий пользователь.<br /><br /> Символ звездочки (\*) включается как роль, если текущий пользователь является сервера или администратор базы данных.<br /><br /> `Username` присоединяется к `ROLES`, если одна из ролей использует динамическую безопасность.|  
|`DATE_MODIFIED`|`DBTYPE_DBTIMESTAMP`||Дата последнего изменения каталога.|  
  
 Набор строк отсортирован по полю `CATALOG_NAME`.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DBSCHEMA_CATALOGS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Необязательно|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы OLE DB](ole-db-schema-rowsets.md)  
  
  