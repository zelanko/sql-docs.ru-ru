---
title: Удалите ссылки на недокументированные системные таблицы | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- undocumented system tables [SQL Server]
- system tables [SQL Server]
ms.assetid: 010b1236-2219-4bf4-a6db-e3fc3abfa37a
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cd8ff349ae3e065233ea104d34016a919b9fd6e7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193508"
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
  
|Вместо|Использовать|  
|----------------|---------|  
|**sysfulltextnotify**|Свойство**TableFulltextPendingChanges** функции OBJECTPROPERTYEX.|  
|**syslocks**|Динамическое административное представление**sys.dm_tran_locks** , хранимая процедура sp_lock или представление совместимости **sys.syslockinfo** .|  
|**sysproperties**|Представление каталога**sys.extended_properties** или функция **fn_listextendedproperty** .|  
|**sysxlogins**|Представление каталога**sys.server_principals** или представление совместимости **syslogins** .|  
|Все таблицы **spt_**|Замена отсутствует|  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
