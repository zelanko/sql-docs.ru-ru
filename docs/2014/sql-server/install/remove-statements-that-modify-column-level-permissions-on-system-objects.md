---
title: Удалите инструкции, изменяющие разрешения уровня столбцов на системные объекты | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- column-level permissions [SQL Server]
- removed statement permissions [SQL Server]
ms.assetid: 7f4fbbef-2696-4911-903b-63f6d9e4484a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: dfc0bf1d77322bca3a95ec5d0ed49ab856ce9cf9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48125274"
---
# <a name="remove-statements-that-modify-column-level-permissions-on-system-objects"></a>Удаление инструкций, которые изменяют разрешения уровня столбца в системных объектах
  Помощник по обновлению обнаружил нестандартные разрешения уровня столбцов на системные объекты. Эти изменения разрешений не поддерживаются при обновлении. Кроме того, разрешения уровня столбцов на системные объекты больше не поддерживаются. Удалите из своих приложений инструкции, задающие разрешения уровня столбца в системных объектах.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Удалите из своих приложений инструкции, которые предоставляют, запрещают или отменяют разрешения уровня столбца для системных объектов.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
