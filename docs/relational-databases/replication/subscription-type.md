---
title: Тип подписки | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.subscriptiontype.f1
ms.assetid: 9a50f588-ee45-4a87-826f-372ff0798587
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 679dc415500bd1cbf3731ecf7f2bd47d3b577f38
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "76287059"
---
# <a name="subscription-type"></a>Тип подписки
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Репликация слиянием реализует два типа подписки: серверную и клиентскую (в предыдущих версиях [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] им соответствуют глобальная и локальная подписки). Подписчики с серверной подпиской могут:  
  
-   повторно публиковать данные для других подписчиков;  
  
-   служить альтернативным участником синхронизации;  
  
-   разрешать конфликты в соответствии с установленным приоритетом.  
  
 Большинству подписчиков не требуются такие функциональные возможности, и они могут использовать клиентскую подписку. Клиентские подписки также позволяют отслеживать и решать конфликты, однако подписчикам не назначается приоритет: первый подписчик, подавший изменение издателю, выигрывает любой конфликт, который может возникнуть из-за внесения данного изменения.  
  
> [!NOTE]  
>  Тип подписки нельзя изменить после ее создания.  
  
## <a name="options"></a>Параметры  
 **Свойства подписки**  
 Выберите **Клиентская** или **Серверная** из раскрывающегося списка в столбце **Тип подписки** для каждого подписчика. Для подписчиков с серверными подписками введите число между 0 и 99,99 в столбце **Приоритет устранения конфликтов** (чем выше число, тем выше приоритет подписчика).  
  
## <a name="see-also"></a>См. также:  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
