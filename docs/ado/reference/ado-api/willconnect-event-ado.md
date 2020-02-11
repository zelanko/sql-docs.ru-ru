---
title: Событие Виллконнект (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- WillConnect
- Connection::WillConnect
helpviewer_keywords:
- WillConnect event [ADO]
ms.assetid: da561d58-eb58-446c-a4fd-1838c76073c0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9fc1ac74e7e3d521bae587957f5f95771e5a5268
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67945851"
---
# <a name="willconnect-event-ado"></a>Событие WillConnect (ADO)
Событие **виллконнект** вызывается до начала соединения.  
  
 Область **применения:** [объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WillConnect ConnectionString, UserID, Password, Options, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *ConnectionString*  
 **Строка** , содержащая сведения о соединении для ожидающего подключения.  
  
 *UserID*  
 **Строка** , содержащая имя пользователя для ожидающего подключения.  
  
 *Пароль*  
 **Строка** , содержащая пароль для ожидающего подключения.  
  
 *Параметры*  
 Значение **типа Long** , указывающее, как поставщик должен оценивать *ConnectionString*. Единственный вариант — **адасинкопен**.  
  
 *адстатус*  
 Значение состояния [евентстатусенум](../../../ado/reference/ado-api/eventstatusenum.md) .  
  
 При вызове этого события этот параметр по умолчанию имеет значение **адстатусок** . Он имеет значение **адстатускантдени** , если событие не может запрашивать отмену ожидающей операции.  
  
 Перед возвратом этого события задайте для этого параметра значение **адстатусунвантедевент** , чтобы предотвратить появление последующих уведомлений. Задайте для этого параметра значение **адстатусканцел** , чтобы запросить операцию подключения, которая привела к отмене этого уведомления.  
  
 *пконнектион*  
 Объект [соединения](../../../ado/reference/ado-api/connection-object-ado.md) , к которому относится данное уведомление о событии. Изменения параметров **соединения** обработчиком событий **виллконнект** не будут влиять на **соединение**.  
  
## <a name="remarks"></a>Remarks  
 При вызове **виллконнект** параметры *ConnectionString*, *UserID*, *Password*и *Options* устанавливаются в значения, установленные операцией, вызвавшей это событие (ожидающее подключение), и могут быть изменены перед возвратом события. **Виллконнект** может возвращать запрос на отмену ожидающего подключения.  
  
 При отмене этого события будет вызван **коннекткомплете** с его параметром *адстатус* , установленным в **адстатусеррорсоккурред**.  
  
## <a name="see-also"></a>См. также:  
 [Пример модели событий ADO (Visual c++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
