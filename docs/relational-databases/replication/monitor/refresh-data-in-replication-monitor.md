---
title: Обновление данных в мониторе репликации | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- refreshing data
ms.assetid: e9582244-7d00-45f4-be16-020a65c76a5e
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 53a4f467d5229033e5dcefbe9c31b903c51a3ec3
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37355036"
---
# <a name="refresh-data-in-replication-monitor"></a>Обновление данных в мониторе репликации
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В мониторе репликации главное окно и окна сведений (окна, запущенные из главного окна) могут быть обновлены автоматически или вручную. Чтобы обновить окно вручную, нажмите F5. По умолчанию главное окно обновляется автоматически каждые пять секунд. Частота обновления может быть установлена для каждого издателя.  
  
 Данные, отображаемые в мониторе репликации, запрашиваются из кэша. Сведения о связи между кэшем и обновлением монитора репликации см. в статье [Кэширование, обновление и производительность монитора репликации](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md). Сведения о запуске монитора репликации см. в [этой статье](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### <a name="to-set-refresh-options-for-replication-monitor"></a>Установка параметров обновления монитора репликации  
  
1.  Щелкните правой кнопкой мыши издатель в левой панели окна монитора репликации, затем щелкните **Настройки издателя**.  
  
2.  В диалоговом окне **Настройки издателя** установите параметры **Автоматическое обновление** и **Частота обновления** . Настройка **Автоматическое обновление** влияет на главное окно монитора репликации. Настройка **Частота обновления** также влияет на любое окно сведений, для которого включено автоматическое обновление (изменения настроек окна сведений вступят в силу только после последующего открытия окна).  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-specify-that-a-detail-window-should-automatically-refresh"></a>Установка автоматического обновления окна сведений  
  
1.  Откройте окно сведений в мониторе репликации. Пример:  
  
    1.  Раскройте на левой панели группу издателей, раскройте издатель и выберите нужную публикацию.  
  
    2.  Перейдите на вкладку **Все подписки** .  
  
    3.  Щелкните правой кнопкой мыши подписку, а затем выберите **Просмотреть сведения**.  
  
2.  В окне сведений **Подписка \<имя_подписки>** щелкните **Действие**, а затем **Автоматическое обновление**. Частота обновления определяется настройкой **Частота обновления** в диалоговом окне **Настройки издателя** .  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за репликацией](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
