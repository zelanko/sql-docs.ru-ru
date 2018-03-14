---
title: "Обновляемые подписки | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newsubwizard.updatablesubscriptions.f1
ms.assetid: 8e9a13a0-6b24-47c6-9d83-3cbaf08f673d
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dc633405859f9f84735f3229994ae49e10ba5a6b
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="updatable-subscriptions"></a>Обновляемые подписки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В случае репликации транзакций реплицированные данные следует рассматривать как находящиеся в режиме только для чтения; однако изменить реплицированные данные на подписчике [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно при помощи обновляемых подписок. Если нужно изменить данные на подписчике, выберите один из следующих параметров в зависимости от потребностей.  
  
|Тип обновляемой подписки|Требования|  
|---------------------------------|------------------|  
|Немедленное обновление|Чтобы обновить данные на сервере подписчика, между издателем и подписчиком должно быть установлено подключение.|  
|Обновление посредством очереди|Чтобы обновить данные на сервере подписчика, установка подключения между издателем и подписчиком необязательна. Обновления можно осуществить в режиме «вне сети», а затем синхронизировать их между издателем и подписчиком.|  
  
## <a name="options"></a>Параметры  
 **Репликация изменений подписчика**  
 Установите флажок в столбце **Репликация** для каждого подписчика, который должен иметь возможность осуществлять обновления. Для подписчиков, которые могут осуществлять обновления, выберите соответствующий параметр из раскрывающегося списка в столбце **Зафиксировать на стороне издателя** :  
  
-   Выберите **Одновременно фиксировать изменения** для немедленного обновления подписки;  
  
-   Выберите **Ставить изменения в очередь и фиксировать при первой возможности** для подписки, обновляемой посредством очередей.  
  
## <a name="see-also"></a>См. также:  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Subscribe to Publications](../../relational-databases/replication/subscribe-to-publications.md)   
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
