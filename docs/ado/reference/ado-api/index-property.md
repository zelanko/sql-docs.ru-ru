---
title: "Свойство Index | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: Recordset21::Index
helpviewer_keywords: Index property
ms.assetid: 1c79e271-21ec-41a8-8163-c5e89f0001a7
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9e7dac3b9494e2c23de547bdf96ba0079a264af9
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="index-property"></a>Свойство Index
Указывает имя индекса в настоящее время действует для [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение, которое является имя индекса.  
  
## <a name="remarks"></a>Remarks  
 Индекс с именем **индекс** свойство должно ранее было объявлено для базовой таблицы базового **записей** объекта. То есть индекса должна быть объявлена программными средствами как ADOX [индекс](../../../ado/reference/adox-api/index-object-adox.md) объекта, или при создании базовой таблицы.  
  
 Ошибка во время выполнения происходит, если индекс не может быть задано. **Индекс** невозможно задать свойство при следующих условиях:  
  
-   В пределах [WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md) или **RecordsetChangeComplete** обработчик событий.  
  
-   Если **записей** по-прежнему выполняется операция (которой можно определить с помощью [состояние](../../../ado/reference/ado-api/state-property-ado.md) свойство).  
  
-   Если фильтр был установлен **записей** с [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство.  
  
 **Индекс** свойства всегда задается успешно при **набора записей** закрыто, но **набора записей** не будет успешно открыт, или индекс не будет доступна, если базовый поставщик не поддерживает индексы.  
  
 Если индекс могут быть установлены, может измениться текущей позиции строки. Это вызовет обновление [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) свойство и формируют **WillChangeRecordset**, **RecordsetChangeComplete**, [WillMove ](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md), и [MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md) события.  
  
 Если индекс может быть задано и [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) свойство **adLockPessimistic** или **adLockOptimistic**, неявное [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) выполняется операция. Это освобождает текущих и уязвимую групп. Любой существующий фильтр освобождается и текущей позиции строки изменяется на первой строке упорядоченный **записей**.  
  
 **Индекс** свойство используется в сочетании с [Seek](../../../ado/reference/ado-api/seek-method.md) метод. Если базовый поставщик не поддерживает **индекс** свойство и, следовательно, **Seek** метод, рассмотрите возможность использования [найти](../../../ado/reference/ado-api/find-method-ado.md) метод вместо него. Определить ли **записей** объект поддерживает индексы с [поддерживает](../../../ado/reference/ado-api/supports-method.md)**(adIndex)** метод.  
  
 Встроенная **индекс** свойство не относится к динамической [оптимизировать](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) свойство, несмотря на то, что оба они работают с индексами.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Поиск метода и пример свойства индекса (Visual Basic)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [Объект индекса (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)   
 [Метод Seek](../../../ado/reference/ado-api/seek-method.md)
