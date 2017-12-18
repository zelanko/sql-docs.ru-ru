---
title: "Обновление данных в мониторе репликации | Документация Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: refreshing data
ms.assetid: e9582244-7d00-45f4-be16-020a65c76a5e
caps.latest.revision: "17"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4d1a2cd6083e3c3243d1a4930499851fc74b491e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="refresh-data-in-replication-monitor"></a>Обновление данных в мониторе репликации
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В мониторе репликации главное окно и окна сведений (окна, запущенные из главного окна) можно обновлять автоматически или вручную. Чтобы обновить окно вручную, нажмите F5. По умолчанию главное окно обновляется автоматически каждые пять секунд. Частота обновления может быть установлена для каждого издателя.  
  
 Данные, отображаемые в мониторе репликации, запрашиваются из кэша. Сведения о связи между кэшем и обновлением монитора репликации см. в статье [Кэширование, обновление и производительность монитора репликации](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md). Сведения о запуске монитора репликации см. в [этой статье](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### <a name="to-set-refresh-options-for-replication-monitor"></a>Установка параметров обновления монитора репликации  
  
1.  Щелкните правой кнопкой мыши издатель в левой панели окна монитора репликации, затем щелкните **Настройки издателя**.  
  
2.  В диалоговом окне **Настройки издателя** установите параметры **Автоматическое обновление** и **Частота обновления** . Настройка **Автоматическое обновление** влияет на главное окно монитора репликации. Настройка **Частота обновления** также влияет на любое окно сведений, для которого включено автоматическое обновление (изменения настроек окна сведений вступят в силу только после последующего открытия окна).  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-specify-that-a-detail-window-should-automatically-refresh"></a>Установка автоматического обновления окна сведений  
  
1.  Откройте окно сведений в мониторе репликации. Например:  
  
    1.  Раскройте на левой панели группу издателей, раскройте издатель и выберите нужную публикацию.  
  
    2.  Перейдите на вкладку **Все подписки** .  
  
    3.  Щелкните правой кнопкой мыши подписку, а затем выберите **Просмотреть сведения**.  
  
2.  В окне сведений **Подписка \<имя_подписки>** щелкните **Действие**, а затем **Автоматическое обновление**. Частота обновления определяется настройкой **Частота обновления** в диалоговом окне **Настройки издателя** .  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за репликацией](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
