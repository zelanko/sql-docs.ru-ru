---
title: "План обслуживания (серверы) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: maintenance-plans
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.maint.servers.f1
- sql13.swb.maint.maintplanproperties.server.f1
ms.assetid: ac24d1a8-dd2f-4162-b804-c0df1fc1e61d
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cb602533a9ce853c59daa501a84dbae206127c40
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="maintenance-plan-servers"></a>План обслуживания (серверы)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Диалоговое окно **Серверы** используется для выбора серверов, для которых нужно запустить план обслуживания.  
  
 Многосерверную среду, содержащую один главный сервер и один или несколько целевых серверов, необходимо настроить для создания многосерверного плана обслуживания. В многосерверных планах обслуживания локальный сервер настраивается, как и главный сервер. В многосерверной среде это диалоговое окно отображает главный **(локальный)** сервер и все соответствующие целевые серверы. Для локального сервера создается одно задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Оно включается или отключается в зависимости от текущего выбора **(локального)** сервера. Если выбраны целевые серверы, то создается многосерверное задание, которое загружается на выделенные целевые серверы. Если не выбран ни один целевой сервер, многосерверное задание удаляется.  
  
## <a name="see-also"></a>См. также:  
 [Планы обслуживания](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Создание многосерверной среды](http://msdn.microsoft.com/library/edc2b60d-15da-40a1-8ba3-f1d473366ee6)   
 [Создание главного сервера](http://msdn.microsoft.com/library/05739a73-1fdf-4d9d-92a6-70f328380322)   
 [Создание целевого сервера](http://msdn.microsoft.com/library/13aabe2d-67fe-4c67-8d49-2928dd705b7a)  
  
  
