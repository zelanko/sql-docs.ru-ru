---
title: Удалите инструкции, изменяющие разрешения уровня столбца на системные объекты | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- column-level permissions [SQL Server]
- removed statement permissions [SQL Server]
ms.assetid: 7f4fbbef-2696-4911-903b-63f6d9e4484a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b377ac0b9baacdab6461a0e62174538902939bd8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66093032"
---
# <a name="remove-statements-that-modify-column-level-permissions-on-system-objects"></a>Удаление инструкций, которые изменяют разрешения уровня столбца в системных объектах
  Помощник по обновлению обнаружил нестандартные разрешения уровня столбцов на системные объекты. Эти изменения разрешений не поддерживаются при обновлении. Кроме того, разрешения уровня столбцов на системные объекты больше не поддерживаются. Удалите из своих приложений инструкции, задающие разрешения уровня столбца в системных объектах.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Удалите из своих приложений инструкции, которые предоставляют, запрещают или отменяют разрешения уровня столбца для системных объектов.  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
