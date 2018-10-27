---
title: Категория событий Broker | Документация Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Broker event category
- Broker event category [SQL Server]
- event classes [SQL Server], Broker event category
ms.assetid: 470dc93c-0dda-4d89-829b-937738d59b31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 602113da86b3d8ffdc79484b35dab59749844a01
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2018
ms.locfileid: "50145649"
---
# <a name="broker-event-category"></a>Категория событий Broker
  Категория событий **Broker** содержит общие события компонента Service Broker.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Класс событий Broker:Activation](broker-activation-event-class.md)|Событие, формируемое при запуске монитором очереди хранимой процедуры активации.|  
|[Класс событий Broker:Connection](broker-connection-event-class.md)|Событие, формируемое для передачи данных о состоянии транспортного соединения, которым управляет компонент Service Broker.|  
|[Класс событий Broker:Conversation](broker-conversation-event-class.md)|Событие, формируемое для передачи данных о ходе диалога.|  
|[Класс событий Broker:Conversation Group](broker-conversation-group-event-class.md)|Событие, формируемое, когда база данных создает или удаляет группу сообщений.|  
|[Класс событий Broker:Corrupted Message](broker-corrupted-message-event-class.md)|Событие, формируемое для уведомления о получении базой данных поврежденного сообщения.|  
|[Класс событий Broker:Forwarded Message Dropped](broker-forwarded-message-dropped-event-class.md)|Событие, формируемое в том случае, если SQL Server удаляет сообщение компонента Service Broker, которое было переслано.|  
|[Класс событий Broker:Forwarded Message Sent](broker-forwarded-message-sent-event-class.md)|Событие, формируемое в том случае, если SQL Server пересылает сообщение компоненту Service Broker.|  
|[Класс событий Broker:Message Classify](broker-message-classify-event-class.md)|Событие, формируемое при определении компонентом Service Broker маршрута сообщения.|  
|[Класс событий Broker: Message Drop](broker-message-drop-event-class.md)|Событие, формируемое в том случае, если компонент Service Broker не может сохранить сообщение, которое должно быть доставлено службе в данном экземпляре.|  
|[Класс событий Broker:Remote Message Ack](broker-remote-message-ack-event-class.md)|Событие, формируемое при получении или отправке компонентом Service Broker подтверждения сообщения.|  
  
 Также компонент Service Broker поддерживает два события аудита безопасности. Дополнительные сведения об этих событиях см. в статьях [Класс событий Audit Broker Login](audit-broker-login-event-class.md) и [Класс событий Audit Broker Conversation](audit-broker-conversation-event-class.md).  
  
## <a name="see-also"></a>См. также  
 [Категория событий «Аудит безопасности»](https://docs.microsoft.com/bi-reference/trace-events/security-audit-event-category)  
  
  
