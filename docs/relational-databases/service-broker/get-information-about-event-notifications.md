---
title: "Получение сведений об уведомлениях о событиях | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "уведомления о событиях [SQL Server], метаданные"
  - "сведения о состоянии [SQL Server], уведомления о событиях"
  - "метаданные [SQL Server], уведомления о событиях"
ms.assetid: 8bc10867-66d6-4f57-ac32-a6c29f3327cd
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Получение сведений об уведомлениях о событиях
  Следующие представления каталога доступны для запроса метаданных об уведомлениях о событиях.  
  
 **Получение сведений об уведомлениях о событиях несерверного уровня**  
  
-   [sys.event_notifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-event-notifications-transact-sql.md)  
  
> [!NOTE]  
>  Необходимые минимальные требования для просмотра метаданных о любом уведомлении в **sys.event_notifications**, созданном на уровне базы данных: иметь разрешение CONTROL, ALTER, TAKE OWNERSHIP или VIEW DEFINITION для базы данных, быть владельцем уведомления о событии или иметь разрешение ALTER ANY DATABASE EVENT NOTIFICATION. Необходимые минимальные требования для уведомлений о событиях, созданных в определенной очереди: иметь разрешение CONTROL, ALTER, TAKE OWNERSHIP или VIEW DEFINITION для объекта, быть владельцем уведомления о событии или иметь разрешение ALTER ANY DATABASE EVENT NOTIFICATION.  
  
 **Получение сведений об уведомлениях о событиях серверного уровня**  
  
-   [sys.server_event_notifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql.md)  
  
> [!NOTE]  
>  Необходимые минимальные требования для просмотра метаданных любого уведомления о событии в представлении каталога **sys.server_event_notifications**: иметь разрешение CONTROL или VIEW ANY DEFINITION для сервера, быть именем входа или владельцем уведомления о событии или иметь разрешение ALTER ANY EVENT NOTIFICATION.  
  
 **Получение сведений обо всех событиях, которые могут создать уведомления**  
  
-   [sys.event_notification_event_types (Transact-SQL)](../../relational-databases/system-catalog-views/sys-event-notification-event-types-transact-sql.md)  
  
> [!NOTE]  
>  Это представление каталога не возвращает группы событий.  
  
## См. также:  
 [Уведомления о событиях](../../relational-databases/service-broker/event-notifications.md)  
  
  