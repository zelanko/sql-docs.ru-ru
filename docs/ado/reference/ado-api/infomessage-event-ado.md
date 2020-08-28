---
description: Событие InfoMessage (ADO)
title: Событие InfoMessage (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 8695dc364a649dff204fcd689ab4722f19e125b9
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990805"
---
# <a name="infomessage-event-ado"></a>Событие InfoMessage (ADO)
Событие **InfoMessage** вызывается при возникновении предупреждения во время операции **коннектионевент** .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
InfoMessage pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *pError*  
 Объект [ошибки](./error-object.md) . Этот параметр содержит все возвращенные ошибки. Если возвращается несколько ошибок, перечислите коллекцию **Errors** , чтобы найти их.  
  
 *адстатус*  
 Значение состояния [евентстатусенум](./eventstatusenum.md) . При возникновении предупреждения *адстатус* имеет значение **Адстатусок** , а *perror* содержит предупреждение.  
  
 Перед возвратом этого события задайте для этого параметра значение **адстатусунвантедевент** , чтобы предотвратить появление последующих уведомлений.  
  
 *пконнектион*  
 Объект [соединения](./connection-object-ado.md) . Соединение, для которого возникло предупреждение. Например, предупреждения могут возникать при открытии объекта **соединения** или при выполнении [команды](./command-object-ado.md) для **соединения**.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (Visual c++)](./ado-events-model-example-vc.md)   
 [Сводка по обработчику событий ADO](../../guide/data/ado-event-handler-summary.md)   
 [Объект Connection (ADO)](./connection-object-ado.md)