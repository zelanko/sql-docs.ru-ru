---
title: "События BeginTrans CommitTrans, RollbackTrans (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- CommitTransComplete
- Connection::BeginTransComplete
- Connection::RollbackTransComplete
- Connection::CommitTransComplete
- RollbackTransComplete
- BeginTransComplete
helpviewer_keywords:
- CommitTransComplete event [ADO]
- RollbackTransComplete event [ADO]
- BeginTransComplete event [ADO]
ms.assetid: ec4e4b38-e9c6-4757-b2ef-4e468ae5f1d8
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 782e17249205d2619fc5aa4c0699166fc21f7c78
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado"></a>BeginTransComplete, CommitTransComplete и RollbackTransComplete события (ADO)
Эти события будет вызван после указанной операции в [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта завершает выполнение.  
  
-   **BeginTransComplete** вызывается после [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) операции.  
  
-   **CommitTransComplete** вызывается после [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) операции.  
  
-   **RollbackTransComplete** вызывается после [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) операции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BeginTransComplete TransactionLevel, pError, adStatus, pConnection  
CommitTransComplete pError, adStatus, pConnection  
RollbackTransComplete pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *TransactionLevel*  
 Объект **длинные** значение, содержащее новый уровень транзакции **BeginTrans** , вызвавшее данное событие.  
  
 *pError*  
 [Ошибка](../../../ado/reference/ado-api/error-object.md) объекта. Здесь описываются ошибки, возникшей при значениях EventStatusEnum **adStatusErrorsOccurred**; в противном случае оно не задано.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния. При вызове любого из этих событий, этот параметр имеет значение **adStatusOK** при успешном выполнении операции, которая вызвала событие или для **adStatusErrorsOccurred** при сбое операции.  
  
 Эти события можно предотвратить последующие уведомления, установка этого параметра **adStatusUnwantedEvent** перед возвратом события.  
  
 *pConnection*  
 **Подключения** объекта, для которого возникает данное событие.  
  
## <a name="remarks"></a>Замечания  
 В Visual C++ несколькими **подключений** могут совместно использовать одинаковые метода обработчика событий. Метод использует возвращенное **подключения** объектом, чтобы определить, какой из объектов, вызвавшее событие.  
  
 Если [атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md) свойству **adXactCommitRetaining** или **adXactAbortRetaining**, начинает новую транзакцию после фиксации или отката транзакции. Используйте **BeginTransComplete** пропустить все события, но первое событие начала транзакции.  
  
## <a name="see-also"></a>См. также:  
 [Пример модели событий ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [BeginTrans CommitTrans и пример RollbackTrans методы (Visual Basic)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vb.md)   
 [Сводка обработчик событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Методы BeginTrans, CommitTrans и RollbackTrans (ADO)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)
