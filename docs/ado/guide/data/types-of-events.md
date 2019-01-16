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
manager: craigg
ms.openlocfilehash: 78505f010706a39e5278d50219dd4504e33dd67c
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2019
ms.locfileid: "54254869"
---
# <a name="types-of-events"></a>Типы событий
Существует два основных типа событий. «Будет события,» которые вызываются до начала операции, обычно включают «Будет» в именах - например, **события WillChangeRecordset** или **WillConnect**. События, которые вызываются после события обычно включают «Complete» в именах -, например, **RecordChangeComplete** или **ConnectComplete**. Существуют исключения — например **InfoMessage** -, но это происходит после завершения связанной операции.  
  
## <a name="will-events"></a>Будет события  
 Обработчики событий вызывается перед началом операции обеспечивают возможность проверить или изменить параметры операции, а затем отменить операцию или ее завершения. Эти подпрограммы обработчика событий обычно имеют имена вида <strong>будет*событий*</strong>.  
  
## <a name="complete-events"></a>События завершения  
 Обработчики событий, вызывается после завершения операции можно уведомления приложения о завершил операцию. Такой обработчик событий также получает уведомления, когда обработчик событий будет отменяющий ожидающую операцию. Эти подпрограммы обработчика событий обычно имеют имена вида  <strong>*событий*завершить</strong>.  
  
 Будет и события завершения обычно используются в парах.  
  
## <a name="other-events"></a>Другие события  
 Обработчики событий — то есть события, имена которых не представлены в формате <strong>будет*событий*</strong>  или  <strong>*событий*завершить</strong> -вызван только после Операция не завершится. Эти события являются **Disconnect**, **EndOfRecordset**, и **InfoMessage**.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Создание экземпляра события ADO по языку](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [Параметры события](../../../ado/guide/data/event-parameters.md)   
 [Совместная работа обработчиков событий](../../../ado/guide/data/how-event-handlers-work-together.md)
