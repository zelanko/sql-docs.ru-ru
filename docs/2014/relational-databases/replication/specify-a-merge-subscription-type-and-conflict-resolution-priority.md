---
title: Укажите тип подписки слиянием и приоритета разрешения конфликтов (среда SQL Server Management Studio) | Документы Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], merge subscription resolvers
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
caps.latest.revision: 33
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: de41a4bf6075a816b751574b5505e324d07aa89f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102405"
---
# <a name="specify-a-merge-subscription-type-and-conflict-resolution-priority-sql-server-management-studio"></a>Указание типа подписки на публикацию слиянием и приоритета устранения конфликтов (среда SQL Server Management Studio)
  Задание типа и приоритета разрешения конфликтов для подписки на публикацию слиянием осуществляется на странице **Тип подписки** мастера создания подписки. Дополнительные сведения об использовании этого мастера см. в разделе [Create a Pull Subscription](create-a-pull-subscription.md) и [Create a Push Subscription](create-a-push-subscription.md).  
  
 Тип подписки после ее создания изменить нельзя, но приоритет для серверного типа подписки можно изменить в диалоговом окне **Свойства подписки — \<издатель>: \<база_данных_публикации>**. Дополнительные сведения о доступе к этому диалоговому окну см. в разделах [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) и [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).  
  
### <a name="to-specify-a-merge-subscription-type-and-conflict-resolution-priority"></a>Указание типа подписки на публикацию слиянием и приоритета разрешения конфликтов  
  
1.  На странице **Тип подписки** мастера создания подписки выберите **Клиент** или **Сервер** в качестве значения параметра **Тип подписки** .  
  
2.  Если выбран тип подписки **Сервер**, введите также значение (от 0.00 до 99.99) для параметра **Приоритет разрешения конфликтов** .  
  
### <a name="to-modify-the-conflict-resolution-priority"></a>Изменение приоритета разрешения конфликтов  
  
1.  В диалоговом окне **Свойства подписки — \<издатель>: \<база_данных_публикации>** в издателе введите значение (от 0,00 до 99,99) для параметра **Приоритет**.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Подписка на публикации](subscribe-to-publications.md)  
  
  