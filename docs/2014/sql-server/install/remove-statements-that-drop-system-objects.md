---
title: Удалите инструкции, удаляющие системные объекты | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- drop system objects [SQL Server]
ms.assetid: cdfc3c50-c801-4039-a4bf-b35f876f1c61
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 68e5000e924c438a4611e2fa8c134f0dd822f930
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63294492"
---
# <a name="remove-statements-that-drop-system-objects"></a>Удалите инструкции, которые удаляют системные объекты
  Советник по переходу обнаружил инструкции, удаляющие системные объекты. Системные объекты, включая расширенные хранимые процедуры, развертываются в базе данных **resource** , доступной только для чтения (mssqlsystemresource), и не могут быть удалены. Измените свои приложения так, чтобы они отменяли или запрещали разрешение EXECUTE для системных объектов.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Такие инструкции, как DROP TABLE, DROP PROCEDURE и **sp_dropextendedproc** , не могут использоваться для удаления системных объектов, поскольку эти объекты развернуты в базе данных **resource** , доступной только для чтения.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Удалите из своих приложений все инструкции, которые пытаются удалить системные объекты. Измените свои приложения так, чтобы они отменяли или запрещали разрешение EXECUTE для системных объектов. В качестве альтернативы для отключения некоторых из этих объектов можно воспользоваться средством настройки контактной зоны (SAC). Например, с помощью средства SAC можно отключить или включить расширенную хранимую процедуру **xp_cmdshell** .  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
