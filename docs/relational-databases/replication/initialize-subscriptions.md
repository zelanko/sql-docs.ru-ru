---
title: "Инициализация подписки| Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newsubwizard.initializesubscriptions.f1
ms.assetid: 7b170e4e-470d-4828-a9ed-7435b0b03514
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1dd4015c8247802bb86973673f4942e2f9cb270a
ms.lasthandoff: 04/11/2017

---
# <a name="initialize-subscriptions"></a>Инициализировать подписки
  Необходимо инициализировать подписчиков, прежде чем они смогут начать прием реплицируемых данных. Начальный набор данных не требуется, но подписчик должен, по крайней мере, обладать схемой для каждого реплицируемого объекта и всеми таблицами метаданных и процедурами, необходимыми для репликации.  
  
## <a name="options"></a>Параметры  
 **Свойства подписки**  
 Установите флажок в столбце **Инициализировать** для каждого подписчика, требующего наличия начального набора данных. Если флажок не установлен, будут инициализированы только метаданные и процедуры репликации. Дополнительные сведения об инициализации подписки без моментального снимка см. в статье [Инициализация подписки на публикацию транзакций без моментального снимка](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
 Выберите пункт **Немедленно** из раскрывающегося списка в столбце **Инициализировать, когда** , чтобы агент слияния или агент распространителя передал файлы моментальных снимков на подписчик по завершении работы мастера. Выберите пункт **При первой синхронизации** , чтобы агент переслал файлы при следующем запланированном запуске. Параметр **Немедленно** недоступен для подписок по запросу на [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. Агент слияния и агент распространителя не работают на экземплярах выпуска [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], поэтому подписка должна быть инициализирована при помощи другого метода.  
  
> [!NOTE]  
>  Мастер может запросить соединение с распространителем, чтобы запустить соответствующее задание для агента распространителя или агента слияния.  
  
## <a name="see-also"></a>См. также:  
 [Создание подписки по запросу](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Инициализация подписки](../../relational-databases/replication/initialize-a-subscription.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
