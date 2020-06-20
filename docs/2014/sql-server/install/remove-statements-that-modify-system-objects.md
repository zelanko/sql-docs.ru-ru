---
title: Удалите инструкции, изменяющие системные объекты | Документация Майкрософт
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
ms.openlocfilehash: 526181bc4bf7ab81df2eaa25f19e7627c9b7af10
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059155"
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
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](https://docs.microsoft.com/sql/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
