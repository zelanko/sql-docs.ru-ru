---
title: Тип подписки | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.subscriptiontype.f1
ms.assetid: 9a50f588-ee45-4a87-826f-372ff0798587
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 473c3ebc9347f5898e043a04a975e4fe497b0fc9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48091441"
---
# <a name="subscription-type"></a>Тип подписки
  Репликация слиянием реализует два типа подписки: серверную и клиентскую (в предыдущих версиях [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] им соответствуют глобальная и локальная, соответственно). Подписчики с серверной подпиской могут:  
  
-   повторно публиковать данные для других подписчиков;  
  
-   служить альтернативным участником синхронизации;  
  
-   разрешать конфликты в соответствии с установленным приоритетом.  
  
 Большинству подписчиков не требуются такие функциональные возможности, и они могут использовать клиентскую подписку. Клиентские подписки также позволяют отслеживать и решать конфликты, однако подписчикам не назначается приоритет: первый подписчик, подавший изменение издателю, выигрывает любой конфликт, который может возникнуть из-за внесения данного изменения.  
  
> [!NOTE]  
>  Тип подписки нельзя изменить после ее создания.  
  
## <a name="options"></a>Параметры  
 **Свойства подписки**  
 Выберите **Клиентская** или **Серверная** из раскрывающегося списка в столбце **Тип подписки** для каждого подписчика. Для подписчиков с серверными подписками введите число между 0 и 99,99 в столбце **Приоритет устранения конфликтов** (чем выше число, тем выше приоритет подписчика).  
  
## <a name="see-also"></a>См. также  
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [Подписка на публикации](subscribe-to-publications.md)  
  
  
