---
description: Событие InfoMessage (ADO)
title: Событие InfoMessage (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection::InfoMessage
- InfoMessage
helpviewer_keywords:
- InfoMessage event [ADO]
ms.assetid: 468c87dd-e3bc-4084-9941-94d10743d4e9
author: rothja
ms.author: jroth
ms.openlocfilehash: d3957c6cf6843ba27c54fb5a979901bd4a656c2e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443456"
---
# <a name="infomessage-event-ado"></a>Событие InfoMessage (ADO)
Событие **InfoMessage** вызывается при возникновении предупреждения во время операции **коннектионевент** .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
InfoMessage pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *pError*  
 Объект [ошибки](../../../ado/reference/ado-api/error-object.md) . Этот параметр содержит все возвращенные ошибки. Если возвращается несколько ошибок, перечислите коллекцию **Errors** , чтобы найти их.  
  
 *адстатус*  
 Значение состояния [евентстатусенум](../../../ado/reference/ado-api/eventstatusenum.md) . При возникновении предупреждения *адстатус* имеет значение **Адстатусок** , а *perror* содержит предупреждение.  
  
 Перед возвратом этого события задайте для этого параметра значение **адстатусунвантедевент** , чтобы предотвратить появление последующих уведомлений.  
  
 *пконнектион*  
 Объект [соединения](../../../ado/reference/ado-api/connection-object-ado.md) . Соединение, для которого возникло предупреждение. Например, предупреждения могут возникать при открытии объекта **соединения** или при выполнении [команды](../../../ado/reference/ado-api/command-object-ado.md) для **соединения**.  
  
## <a name="see-also"></a>См. также:  
 [Пример модели событий ADO (Visual c++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Сводка по обработчику событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
