---
title: План обслуживания (серверы) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.maintplanproperties.server.f1
- sql12.swb.maint.servers.f1
ms.assetid: ac24d1a8-dd2f-4162-b804-c0df1fc1e61d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 989b2992407c4a3825d42106d848598a723a41c5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63187236"
---
# <a name="maintenance-plan-servers"></a>План обслуживания (серверы)
  Диалоговое окно **Серверы** используется для выбора серверов, для которых нужно запустить план обслуживания.  
  
 Многосерверную среду, содержащую один главный сервер и один или несколько целевых серверов, необходимо настроить для создания многосерверного плана обслуживания. В многосерверных планах обслуживания локальный сервер настраивается, как и главный сервер. В многосерверной среде это диалоговое окно отображает главный **(локальный)** сервер и все соответствующие целевые серверы. Для локального сервера создается одно задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Оно включается или отключается в зависимости от текущего выбора **(локального)** сервера. Если выбраны целевые серверы, то создается многосерверное задание, которое загружается на выделенные целевые серверы. Если не выбран ни один целевой сервер, многосерверное задание удаляется.  
  
## <a name="see-also"></a>См. также  
 [Планы обслуживания](maintenance-plans.md)   
 [Создание многосерверной среды](../../ssms/agent/create-a-multiserver-environment.md)   
 [Создание главного сервера](../../ssms/agent/make-a-master-server.md)   
 [Создание целевого сервера](../../ssms/agent/make-a-target-server.md)  
  
  
