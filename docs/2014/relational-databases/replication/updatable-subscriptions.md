---
title: Обновляемые подписки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rep.newsubwizard.updatablesubscriptions.f1
ms.assetid: 8e9a13a0-6b24-47c6-9d83-3cbaf08f673d
caps.latest.revision: 21
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 17b561938c9d1d8852e59db7078bfca5e9f298ab
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097931"
---
# <a name="updatable-subscriptions"></a>Обновляемые подписки
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
  
## <a name="see-also"></a>См. также  
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [Subscribe to Publications](subscribe-to-publications.md)   
 [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  