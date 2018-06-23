---
title: Удалите инструкции, изменяющие разрешения уровня столбцов на системные объекты | Документы Microsoft
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
- column-level permissions [SQL Server]
- removed statement permissions [SQL Server]
ms.assetid: 7f4fbbef-2696-4911-903b-63f6d9e4484a
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3bb611f4ccad6f6c5d89680857d4e96eabf79611
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102139"
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
  
  
