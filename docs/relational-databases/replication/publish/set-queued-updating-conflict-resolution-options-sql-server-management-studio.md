---
title: "настроить параметры разрешения конфликтов обновления посредством очередей (среда SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "разрешение конфликтов [репликация SQL Server], обновляемые посредством очередей подписки"
  - "обновляемые посредством очередей подписки [репликация SQL Server]"
ms.assetid: bb6b6c71-42c7-421a-a0fa-d5594d27e35d
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# настроить параметры разрешения конфликтов обновления посредством очередей (среда SQL Server Management Studio)
  Установить параметры разрешения для публикаций, которые поддерживают обновляемые подписки на конфликтов **Параметры подписки** Страница **Свойства публикации — \< публикация>** диалоговое окно. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### Установка параметров разрешения конфликтов обновления посредством очередей  
  
1.  На **Параметры подписки** Страница **Свойства публикации — \< публикация>** выберите одно из следующих значений для **политики разрешения конфликтов** параметр:  
  
    -   **Сохранить изменение издателя**  
  
    -   **Сохранить изменение подписчика**  
  
    -   **Повторно инициализировать подписку**  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## См. также:  
 [Включение обновляемых подписок для публикаций транзакций](../../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)   
 [Обнаружение и разрешение конфликтов обновлений посредством очередей](../../../relational-databases/replication/transactional/queued-updating-conflict-detection-and-resolution.md)  
  
  