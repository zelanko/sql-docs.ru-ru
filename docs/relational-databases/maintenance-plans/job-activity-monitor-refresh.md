---
title: "Обновление монитора активности заданий | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: maintenance-plans
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.jobactivitymon.refresh.f1
ms.assetid: 413a368e-fd2b-4e1f-b370-002cdbc85bab
caps.latest.revision: "11"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cb9ae6930bdb4172b7a1a71e234e8367903983fc
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="job-activity-monitor-refresh"></a>Обновление монитора активности заданий
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Диалоговое окно **Настройки обновления** используется для настройки частоты, с которой монитор активности заданий получает новые сведения об активности сервера. Монитор активности заданий должен выполнять запросы на контролируемом сервере для получения данных для сетки монитора активности заданий. Если интервал автообновления составляет менее 30 секунд, время выполнения этих запросов может влиять на производительность сервера.  
  
 Для открытия данного диалогового окна выберите пункт **Просмотреть настройки обновления**в разделе **Состояние** монитора активности заданий.  
  
## <a name="options"></a>Параметры  
 **Автоматическое обновление каждые**  
 Выберите, чтобы включить автоматическое обновление сведений монитора активности. По умолчанию эта настройка отключена.  
  
 **секунд**  
 Количество секунд между попытками автообновления. Значение по умолчанию — 60 секунд. При установке значения 5 или менее обновление будет производиться каждые 5 секунд.  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за активностью заданий](http://msdn.microsoft.com/library/71cb432b-631d-4b8b-9965-e731b3d8266d)  
  
  
