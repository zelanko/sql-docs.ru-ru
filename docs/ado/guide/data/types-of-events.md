---
title: Типы событий | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- EventComplete event [ADO]
- events [ADO], types
- Will events [ADO]
- complete events [ADO]
- WillEvent event [ADO]
ms.assetid: f3327ea0-635a-43d4-bd78-c1674f62f1a2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c02d8d115a4336470c0e0d32aebabea63c05ab0b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67923818"
---
# <a name="types-of-events"></a>Типы событий
Существует два основных типа событий. «Будут события», которые вызываются перед началом операции, обычно включают в себя имя «будет», например **виллчанжерекордсет** или **виллконнект**. События, которые вызываются после завершения события, обычно содержат "Complete" в своих именах, например **рекордчанжекомплете** или **коннекткомплете**. Существуют исключения, такие как **InfoMessage** , но они происходят после завершения связанной операции.  
  
## <a name="will-events"></a>События будут  
 Обработчики событий, вызываемые перед началом операции, предлагают вам возможность проверить или изменить параметры операции, а затем отменить операцию или разрешить ее выполнение. Эти подпрограммы обработчика событий, как правило, имеют имена в виде <strong>*события*</strong>.  
  
## <a name="complete-events"></a>Завершение событий  
 Обработчики событий, вызванные после завершения операции, могут уведомлять приложение о завершении операции. Такой обработчик событий также уведомляется, когда обработчик событий будет отменять отложенную операцию. Эти подпрограммы обработчика событий обычно имеют имена <strong>завершенных *событий*</strong>формы.  
  
 События «будет» и «завершение» обычно используются парами.  
  
## <a name="other-events"></a>Другие события  
 Другие обработчики событий, т. е. события, имена которых не являются формами, вызывают <strong>*событие* </strong> или <strong> *событие*завершено</strong> . вызывается только после завершения операции. Эти события: **Disconnect**, **ендофрекордсет**и **InfoMessage**.  
  
## <a name="see-also"></a>См. также:  
 [Сводка по обработчику событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Создание экземпляра события ADO по языку](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [Параметры события](../../../ado/guide/data/event-parameters.md)   
 [Совместная работа обработчиков событий](../../../ado/guide/data/how-event-handlers-work-together.md)
