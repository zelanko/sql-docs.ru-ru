---
title: Свойство index | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset21::Index
helpviewer_keywords:
- Index property
ms.assetid: 1c79e271-21ec-41a8-8163-c5e89f0001a7
author: rothja
ms.author: jroth
ms.openlocfilehash: 2a77aa3c2e144859eaead332e71c5c4c8776608c
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82758700"
---
# <a name="index-property"></a>Свойство Index
Указывает имя индекса, действующего в настоящий момент для объекта [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает **строковое** значение, представляющее собой имя индекса.  
  
## <a name="remarks"></a>Remarks  
 Индекс, указанный в свойстве **index** , должен быть ранее объявлен в базовой таблице базового объекта **Recordset** . Это означает, что индекс должен быть объявлен программным образом как объект [индекса](../../../ado/reference/adox-api/index-object-adox.md) ADOX или при создании базовой таблицы.  
  
 Если индекс не может быть установлен, возникнет ошибка времени выполнения. Свойство **index** не может быть задано при следующих условиях:  
  
-   В обработчике событий [виллчанжерекордсет](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md) или **рекордсетчанжекомплете** .  
  
-   Значение, если **набор записей** по-прежнему исполняет операцию (которая может быть определена свойством [State](../../../ado/reference/ado-api/state-property-ado.md) ).  
  
-   Значение, если для **набора записей** задан фильтр со свойством [Filter](../../../ado/reference/ado-api/filter-property.md) .  
  
 Свойство **index** всегда может быть установлено успешно, если **набор записей** закрыт, но **набор записей** не будет открыт успешно, или индекс не будет использоваться, если базовый поставщик не поддерживает индексы.  
  
 Если индекс может быть установлен, текущая позиция строки может измениться. Это приведет к обновлению свойства [примеры AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) и запустит события **виллчанжерекордсет**, **рекордсетчанжекомплете**, [виллмове](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)и [мовекомплете](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md) .  
  
 Если индекс можно задать и свойство [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) имеет значение **адлоккпессимистик** или **adLockOptimistic**, то выполняется неявная операция [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) . Это освобождает текущие и затронутые группы. Все существующие фильтры освобождаются, и текущая строка строки изменяется на первую строку переупорядоченного **набора записей**.  
  
 Свойство **index** используется в сочетании с методом [Seek](../../../ado/reference/ado-api/seek-method.md) . Если базовый поставщик не поддерживает свойство **index** , и поэтому метод **Seek** , попробуйте использовать вместо него метод [Find](../../../ado/reference/ado-api/find-method-ado.md) . Определите, поддерживает ли объект **набора записей** индексы с [поддержкой](../../../ado/reference/ado-api/supports-method.md)метода **(адиндекс)** .  
  
 Встроенное свойство **индекса** не связано с динамическим свойством [optimize](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) , хотя они работают с индексами.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода Seek и свойства Index (Visual Basic)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [Объект index (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)   
 [Seek, метод](../../../ado/reference/ado-api/seek-method.md)
