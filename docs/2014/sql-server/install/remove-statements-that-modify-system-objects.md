---
title: Удалите инструкции, которые изменяют системные объекты | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- direct system catalog updates [SQL Server]
- system catalogs [SQL Server]
ms.assetid: 221b46c2-c27e-4df8-bd8c-8b990d6d5e98
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c722d1d40d206ab300b4b6c90fdf6648575c356b
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66093005"
---
# <a name="remove-statements-that-modify-system-objects"></a>Удаление инструкций, которые изменяют системные объекты
  Советник по переходу обнаружил инструкции, производящие обновление системного каталога. Непосредственное изменение системного каталога не допускается. Измените свои SQL-скрипты так, чтобы они использовали официальные документированные функции API-интерфейса.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Непосредственное изменение системного каталога не допускается. Любая попытка сделать это приведет к возникновению следующей ошибки.  
  
 `Server: Msg 259, Level 16, State 1, Line 1`  
  
 `Ad hoc updates to system catalogs are not allowed.`  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Измените свои SQL-скрипты так, чтобы они использовали официальные документированные функции API-интерфейса. Например, используйте инструкцию ALTER DATABASE *database_name* SET EMERGENCY вместо инструкции UPDATE в системной таблице **sysdatabases** .  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
