---
title: Примеры BeginTrans, CommitTrans, события RollbackTrans (ADO) | Документация Майкрософт
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
ms.openlocfilehash: 750e89e97eb916c7db23e71475b753a57a4d90e9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67920446"
---
# <a name="begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado"></a>События Бегинтранскомплете, Коммиттранскомплете и Роллбакктранскомплете (ADO)
Эти события будут вызываться после завершения выполнения связанной операции над объектом [Connection](../../../ado/reference/ado-api/connection-object-ado.md) .  
  
-   **Бегинтранскомплете** вызывается после операции [примеры BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) .  
  
-   **Коммиттранскомплете** вызывается после операции [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) .  
  
-   **Роллбакктранскомплете** вызывается после операции [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BeginTransComplete TransactionLevel, pError, adStatus, pConnection  
CommitTransComplete pError, adStatus, pConnection  
RollbackTransComplete pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *трансактионлевел*  
 Значение **типа Long** , которое содержит новый уровень транзакции **примеры BeginTrans** , вызвавшего это событие.  
  
 *pError*  
 Объект [ошибки](../../../ado/reference/ado-api/error-object.md) . Она описывает ошибку, которая возникла, если значение Евентстатусенум равно **адстатусеррорсоккурред**; в противном случае он не задан.  
  
 *адстатус*  
 Значение состояния [евентстатусенум](../../../ado/reference/ado-api/eventstatusenum.md) . При вызове любого из этих событий этот параметр устанавливается в значение **адстатусок** , если операция, вызвавшая событие, прошла успешно, или значение **адстатусеррорсоккурред** , если операция завершилась ошибкой.  
  
 Эти события могут препятствовать последующим уведомлениям, присвоив этому параметру значение **адстатусунвантедевент** перед возвратом события.  
  
 *пконнектион*  
 Объект **соединения** , для которого произошло это событие.  
  
## <a name="remarks"></a>Remarks  
 В Visual C++ несколько **соединений** могут совместно использовать один и тот же метод обработки событий. Метод использует возвращенный объект **соединения** , чтобы определить, какой объект вызывал событие.  
  
 Если свойство [Attributes](../../../ado/reference/ado-api/attributes-property-ado.md) имеет значение **адксакткоммитретаининг** или **адксактабортретаининг**, Новая транзакция начинается после фиксации или отката транзакции. Используйте событие **бегинтранскомплете** , чтобы пропустить все события начала транзакции, кроме первого.  
  
## <a name="see-also"></a>См. также:  
 [Пример модели событий ADO (Visual c++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Примеры методов примеры BeginTrans, CommitTrans и RollbackTrans (Visual Basic)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vb.md)   
 [Сводка по обработчику событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Методы BeginTrans, CommitTrans и RollbackTrans (ADO)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)
