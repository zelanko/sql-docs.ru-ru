---
title: Получение сведений об уведомлениях о событиях | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 9786faaf44724b1a2452bd5304b63deb2c9ea54e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63015316"
---
# <a name="get-information-about-event-notifications"></a>Получение сведений об уведомлениях о событиях
  Следующие представления каталога доступны для запроса метаданных об уведомлениях о событиях.  
  
 **Получение сведений об уведомлениях о событиях несерверного уровня**  
  
-   [sys.event_notifications (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-event-notifications-transact-sql)  
  
> [!NOTE]  
>  Для просмотра метаданных любого уведомления о событии в **sys.event_notifications** созданных на базе уровне, как минимум должны быть следующие компоненты: Элемент УПРАВЛЕНИЯ, ALTER, TAKE OWNERSHIP или VIEW DEFINITION для базы данных, быть владельцем уведомления о событии или иметь разрешение ALTER ANY DATABASE EVENT NOTIFICATION. Для уведомлений о событиях, созданных в определенной очереди по меньшей мере необходимо иметь следующее: Элемент УПРАВЛЕНИЯ, ALTER, TAKE OWNERSHIP или VIEW DEFINITION на объект, быть владельцем уведомления о событии или иметь разрешение ALTER ANY DATABASE EVENT NOTIFICATION.  
  
 **Получение сведений об уведомлениях о событиях серверного уровня**  
  
-   [sys.server_event_notifications (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql)  
  
> [!NOTE]  
>  Как минимум необходимо иметь следующее: Элемент УПРАВЛЕНИЯ или просмотр ЛЮБОГО определения разрешений на сервере, быть именем входа или владельцем уведомления о событии или иметь разрешение ALTER ANY EVENT NOTIFICATION для просмотра метаданных любого уведомления о событии в **sys.server_event_notifications**.  
  
 **Получение сведений обо всех событиях, которые могут создать уведомления**  
  
-   [sys.event_notification_event_types (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-event-notification-event-types-transact-sql)  
  
> [!NOTE]  
>  Это представление каталога не возвращает группы событий.  
  
## <a name="see-also"></a>См. также  
 [Уведомления о событиях](event-notifications.md)  
  
  
