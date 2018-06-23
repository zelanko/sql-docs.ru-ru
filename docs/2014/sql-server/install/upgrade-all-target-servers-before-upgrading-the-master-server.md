---
title: Обновите все целевые серверы перед обновлением главного сервера | Документы Microsoft
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
- TSX [SQL Server Agent]
- target servers [SQL Server Agent]
- MSX [SQL Server Agent]
- master servers [SQL Server Agent]
ms.assetid: 2c231793-3878-4a5e-a425-1fa0d787ba84
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fdd218b1d5bfaacaffbd50c50d55dd47d613d207
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188954"
---
# <a name="upgrade-all-target-servers-before-upgrading-the-master-server"></a>Обновите все целевые серверы перед обновлением главного сервера
  Перед обновлением главного сервера обновите все компьютеры, на которых работают серверы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , настроенные в качестве целевых серверов.  
  
## <a name="component"></a>Компонент  
 Агент[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]   
  
## <a name="description"></a>Описание  
 Чтобы автоматизировать администрирование многосерверной среды, необходимо иметь по меньшей мере один главный сервер и один целевой. Главный сервер распределяет задания целевым серверам и получает от них события. На главном сервере также хранится центральная копия определений заданий, выполняющихся на целевых серверах.  
  
 Если текущий сервер настроен как главный, необходимо сначала обновить все целевые серверы, а затем главный сервер.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Если нельзя обновить все целевые серверы до обновления главного сервера, то следует исключить все целевые серверы и после обновления прикрепить их повторно.  
  
 Дополнительные сведения об определении выполняемых задач см. в разделах «Автоматизация администрирования в масштабах предприятия», «Как отключить целевой сервер от главного сервера» и «Как прикрепить целевой сервер к главному серверу» в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления агента SQL Server](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)   
 [Проблемы обновления агента SQL Server](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  