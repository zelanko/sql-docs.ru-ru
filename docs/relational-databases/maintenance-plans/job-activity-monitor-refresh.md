---
title: Обновление монитора активности заданий | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: maintenance-plans
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.jobactivitymon.refresh.f1
ms.assetid: 413a368e-fd2b-4e1f-b370-002cdbc85bab
caps.latest.revision: 11
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 52160a10a8b404588103f36c90a103f9067530ba
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40405239"
---
# <a name="job-activity-monitor-refresh"></a>Обновление монитора активности заданий
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Диалоговое окно **Настройки обновления** используется для настройки частоты получения монитором активности заданий новых данных об активности сервера. Монитор активности заданий должен выполнять запросы на контролируемом сервере для получения данных для сетки монитора активности заданий. Если интервал автообновления составляет менее 30 секунд, время выполнения этих запросов может влиять на производительность сервера.  
  
 Для открытия данного диалогового окна выберите пункт **Просмотреть настройки обновления**в разделе **Состояние** монитора активности заданий.  
  
## <a name="options"></a>Параметры  
 **Автоматическое обновление каждые**  
 Выберите, чтобы включить автоматическое обновление сведений монитора активности. По умолчанию эта настройка отключена.  
  
 **секунд**  
 Количество секунд между попытками автообновления. Значение по умолчанию — 60 секунд. При установке значения 5 или менее обновление будет производиться каждые 5 секунд.  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за активностью заданий](../../ssms/agent/monitor-job-activity.md)  
  
  
