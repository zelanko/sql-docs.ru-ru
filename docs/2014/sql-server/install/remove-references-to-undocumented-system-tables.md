---
title: Удалить ссылки на недокументированные системные таблицы | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- undocumented system tables [SQL Server]
- system tables [SQL Server]
ms.assetid: 010b1236-2219-4bf4-a6db-e3fc3abfa37a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 06249aa1849a1be9af40e183724e85b0f318f3dc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66093147"
---
# <a name="remove-references-to-undocumented-system-tables"></a>Удаление ссылки на недокументированные системные таблицы
  Многие системные таблицы, которые были недокументированными в предыдущих версиях, изменились или больше не существуют, поэтому использование таких таблиц может вызывать ошибки после обновления. Поскольку помощник по обновлению ищет ссылки на системные таблицы, он сообщит о ссылках на любые пользовательские таблицы, имена которых совпадают с именами системных таблиц.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Удалены следующие недокументированные системные таблицы.  
  
-   **spt_datatype_info**  
  
-   **spt_datatype_info_ext**  
  
-   **spt_provider_types**  
  
-   **spt_server_info**  
  
-   **spt_values**  
  
-   **sysfulltextnotify**  
  
-   **syslocks**  
  
-   **sysproperties**  
  
-   **sysprotects_aux**  
  
-   **sysprotects_view**  
  
-   **SYSREMOTE_CATALOGS**  
  
-   **SYSREMOTE_COLUMN_PRIVILEGES**  
  
-   **SYSREMOTE_COLUMNS**  
  
-   **SYSREMOTE_FOREIGN_KEYS**  
  
-   **SYSREMOTE_INDEXES**  
  
-   **SYSREMOTE_PRIMARY_KEYS**  
  
-   **SYSREMOTE_PROVIDER_TYPES**  
  
-   **SYSREMOTE_SCHEMATA**  
  
-   **SYSREMOTE_STATISTICS**  
  
-   **SYSREMOTE_TABLE_PRIVILEGES**  
  
-   **SYSREMOTE_TABLES**  
  
-   **SYSREMOTE_VIEWS**  
  
-   **syssegments**  
  
-   **sysxlogins**  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Измените приложения в соответствии со следующей таблицей.  
  
|Вместо|Использование|  
|----------------|---------|  
|**sysfulltextnotify**|Свойство**TableFulltextPendingChanges** функции OBJECTPROPERTYEX.|  
|**syslocks**|Динамическое административное представление**sys.dm_tran_locks** , хранимая процедура sp_lock или представление совместимости **sys.syslockinfo** .|  
|**sysproperties**|Представление каталога**sys.extended_properties** или функция **fn_listextendedproperty** .|  
|**sysxlogins**|Представление каталога**sys.server_principals** или представление совместимости **syslogins** .|  
|Все таблицы **spt_**|Замена отсутствует|  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
