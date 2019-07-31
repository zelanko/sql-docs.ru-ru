---
title: Получение сведений об уведомлениях о событиях | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- event notifications [SQL Server], metadata
- status information [SQL Server], event notifications
- metadata [SQL Server], event notifications
ms.assetid: 8bc10867-66d6-4f57-ac32-a6c29f3327cd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fefdced57d611d241dbb96b71a0b220139683243
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68083834"
---
# <a name="get-information-about-event-notifications"></a>Получение сведений об уведомлениях о событиях
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Следующие представления каталога доступны для запроса метаданных об уведомлениях о событиях.  
  
 **Получение сведений об уведомлениях о событиях несерверного уровня**  
  
-   [sys.event_notifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-event-notifications-transact-sql.md)  
  
> [!NOTE]  
>  Чтобы просмотреть метаданные любого уведомления о событии, созданном на уровне базы данных, в представлении каталога **sys.event_notifications**, требуется следующее: иметь разрешения CONTROL, ALTER, TAKE OWNERSHIP или VIEW DEFINITION на базу данных, быть владельцем уведомления о событии или иметь разрешение ALTER ANY DATABASE EVENT NOTIFICATION. Чтобы просмотреть метаданные уведомлений о событиях, созданных в конкретной очереди, требуется следующее: иметь разрешения CONTROL, ALTER, TAKE OWNERSHIP или VIEW DEFINITION на объект, быть владельцем уведомления о событии или иметь разрешение ALTER ANY DATABASE EVENT NOTIFICATION.  
  
 **Получение сведений об уведомлениях о событиях серверного уровня**  
  
-   [sys.server_event_notifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql.md)  
  
> [!NOTE]  
>  Требуется следующее: иметь разрешения CONTROL или VIEW ANY DEFINITION на сервер, быть именем входа или владельцем уведомления о событии или иметь разрешение ALTER ANY EVENT NOTIFICATION для просмотра метаданных любого уведомления о событии в представлении каталога **sys.server_event_notifications**.  
  
 **Получение сведений обо всех событиях, которые могут создать уведомления**  
  
-   [sys.event_notification_event_types (Transact-SQL)](../../relational-databases/system-catalog-views/sys-event-notification-event-types-transact-sql.md)  
  
> [!NOTE]  
>  Это представление каталога не возвращает группы событий.  
  
## <a name="see-also"></a>См. также:  
 [Уведомления о событиях](../../relational-databases/service-broker/event-notifications.md)  
  
  
