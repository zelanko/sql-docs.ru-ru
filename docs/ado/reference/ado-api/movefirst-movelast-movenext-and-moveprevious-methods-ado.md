---
title: MoveFirst, MoveLast, MoveNext и MovePrevious методов (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::MoveLast
- Recordset15::MoveNext
- Recordset15::raw_MoveNext
- Recordset15::raw_MovePrevious
- Recordset15::MoveFirst
- Recordset15::raw_MoveLast
- Recordset15::MovePrevious
- Recordset15::raw_MoveFirst
helpviewer_keywords:
- MoveNext method [ADO]
- MoveLast method [ADO]
- MoveFirst method [ADO]
- MovePrevious method [ADO]
ms.assetid: a61a01a7-5b33-4150-9126-21dfa63654cb
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5803eb0c9c10c0bb4e62cc32b0f341b7ba06c32f
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="movefirst-movelast-movenext-and-moveprevious-methods-ado"></a>MoveFirst, MoveLast, MoveNext и MovePrevious методов (ADO)
Переходит к первой, последней, следующей или предыдущей записи в указанном [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта и делает этот запись текущей записи.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.{MoveFirst | MoveLast | MoveNext | MovePrevious}  
```  
  
## <a name="remarks"></a>Замечания  
 Используйте **MoveFirst** метод для перемещения положения текущей записи к первой записи в **записей**.  
  
 Используйте **MoveLast** метод для перемещения положения текущей записи к последней записи в **записей**. **Записей** объект должен поддерживать закладки или перемещение назад курсора; в противном случае вызов метода приведет к ошибке.  
  
 Вызов либо **MoveFirst** или **MoveLast** при **записей** пуст (оба **BOF** и **EOF** — True), приведет к ошибке.  
  
 Используйте **MoveNext** метод Перемещение текущей записи вперед положение одной записи (в нижней части **записей**). Если последняя запись становится текущей записью и вызывается **MoveNext** метода ADO задает текущую запись на позицию после последней записи в **записей** ([EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) — **True**). Переместить вперед Если **EOF** свойство уже **True** приводит к ошибке.  
  
 В ADO 2.5 и более поздней версии, если **набора записей** фильтрации или сортировки и изменении данных текущей записи, вызов **MoveNext** метод перемещает курсор на две записи вперед от текущей записи . Это так, как при изменении текущей записи следующей записи становится новой текущей записи. Вызов **MoveNext** после изменения перемещает курсор одной записи вперед от новой текущей записи. Это отличается от поведения в ADO 2.1 и более ранних версий. В более ранних версиях, изменение данных текущей записи в отсортированном или отфильтрованные **записей** не меняет позицию текущей записи и **MoveNext** перемещает курсор к следующей записи сразу после текущей записи.  
  
 Используйте **MovePrevious** метод Перемещение текущей записи размещения обратной записи (расположенной в верхней части **записей**). **Записей** объект должен поддерживать закладки или перемещение назад курсора; в противном случае вызов метода приведет к ошибке. Если первая запись становится текущей записи и вызывается **MovePrevious** метода ADO задает текущую запись в позицию перед первой записью в **записей** ([BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)— **True**). Переместить назад Если **BOF** свойство уже **True** приводит к ошибке. Если **записей** объект не поддерживает закладки или перемещения курсора обратной **MovePrevious** метод выдаст ошибку.  
  
 Если **записей** только вперед, и вы хотите поддерживают прокрутку вперед и назад, можно использовать [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) свойства для создания записи кэша, которое будет поддерживать перемещение назад курсора через [переместить](../../../ado/reference/ado-api/move-method-ado.md) метод. Так как кэшированные записи загружаются в память, следует кэширование больше записей, чем необходимо. Можно вызвать **MoveFirst** метода последовательным **записей** объекта; это может привести к поставщику для повторного выполнения команды, создавшего **записей** объекта .  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [MoveFirst, MoveLast, MoveNext и MovePrevious методы пример (Visual Basic)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-example-vb.md)   
 [MoveFirst, MoveLast, MoveNext и MovePrevious методы примере (VBScript)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-example-vbscript.md)   
 [MoveFirst, MoveLast, MoveNext и MovePrevious примере методы (VC ++)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-example-vc.md)   
 [Move-метод (ADO)](../../../ado/reference/ado-api/move-method-ado.md)   
 [MoveFirst, MoveLast, MoveNext и MovePrevious методов (RDS)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)   
 [Метод MoveRecord (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)
