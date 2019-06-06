---
title: Свойство Index | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 21f8ec6ea0ed9cd1af8257dcd10b18f59903c929
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66694793"
---
# <a name="index-property"></a>Свойство Index
Указывает имя индекса в настоящее время действует для [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение, представляющее собой имя индекса.  
  
## <a name="remarks"></a>Примечания  
 Индекс с именем, **индекс** свойство должна быть предварительно объявлена для базовой таблицы базового **записей** объекта. То есть индекс должна быть объявлена программными средствами как ADOX [индекс](../../../ado/reference/adox-api/index-object-adox.md) объекта, или при создании базовой таблицы.  
  
 Ошибка во время выполнения возникнет в том случае, если индекс не может быть задано. **Индекс** невозможно задать свойство при следующих условиях:  
  
-   В рамках [события WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md) или **RecordsetChangeComplete** обработчик событий.  
  
-   Если **записей** по-прежнему выполняет операцию (которой можно определить с помощью [состояние](../../../ado/reference/ado-api/state-property-ado.md) свойство).  
  
-   Если фильтр был настроен на **записей** с [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство.  
  
 **Индекс** может всегда быть установлено успешно Если **набор записей** закрыто, но **набор записей** не будет успешно открыт, или индекс нельзя использовать, если базовый поставщик не поддерживает индексы.  
  
 Если индекс может быть задано, текущая позиция строки может измениться. Это вызовет обновление [примеры AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) свойство и будет запускаться **события WillChangeRecordset**, **RecordsetChangeComplete**, [события WillMove ](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md), и [MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md) события.  
  
 Если индекс может быть задано и [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) свойство **adLockPessimistic** или **adLockOptimistic**, затем неявным [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) выполняется операция. Это освобождает текущие и затронутых групп. Любой существующий фильтр освобождается, и текущая позиция строки изменяется на первую строку переупорядоченных **записей**.  
  
 **Индекс** свойство используется в сочетании с [Seek](../../../ado/reference/ado-api/seek-method.md) метод. Если базовый поставщик не поддерживает **индекс** свойство и, следовательно, **Seek** метод, рассмотрите возможность использования [найти](../../../ado/reference/ado-api/find-method-ado.md) метод вместо этого. Определить ли **записей** объект поддерживает индексы с [поддерживает](../../../ado/reference/ado-api/supports-method.md) **(adIndex)** метод.  
  
 Встроенная **индекс** свойство не относится к динамической [оптимизировать](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) свойство, несмотря на то, что оба они работают с индексами.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры метода Seek и свойства Index (Visual Basic)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [Объект INDEX (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)   
 [Метод Seek](../../../ado/reference/ado-api/seek-method.md)
