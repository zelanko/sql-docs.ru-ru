---
title: "Указание типа подписки на публикацию слиянием и приоритета устранения конфликтов | Документация Майкрософт"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], merge subscription resolvers
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: c15a995e00c540422cafa3c9f00ca5de2cf63918
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="specify-a-merge-subscription-type-and-conflict-resolution-priority"></a>Указание типа подписки на публикацию слиянием и приоритета разрешения конфликтов
  Задание типа и приоритета разрешения конфликтов для подписки на публикацию слиянием осуществляется на странице **Тип подписки** мастера создания подписки. Дополнительные сведения об использовании этого мастера см. в разделе [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md) и [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
 Тип подписки после ее создания изменить нельзя, но приоритет для серверного типа подписки можно изменить в диалоговом окне **Свойства подписки — \<издатель>: \<база_данных_публикации>**. Дополнительные сведения о доступе к этому диалоговому окну см. в разделах [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md) и [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md).  
  
### <a name="to-specify-a-merge-subscription-type-and-conflict-resolution-priority"></a>Указание типа подписки на публикацию слиянием и приоритета разрешения конфликтов  
  
1.  На странице **Тип подписки** мастера создания подписки выберите **Клиент** или **Сервер** в качестве значения параметра **Тип подписки** .  
  
2.  Если выбран тип подписки **Сервер**, введите также значение (от 0.00 до 99.99) для параметра **Приоритет разрешения конфликтов** .  
  
### <a name="to-modify-the-conflict-resolution-priority"></a>Изменение приоритета разрешения конфликтов  
  
1.  В диалоговом окне **Свойства подписки — \<издатель>: \<база_данных_публикации>** в издателе введите значение (от 0,00 до 99,99) для параметра **Приоритет**.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
