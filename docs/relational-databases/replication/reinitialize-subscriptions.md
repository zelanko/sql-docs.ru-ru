---
title: Повторная инициализация подписки| Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
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
helpviewer_keywords:
- initializing subscriptions [SQL Server replication], reinitializing
- subscriptions [SQL Server replication], reinitializing
- reinitializing subscriptions
ms.assetid: fb13712b-e7ad-4f1f-b605-4554bad0cb60
caps.latest.revision: 51
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a6d014dbd60d449d559049c61dbf429e97e06938
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="reinitialize-subscriptions"></a>Повторная инициализация подписок
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Повторная инициализация подписки влечет за собой применение нового моментального снимка одной или нескольких статей к одному или нескольким подписчикам: репликация транзакций и репликация моментальных снимков позволяют повторно инициализировать отдельные статьи; репликация слиянием требует, чтобы повторно были инициализированы все статьи. Узлы в одноранговой топологии репликации транзакций не могут быть инициализированы повторно. Если нужно убедиться в том, что узел имеет новую копию данных, восстановите резервную копию на этом узле. Повторная инициализация выполняется по одной из двух причин.  
  
-   Подписка явно помечена для повторной инициализации.  
  
-   Выполняется действие, например изменение свойств, требующее повторной инициализации. Дополнительные сведения о действиях, после которых нужно выполнять повторную инициализацию, см. в статье [Изменение свойств публикации и статьи](../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
 В обоих случаях последний моментальный снимок применяется к подписчику при следующем запуске агента слияния или агента распространителя. При репликации транзакций и репликации слиянием, когда происходит повторная инициализация, любые изменения, внесенные на подписчике, но еще не синхронизированные с издателем, переопределяются посредством применения нового моментального снимка.  
  
 Для репликации слиянием можно выбрать передачу всех изменений данных с подписчика до применения моментального снимка. Любые отложенные изменения схемы с издателя применяются на подписчике, а затем любые обновления, сделанные на подписчике с момента последней синхронизации, распространяются на издатель до повторного применения моментального снимка. Это поведение управляется свойствами **upload_first** и **automatic_reinitialization_policy** . Дополнительные сведения см. в разделе [Reinitialize a Subscription](../../relational-databases/replication/reinitialize-a-subscription.md). Если пометить подписку для повторной инициализации с помощью среды SQL Server Management Studio или монитора репликации, в диалоговом окне **Повторная инициализация подписок** можно будет указать, что необходимо сначала передать изменения.  
  
> [!IMPORTANT]  
>  Если добавить, удалить или изменить параметризованный фильтр в публикации слиянием, ожидающие обработки изменения на подписчике невозможно будет передать на издатель во время повторной инициализации. Если нужно передать изменения, ожидающие обработки, то перед изменением фильтра необходимо синхронизировать все подписки.  
  
 Если при создании подписки к подписчику исходный моментальный снимок не применялся, а затем подписка была помечена для повторной инициализации, то моментальный снимок неприменим. Дополнительные сведения см. в статье [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
 **Повторная инициализация подписки**  
  
 Чтобы повторно инициализировать все статьи в подписке, используйте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], хранимые процедуры или объекты RMO. Чтобы повторно инициализировать отдельные статьи в моментальном снимке и в публикациях транзакций, следует использовать хранимые процедуры. Дополнительные сведения см. в статье [Reinitialize a Subscription](../../relational-databases/replication/reinitialize-a-subscription.md).  
  
## <a name="see-also"></a>См. также:  
 [Инициализация подписки](../../relational-databases/replication/initialize-a-subscription.md)   
 [Окончание срока действия и отключение подписки](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  
