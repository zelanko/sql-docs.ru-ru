---
description: Методы BeginTrans, CommitTrans и RollbackTrans (ADO)
title: Методы примеры BeginTrans, CommitTrans и RollbackTrans (ADO) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 71dd02544e80d24e96d9cc64fa1e5947f38c685a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451196"
---
# <a name="begintrans-committrans-and-rollbacktrans-methods-ado"></a>Методы BeginTrans, CommitTrans и RollbackTrans (ADO)
Эти методы транзакций управляют обработкой транзакций в объекте [соединения](../../../ado/reference/ado-api/connection-object-ado.md) следующим образом:  
  
-   **Примеры BeginTrans** Начинает новую транзакцию.  
  
-   **CommitTrans** Сохраняет все изменения и завершает текущую транзакцию. Она также может начать новую транзакцию.  
  
-   **RollbackTrans** Отменяет все изменения, внесенные во время текущей транзакции, и завершает транзакцию. Она также может начать новую транзакцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
level = object.BeginTrans()  
object.BeginTrans  
object.CommitTrans  
object.RollbackTrans  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Примеры BeginTrans** может вызываться как функция, возвращающая переменную **типа Long** , указывающую уровень вложенности транзакции.  
  
#### <a name="parameters"></a>Параметры  
 *object*  
 Объект **соединения** .  
  
## <a name="connection"></a>Соединение  
 Используйте эти методы с объектом **Connection** , если нужно сохранить или отменить ряд изменений, внесенных в исходные данные в виде одного элемента. Например, чтобы переносить деньги между учетными записями, можно вычесть сумму из единицы и добавить ту же сумму в другую. В случае сбоя одного из обновлений учетные записи больше не будут сбалансированы. Внесение этих изменений в открытой транзакции гарантирует, что все изменения не проходят.  
  
> [!NOTE]
>  Не все поставщики поддерживают транзакции. Убедитесь, что определяемое поставщиком свойство "**Transaction DDL**" отображается в коллекции [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) объекта **Connection** , указывая, что поставщик поддерживает транзакции. Если поставщик не поддерживает транзакции, вызов одного из этих методов возвратит ошибку.  
  
 После вызова метода **примеры BeginTrans** поставщик больше не будет мгновенно фиксировать внесенные изменения, пока вы не вызовите **CommitTrans** или **RollbackTrans** , чтобы завершить транзакцию.  
  
 Для поставщиков, поддерживающих вложенные транзакции, вызов метода **примеры BeginTrans** в открытой транзакции запускает новую вложенную транзакцию. Возвращаемое значение указывает уровень вложенности: возвращаемое значение "1" указывает, что вы открыли транзакцию верхнего уровня (то есть транзакция не вложена в другую транзакцию), "2" означает, что вы открыли транзакцию второго уровня (транзакцию, вложенную в транзакцию верхнего уровня) и т. д. Вызов **CommitTrans** или **RollbackTrans** влияет только на последнюю открытую транзакцию. перед разрешением любых транзакций более высокого уровня необходимо закрыть или откатить текущую транзакцию.  
  
 Вызов метода **CommitTrans** сохраняет изменения, сделанные в открытой транзакции в соединении, и завершает транзакцию. Вызов метода **RollbackTrans** изменяет все изменения, сделанные в открытой транзакции, и завершает транзакцию. Вызов любого из методов при отсутствии открытой транзакции приводит к ошибке.  
  
 В зависимости от свойства [атрибута](../../../ado/reference/ado-api/attributes-property-ado.md) объекта **Connection** вызов методов **CommitTrans** или **RollbackTrans** может автоматически начать новую транзакцию. Если свойство **Attributes** имеет значение **адксакткоммитретаининг**, то поставщик автоматически запускает новую транзакцию после вызова **CommitTrans** . Если свойство **Attributes** имеет значение **адксактабортретаининг**, то поставщик автоматически запускает новую транзакцию после вызова **RollbackTrans** .  
  
## <a name="remote-data-service"></a>Remote Data Service  
 Методы **примеры BeginTrans**, **CommitTrans**и **RollbackTrans** недоступны для объекта **подключения** на стороне клиента.  
  
## <a name="applies-to"></a>Применение  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов примеры BeginTrans, CommitTrans и RollbackTrans (Visual Basic)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vb.md)   
 [Примеры методов примеры BeginTrans, CommitTrans и RollbackTrans (Visual c++)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vc.md)   
 [Свойство Attributes (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
