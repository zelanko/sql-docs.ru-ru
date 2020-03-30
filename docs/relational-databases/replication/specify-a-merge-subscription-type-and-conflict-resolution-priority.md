---
title: Указание типа и приоритета разрешения конфликтов (слияние)
description: Узнайте, как указать тип и политику разрешения конфликтов, используемую подпиской на публикацию слиянием для SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], merge subscription resolvers
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a988935a1d0a614f1b7b336cc95ed82ce2a36214
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "75321741"
---
# <a name="specify-a-merge-subscription-type-and-conflict-resolution-priority"></a>Указание типа подписки на публикацию слиянием и приоритета разрешения конфликтов
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Задание типа и приоритета разрешения конфликтов для подписки на публикацию слиянием осуществляется на странице **Тип подписки** мастера создания подписки. Дополнительные сведения об использовании этого мастера см. в разделе [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md) и [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
 Тип подписки после ее создания изменить нельзя, но приоритет для серверного типа подписки можно изменить в диалоговом окне **Свойства подписки — \<издатель>: \<база_данных_публикации>** . Дополнительные сведения о доступе к этому диалоговому окну см. в разделах [Просмотр и изменение свойств принудительной подписки](../../relational-databases/replication/view-and-modify-push-subscription-properties.md) и [Просмотр и изменение свойств подписки по запросу](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md).  
  
### <a name="to-specify-a-merge-subscription-type-and-conflict-resolution-priority"></a>Указание типа подписки на публикацию слиянием и приоритета разрешения конфликтов  
  
1.  На странице **Тип подписки** мастера создания подписки выберите **Клиент** или **Сервер** в качестве значения параметра **Тип подписки** .  
  
2.  Если выбран тип подписки **Сервер**, введите также значение (от 0.00 до 99.99) для параметра **Приоритет разрешения конфликтов** .  
  
### <a name="to-modify-the-conflict-resolution-priority"></a>Изменение приоритета разрешения конфликтов  
  
1.  В диалоговом окне **Свойства подписки — \<издатель>: \<база_данных_публикации>** в издателе введите значение (от 0,00 до 99,99) для параметра **Приоритет**.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
