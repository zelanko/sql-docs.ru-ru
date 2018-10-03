---
title: События BeginTrans, CommitTrans, RollbackTrans (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: afd8b9d4a45bdc98388f1133b3478a1cfbe51e4c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773452"
---
# <a name="begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado"></a>BeginTransComplete CommitTransComplete и RollbackTransComplete события (ADO)
Эти события, которая будет вызываться после указанной операции на [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объект завершения выполнения.  
  
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
 Объект **Long** значение, содержащее новый уровень транзакции **BeginTrans** , вызвавшее данное событие.  
  
 *pError*  
 [Ошибка](../../../ado/reference/ado-api/error-object.md) объекта. Он описывает ошибки, возникшей при значение EventStatusEnum **adStatusErrorsOccurred**; в противном случае оно не задано.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния. При вызове любого из этих событий, этот параметр имеет значение **adStatusOK** при успешной операции, которая вызвала событие, или чтобы **adStatusErrorsOccurred** Если произошел сбой операции.  
  
 Эти события можно предотвратить последующие уведомления, задать этому параметру значение **adStatusUnwantedEvent** перед возвратом события.  
  
 *pConnection*  
 **Подключения** объекта, для которой произошло это событие.  
  
## <a name="remarks"></a>Примечания  
 В Visual C++ нескольких **подключений** могут совместно использовать же метод обработки события. Метод использует возвращенное **подключения** объектом, чтобы определить, какой объект вызвавшее событие.  
  
 Если [атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md) свойству **adXactCommitRetaining** или **adXactAbortRetaining**, начинается новая транзакция после фиксации или отката транзакции. Используйте **BeginTransComplete** событие, чтобы пропустить все, но первое событие начала транзакции.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (Visual C++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Примеры BeginTrans, CommitTrans и Rollbacktrans по методы (Visual Basic)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vb.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Методы BeginTrans, CommitTrans и RollbackTrans (ADO)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)
