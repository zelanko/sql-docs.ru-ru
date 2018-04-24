---
title: Инициализация подписки| Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.rep.newsubwizard.initializesubscriptions.f1
ms.assetid: 7b170e4e-470d-4828-a9ed-7435b0b03514
caps.latest.revision: 24
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c688ea2bd6345d6e57425e5d99d3068838d237bd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="initialize-subscriptions"></a>Инициализировать подписки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Необходимо инициализировать подписчиков, прежде чем они смогут начать прием реплицируемых данных. Начальный набор данных не требуется, но подписчик должен, по крайней мере, обладать схемой для каждого реплицируемого объекта и всеми таблицами метаданных и процедурами, необходимыми для репликации.  
  
## <a name="options"></a>Параметры  
 **Свойства подписки**  
 Установите флажок в столбце **Инициализировать** для каждого подписчика, требующего наличия начального набора данных. Если флажок не установлен, будут инициализированы только метаданные и процедуры репликации. Дополнительные сведения об инициализации подписки без моментального снимка см. в статье [Инициализация подписки на публикацию транзакций без моментального снимка](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
 Выберите пункт **Немедленно** из раскрывающегося списка в столбце **Инициализировать, когда** , чтобы агент слияния или агент распространителя передал файлы моментальных снимков на подписчик по завершении работы мастера. Выберите пункт **При первой синхронизации** , чтобы агент переслал файлы при следующем запланированном запуске. Параметр **Немедленно** недоступен для подписок по запросу на [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. Агент слияния и агент распространителя не работают на экземплярах выпуска [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], поэтому подписка должна быть инициализирована при помощи другого метода.  
  
> [!NOTE]  
>  Мастер может запросить соединение с распространителем, чтобы запустить соответствующее задание для агента распространителя или агента слияния.  
  
## <a name="see-also"></a>См. также:  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Инициализация подписки](../../relational-databases/replication/initialize-a-subscription.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
