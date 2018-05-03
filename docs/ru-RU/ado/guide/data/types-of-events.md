---
title: Типы событий | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- EventComplete event [ADO]
- events [ADO], types
- Will events [ADO]
- complete events [ADO]
- WillEvent event [ADO]
ms.assetid: f3327ea0-635a-43d4-bd78-c1674f62f1a2
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d2fc67ba61f703e80926425405da90641b9cda64
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="types-of-events"></a>Типы событий
Существует два основных типа событий. «Будет события,» называемые до начала операции, обычно их названия содержат «Будет» — например, **WillChangeRecordset** или **WillConnect**. События, которые вызываются после выполнения события, обычно их названия содержат «Завершено», например, **RecordChangeComplete** или **ConnectComplete**. Существуют исключения, таких как **InfoMessage** —, но это происходит после завершения связанной операции.  
  
## <a name="will-events"></a>Будет события  
 Обработчики событий вызывается перед началом операции обеспечивают возможность проверить или изменить параметры операции и отменить операцию или разрешить его завершения. Эти процедуры обработчика событий, обычно имеют имена вида **будет*событий ***.  
  
## <a name="complete-events"></a>События завершения  
 Обработчики событий, вызывается после завершения операции может уведомить приложение, которое завершает операцию. Такой обработчик событий также уведомления, когда обработчик событий будет отменяет операцию в очереди. Эти процедуры обработчика событий, обычно имеют имена вида ***событий * завершить**.  
  
 Будет и завершения события обычно используются в парах.  
  
## <a name="other-events"></a>Другие события  
 Обработчики событий — то есть события, имена которых не являются формы **будет * событий*** или ***событий * завершить** — вызываются только после завершения операции. Эти события являются **Disconnect**, **EndOfRecordset**, и **InfoMessage**.  
  
## <a name="see-also"></a>См. также  
 [Сводка обработчик событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Создание экземпляра события ADO по языку](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [Параметры события](../../../ado/guide/data/event-parameters.md)   
 [Совместная работа обработчиков событий](../../../ado/guide/data/how-event-handlers-work-together.md)
