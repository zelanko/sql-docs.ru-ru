---
title: Примеры MoveFirst, MoveLast, MoveNext и MovePrevious методы (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 905fc532057a827f30735efe067464f488f51dc0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63242906"
---
# <a name="movefirst-movelast-movenext-and-moveprevious-methods-ado"></a>Примеры MoveFirst, MoveLast, MoveNext и MovePrevious методы (ADO)
Переходит к первой, последней, следующей или предыдущей записи в указанном [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта и делает этот записи текущей записи.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.{MoveFirst | MoveLast | MoveNext | MovePrevious}  
```  
  
## <a name="remarks"></a>Примечания  
 Используйте **MoveFirst** метод для перехода к первой записи в текущей позиции записи **записей**.  
  
 Используйте **MoveLast** метод для перемещения положения текущей записи к последней записи в **записей**. **Записей** объект должен поддерживать закладки или движение курсора назад; в противном случае вызов метода приведет к ошибке.  
  
 Вызов либо **MoveFirst** или **MoveLast** при **записей** пуст (оба **BOF** и **EOF** имеют значение True) приводит к ошибке.  
  
 Используйте **MoveNext** метод для перемещения текущей записи вперед положение одной записи (в нижней части **записей**). Если последняя запись становится текущей записью и вызывается **MoveNext** метода ADO задает текущую запись в позицию после последней записи в **записей** ([EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) — **True**). Переместить вперед when **EOF** свойство уже **True** приводит к ошибке.  
  
 В ADO 2.5 и более поздних версий, при **набор записей** фильтрации или сортировки и изменении данных текущей записи, вызвав **MoveNext** метод перемещает курсор на две записи вперед от текущей записи . Это потому, что при изменении текущей записи следующей записи становится новой текущей записи. Вызов **MoveNext** после изменения перемещает курсор одной записи вперед из новой текущей записи. Это отличается от поведения в ADO 2.1 и более ранних версий. В более ранних версиях, изменение данных текущей записи в отсортированном или фильтрованном **записей** не меняет позицию текущей записи, и **MoveNext** перемещает курсор к следующей записи сразу после текущей записи.  
  
 Используйте **MovePrevious** метод для перемещения текущей записи размещения обратной записи (в верхней части **записей**). **Записей** объект должен поддерживать закладки или движение курсора назад; в противном случае вызов метода приведет к ошибке. Если первая запись становится текущей записью и вызывается **MovePrevious** метода ADO задает текущую запись до позиции перед первой записи в **записей** ([BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)— **True**). Переместить назад when **BOF** свойство уже **True** приводит к ошибке. Если **записей** объект не поддерживает закладки или перемещение курсора обратной **MovePrevious** метод выдаст ошибку.  
  
 Если **записей** только вперед, и вы хотите поддерживают прокрутку вперед и назад, можно использовать [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) свойства для создания записи кэша, который будет поддерживать движение курсора назад через [переместить](../../../ado/reference/ado-api/move-method-ado.md) метод. Так как кэшированные записи загружаются в память, следует избегать кэширования больше записей, чем необходимо. Можно вызвать **MoveFirst** метод в последовательным **записей** объекта; это может привести к поставщику, повторно выполните команду, которая сформирована **записей** объекта .  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [MoveFirst, MoveLast, MoveNext и MovePrevious методы пример (Visual Basic)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-example-vb.md)   
 [Примеры MoveFirst, MoveLast, MoveNext и MovePrevious примеры методов (VBScript)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-example-vbscript.md)   
 [MoveFirst, MoveLast, MoveNext и MovePrevious примеры методов (Visual C++)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-example-vc.md)   
 [Метод Move (ADO)](../../../ado/reference/ado-api/move-method-ado.md)   
 [Примеры MoveFirst, MoveLast, MoveNext и MovePrevious методы (RDS)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)   
 [Метод MoveRecord (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)
