---
title: Проверка структур плана после обновления | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-plan-guides
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- plan guides [SQL Server], validating after upgrade
ms.assetid: a55ebd88-6f58-454d-b1c4-991b88add522
caps.latest.revision: 6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4e434a536a8012adfb3384a78344044adc64499a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="validate-plan-guides-after-upgrade"></a>Проверка структур плана после обновления
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Рекомендуется переоценить и протестировать определения структур планов при обновлении приложения для работы с новым выпуском [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Требования к настройке производительности и поведение сопоставления структур планов могут меняться. Хотя недопустимая структура плана не приведет к сбою при выполнении запроса, план будет скомпилирован без использования структуры, что не рекомендуется. После обновления базы данных до версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]рекомендуется выполнить следующие действия.  
  
-   Проверьте существующие структуры планов с помощью функции [sys.fn_validate_plan_guide](../../relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql.md) .  
  
-   Используйте расширенные события, чтобы проверить наличие планов без структуры за определенное время с помощью события [Plan Guide Unsuccessful](../../relational-databases/event-classes/plan-guide-unsuccessful-event-class.md) .  
  
  
