---
title: План обслуживания (управление соединениями) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: maintenance-plans
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.swb.maint.connections.f1
ms.assetid: 95ad9375-6584-423e-b9de-0e86782f8017
caps.latest.revision: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6f7a35cc6e39beb2e81b092d862b881e4922c491
ms.sourcegitcommit: 6e16d1616985d65484c72f5e0f34fb2973f828f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2018
---
# <a name="maintenance-plan-manage-connections"></a>План обслуживания (управление соединениями)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Используйте диалоговое окно **Управление соединениями** , чтобы задать свойства соединений, используемых планами обслуживания. При создании плана обслуживания устанавливается локальное соединение с сервером, на котором создается план. Используйте это соединение, чтобы создать задачи, работающие по данному локальному соединению. При необходимости используйте диалоговое окно **Управление соединениями** , чтобы добавить их. Как только дополнительные соединения будут настроены, они будут появляться в окне соединений для каждой задачи.  
  
## <a name="options"></a>Параметры  
 **Server**  
 Экземпляр сервера.  
  
 **Проверка подлинности**  
 Указывает, используется ли при соединении проверка подлинности Windows или проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  

> [!IMPORTANT]  
> Пакет хранится в базе данных **msdb** с параметром **ProtectionLevel**, равным **ServerStorage**, поэтому при использовании *проверки подлинности SQL Server* пароль не шифруется в **msdb**. Вы можете использовать *проверку подлинности SQL Server*, если база данных **msdb** защищена, но рекомендуется применять *проверку подлинности Windows*.

## <a name="see-also"></a>См. также:  
 [Планы обслуживания](../../relational-databases/maintenance-plans/maintenance-plans.md)  
  
  
