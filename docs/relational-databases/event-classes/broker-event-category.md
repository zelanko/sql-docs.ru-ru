---
description: Категория событий Broker
title: Категория событий Broker | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- SQL Server event classes, Broker event category
- Broker event category [SQL Server]
- event classes [SQL Server], Broker event category
ms.assetid: 470dc93c-0dda-4d89-829b-937738d59b31
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ab93bbb94022f25206154e94531754315ef21c34
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456030"
---
# <a name="broker-event-category"></a>Категория событий Broker

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

 Категория событий **Broker** содержит общие события компонента Service Broker.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Класс событий Broker:Activation](../../relational-databases/event-classes/broker-activation-event-class.md)|Событие, формируемое при запуске монитором очереди хранимой процедуры активации.|  
|[Класс событий Broker:Connection](../../relational-databases/event-classes/broker-connection-event-class.md)|Событие, формируемое для передачи данных о состоянии транспортного соединения, которым управляет компонент Service Broker.|  
|[Класс событий Broker:Conversation](../../relational-databases/event-classes/broker-conversation-event-class.md)|Событие, формируемое для передачи данных о ходе диалога.|  
|[Класс событий Broker:Conversation Group](../../relational-databases/event-classes/broker-conversation-group-event-class.md)|Событие, формируемое, когда база данных создает или удаляет группу сообщений.|  
|[Класс событий Broker:Corrupted Message](../../relational-databases/event-classes/broker-corrupted-message-event-class.md)|Событие, формируемое для уведомления о получении базой данных поврежденного сообщения.|  
|[Класс событий Broker:Forwarded Message Dropped](../../relational-databases/event-classes/broker-forwarded-message-dropped-event-class.md)|Событие, формируемое в том случае, если SQL Server удаляет сообщение компонента Service Broker, которое было переслано.|  
|[Класс событий Broker:Forwarded Message Sent](../../relational-databases/event-classes/broker-forwarded-message-sent-event-class.md)|Событие, формируемое в том случае, если SQL Server пересылает сообщение компоненту Service Broker.|  
|[Класс событий Broker:Message Classify](../../relational-databases/event-classes/broker-message-classify-event-class.md)|Событие, формируемое при определении компонентом Service Broker маршрута сообщения.|  
|[Класс событий Broker: Message Drop](../../relational-databases/event-classes/broker-message-drop-event-class.md)|Событие, формируемое в том случае, если компонент Service Broker не может сохранить сообщение, которое должно быть доставлено службе в данном экземпляре.|  
|[Класс событий Broker:Remote Message Ack](../../relational-databases/event-classes/broker-remote-message-ack-event-class.md)|Событие, формируемое при получении или отправке компонентом Service Broker подтверждения сообщения.|  
  
 Также компонент Service Broker поддерживает два события аудита безопасности. Дополнительные сведения об этих событиях см. в статьях [Класс событий Audit Broker Login](../../relational-databases/event-classes/audit-broker-login-event-class.md) и [Класс событий Audit Broker Conversation](../../relational-databases/event-classes/audit-broker-conversation-event-class.md).  
  
## <a name="see-also"></a>См. также  
 [Категория событий «Аудит безопасности»](https://docs.microsoft.com/analysis-services/trace-events/security-audit-event-category)  
  
  
