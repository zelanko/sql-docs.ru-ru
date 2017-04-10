---
title: "Указание типа подписки на публикацию слиянием и приоритета устранения конфликтов (среда SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "разрешение конфликтов при репликации слиянием [репликация SQL Server], сопоставители подписок на публикацию слиянием"
  - "разрешение конфликтов [репликация SQL Server], репликация слиянием"
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Указание типа подписки на публикацию слиянием и приоритета устранения конфликтов (среда SQL Server Management Studio)
  Задание типа и приоритета разрешения конфликтов для подписки на публикацию слиянием осуществляется на странице **Тип подписки** мастера создания подписки. Дополнительные сведения об использовании этого мастера см. в разделе [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md) и [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
 Тип подписки нельзя изменить после создания подписки, но можно изменить приоритет для серверного типа подписки в **Свойства подписки — \< издатель>: \< база данных публикации>** диалоговое окно. Дополнительные сведения о доступе к этому диалоговому окну см. в разделах [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md) и [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md).  
  
### Указание типа подписки на публикацию слиянием и приоритета разрешения конфликтов  
  
1.  На странице **Тип подписки** мастера создания подписки выберите **Клиент** или **Сервер** в качестве значения параметра **Тип подписки** .  
  
2.  Если выбран тип подписки **сервера**, также введите значение (от 0.00 до 99.99) для **Приоритет разрешения конфликтов** параметр.  
  
### Изменение приоритета разрешения конфликтов  
  
1.  В **Свойства подписки — \< издатель>: \< база данных публикации>** на издателе, введите значение (от 0.00 до 99.99) для **приоритет** параметр.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## См. также:  
 [Расширенное обнаружение и разрешение конфликтов репликации слиянием](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  
  
  