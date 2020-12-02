---
description: План обслуживания (управление соединениями)
title: План обслуживания (управление соединениями) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql13.swb.maint.connections.f1
ms.assetid: 95ad9375-6584-423e-b9de-0e86782f8017
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ce9ac0469125a6077799e5bab0a69cdc1d06d82b
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "88420838"
---
# <a name="maintenance-plan-manage-connections"></a>План обслуживания (управление соединениями)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
   Используйте диалоговое окно **Управление соединениями**, чтобы задать свойства соединений, используемых планами обслуживания. При создании плана обслуживания устанавливается локальное соединение с сервером, на котором создается план. Используйте это соединение, чтобы создать задачи, работающие по данному локальному соединению. При необходимости используйте диалоговое окно **Управление соединениями** , чтобы добавить их. Как только дополнительные соединения будут настроены, они будут появляться в окне соединений для каждой задачи.  
  
## <a name="options"></a>Параметры  
 **Server**  
 Экземпляр сервера.  
  
 **Аутентификация**  
 Указывает, используется ли при соединении проверка подлинности Windows или проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  

> [!IMPORTANT]  
> Пакет хранится в базе данных **msdb** с параметром **ProtectionLevel**, равным **ServerStorage**, поэтому при использовании *проверки подлинности SQL Server* пароль не шифруется в **msdb**. Вы можете использовать *проверку подлинности SQL Server*, если база данных **msdb** защищена, но рекомендуется применять *проверку подлинности Windows*.

## <a name="see-also"></a>См. также:  
 [Планы обслуживания](../../relational-databases/maintenance-plans/maintenance-plans.md)  
  
  
