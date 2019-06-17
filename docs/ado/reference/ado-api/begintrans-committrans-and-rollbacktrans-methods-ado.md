---
title: Примеры BeginTrans, CommitTrans и RollbackTrans методы (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::raw_RollbackTrans
- Connection15::CommitTrans
- Connection15::raw_CommitTrans
- Connection15::raw_BeginTrans
- Connection15::BeginTrans
- Connection15::RollbackTrans
helpviewer_keywords:
- BeginTrans method [ADO]
- CommitTrans method [ADO]
- RollbackTrans method [ADO]
ms.assetid: d4683472-4120-4236-8640-fa9ae289e23e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ee5560a27f7df49a82e964753f792bd46270d3a6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66696482"
---
# <a name="begintrans-committrans-and-rollbacktrans-methods-ado"></a>Методы BeginTrans, CommitTrans и RollbackTrans (ADO)
Эти методы транзакции управление обработки в пределах транзакций [подключения](../../../ado/reference/ado-api/connection-object-ado.md) следующим образом:  
  
-   **Примеры BeginTrans** начинает новую транзакцию.  
  
-   **CommitTrans** сохраняет все изменения и завершает текущую транзакцию. Кроме того, он может начать новую транзакцию.  
  
-   **RollbackTrans** отменяет все изменения, внесенные в ходе текущей транзакции и завершает транзакцию. Кроме того, он может начать новую транзакцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
level = object.BeginTrans()  
object.BeginTrans  
object.CommitTrans  
object.RollbackTrans  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Примеры BeginTrans** может вызываться как функция, возвращающая **Long** переменной, показывающей, уровень вложенности транзакции.  
  
#### <a name="parameters"></a>Параметры  
 *object*  
 Объект **подключения** объекта.  
  
## <a name="connection"></a>Соединение  
 Используйте эти методы с **подключения** объекта, если вы хотите сохранить или отменить ряд изменений, внесенных в данные источника, как единое целое. Например для передачи денег между учетными записями, можно вычесть сумму из одного и добавьте столько же для других. Если либо обновите завершается ошибкой, учетные записи больше не сбалансированы. Эти изменения в открытой транзакции гарантирует, что все или изменения проходят через.  
  
> [!NOTE]
>  Не все поставщики поддерживают транзакции. Убедитесь, что свойство, определенное поставщиком "**DDL транзакций**" отображается в **подключения** объекта [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции, указывающий, что поставщик поддерживает транзакции. Если поставщик не поддерживает транзакции, вызвав один из этих методов возвращает ошибку.  
  
 После вызова метода **BeginTrans** метод, поставщик будет зафиксировать больше не мгновенно изменения, внесенные до вызова метода **CommitTrans** или **RollbackTrans** до конца транзакция.  
  
 Для поставщиков, которые поддерживают вложенные транзакции вызова **BeginTrans** метод в открытой транзакции начинает новый, вложенные транзакции. Возвращаемое значение указывает уровень вложенности: возвращаемое значение «1» указывает, вы открыли транзакцией верхнего уровня (то есть транзакция не вложен в другой транзакции), «2» означает, что вы открыли транзакции второго уровня ( транзакция вложенной транзакции верхнего уровня), и т. д. Вызов **CommitTrans** или **RollbackTrans** затрагивает только последний открытый транзакции; необходимо закрыть или отката текущей транзакции, чтобы связать все более высокого уровня транзакции.  
  
 Вызов **CommitTrans** метод сохраняет изменения, внесенные в открытые транзакции в соединении и завершает транзакцию. Вызов **RollbackTrans** метод отменяет любые изменения, внесенные в открытые транзакции и завершает транзакцию. Вызов любого из этих методов, если нет открытых транзакций приводит к ошибке.  
  
 В зависимости от **подключения** объекта [атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md) свойство, вызывая **CommitTrans** или **RollbackTrans** может методы автоматически запускает новую транзакцию. Если **атрибуты** свойству **adXactCommitRetaining**, поставщик автоматически запускает новую транзакцию после **CommitTrans** вызова. Если **атрибуты** свойству **adXactAbortRetaining**, поставщик автоматически запускает новую транзакцию после **RollbackTrans** вызова.  
  
## <a name="remote-data-service"></a>Служба удаленных данных  
 **BeginTrans**, **CommitTrans**, и **RollbackTrans** методы недоступны на стороне клиента **подключения** объекта.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры BeginTrans, CommitTrans и Rollbacktrans по методы (Visual Basic)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vb.md)   
 [Примеры BeginTrans, CommitTrans и Rollbacktrans методы (Visual C++)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vc.md)   
 [Свойство Attributes (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
