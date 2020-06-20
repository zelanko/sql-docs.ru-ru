---
title: Удалите инструкции, удаляющие системные объекты | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- drop system objects [SQL Server]
ms.assetid: cdfc3c50-c801-4039-a4bf-b35f876f1c61
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d9e8fbfd4a436e87cee413d95468ccf5dd36b9dd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059174"
---
# <a name="remove-statements-that-drop-system-objects"></a>Удалите инструкции, которые удаляют системные объекты
  Советник по переходу обнаружил инструкции, удаляющие системные объекты. Системные объекты, включая расширенные хранимые процедуры, развертываются в базе данных **resource** , доступной только для чтения (mssqlsystemresource), и не могут быть удалены. Измените свои приложения так, чтобы они отменяли или запрещали разрешение EXECUTE для системных объектов.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Такие инструкции, как DROP TABLE, DROP PROCEDURE и **sp_dropextendedproc** , не могут использоваться для удаления системных объектов, поскольку эти объекты развернуты в базе данных **resource** , доступной только для чтения.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Удалите из своих приложений все инструкции, которые пытаются удалить системные объекты. Измените свои приложения так, чтобы они отменяли или запрещали разрешение EXECUTE для системных объектов. В качестве альтернативы для отключения некоторых из этих объектов можно воспользоваться средством настройки контактной зоны (SAC). Например, с помощью средства SAC можно отключить или включить расширенную хранимую процедуру **xp_cmdshell** .  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
