---
title: Получение сведений об уведомлениях о событиях | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-notifications
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- event notifications [SQL Server], metadata
- status information [SQL Server], event notifications
- metadata [SQL Server], event notifications
ms.assetid: 8bc10867-66d6-4f57-ac32-a6c29f3327cd
caps.latest.revision: 21
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 38a04ea335975a19aa969f53581424130eb14012
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101041"
---
# <a name="get-information-about-event-notifications"></a>Получение сведений об уведомлениях о событиях
  Следующие представления каталога доступны для запроса метаданных об уведомлениях о событиях.  
  
 **Получение сведений об уведомлениях о событиях несерверного уровня**  
  
-   [sys.event_notifications (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-event-notifications-transact-sql)  
  
> [!NOTE]  
>  Необходимые минимальные требования для просмотра метаданных о любом уведомлении в **sys.event_notifications** , созданном на уровне базы данных: иметь разрешение CONTROL, ALTER, TAKE OWNERSHIP или VIEW DEFINITION для базы данных, быть владельцем уведомления о событии или иметь разрешение ALTER ANY DATABASE EVENT NOTIFICATION. Необходимые минимальные требования для уведомлений о событиях, созданных в определенной очереди: иметь разрешение CONTROL, ALTER, TAKE OWNERSHIP или VIEW DEFINITION для объекта, быть владельцем уведомления о событии или иметь разрешение ALTER ANY DATABASE EVENT NOTIFICATION.  
  
 **Получение сведений об уведомлениях о событиях серверного уровня**  
  
-   [sys.server_event_notifications (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql)  
  
> [!NOTE]  
>  Необходимые минимальные требования для просмотра метаданных любого уведомления о событии в представлении каталога **sys.server_event_notifications**: иметь разрешение CONTROL или VIEW ANY DEFINITION для сервера, быть именем входа или владельцем уведомления о событии или иметь разрешение ALTER ANY EVENT NOTIFICATION.  
  
 **Получение сведений обо всех событиях, которые могут создать уведомления**  
  
-   [sys.event_notification_event_types (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-event-notification-event-types-transact-sql)  
  
> [!NOTE]  
>  Это представление каталога не возвращает группы событий.  
  
## <a name="see-also"></a>См. также  
 [Уведомления о событиях](event-notifications.md)  
  
  
