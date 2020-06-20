---
title: Обновляемые подписки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.updatablesubscriptions.f1
ms.assetid: 8e9a13a0-6b24-47c6-9d83-3cbaf08f673d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 812cbf22d8013b0f52f889d1e34039d688e411aa
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047604"
---
# <a name="updatable-subscriptions"></a>Обновляемые подписки
  В случае репликации транзакций реплицированные данные следует рассматривать как находящиеся в режиме только для чтения; однако изменить реплицированные данные в подписчике [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно с помощью обновляемых подписок. Если нужно изменить данные на подписчике, выберите один из следующих параметров в зависимости от потребностей.  
  
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
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [Subscribe to Publications](subscribe-to-publications.md)   
 [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
