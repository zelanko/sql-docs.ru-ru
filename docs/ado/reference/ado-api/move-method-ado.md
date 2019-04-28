---
title: Метод Move (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Move
- Recordset15::raw_Move
helpviewer_keywords:
- Move method [ADO]
ms.assetid: 13fe9381-d00b-4f4a-9162-83c3f21b3837
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c8306a7d8e3247e77579d0bebc9147c3f9a1cc56
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62863491"
---
# <a name="move-method-ado"></a>Метод Move (ADO)
Перемещает положение элемента текущей записи в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.Move NumRecords, Start  
```  
  
#### <a name="parameters"></a>Параметры  
 *NumRecords*  
 Со знаком **Long** выражение, указывающее количество записей, перемещает текущую позицию записи.  
  
 *Запуск*  
 Необязательный. Объект **строка** значение или **Variant** , результатом которого является закладка. Можно также использовать [BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md) значение.  
  
## <a name="remarks"></a>Примечания  
 **Переместить** метод поддерживается на всех **записей** объектов.  
  
 Если *NumRecords* аргумента не равно нулю, положения текущей записи перемещается вперед (к концу **записей**). Если *NumRecords* меньше нуля, положения текущей записи выполняется перемещение назад (к началу **записей**).  
  
 Если **переместить** вызов перемещает положение текущей записи в точку перед первой записи, ADO задает текущую запись до позиции перед первой записи в наборе записей ([BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) является **True** ). Переместить назад when **BOF** свойство уже **True** приводит к ошибке.  
  
 Если **переместить** вызов перемещает положение текущей записи к точке после последней записи, ADO задает текущую запись в позицию после последней записи в наборе записей ([EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) является **True** ). Переместить вперед when **EOF** свойство уже **True** приводит к ошибке.  
  
 Вызов **переместить** метод с пустого **записей** возвращает ошибку.  
  
 Если передать *запустить* аргумент, перемещение является относительно записи с этой закладкой, при условии, что **набор записей** объект поддерживает закладки. Если не указан, перемещение задается относительно текущей записи.  
  
 Если вы используете [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) свойство локально кэшировать записи от поставщика, передав *NumRecords* аргумент, который перемещает текущую позицию записи за пределами текущей группы кэшированных записей заставляет ADO для получения новой группы записи, начиная с записи назначения. **CacheSize** свойство определяет размер только что полученный группы, а запись назначения является первой записью извлечь.  
  
 Если **записей** объекта является однонаправленным, пользователь все равно могут передавать *NumRecords* аргумент меньше нуля, предоставляемые назначения находится в пределах текущего набора кэшированные записи. Если **переместить** вызов перемещает положение текущей записи к записи перед первой кэшированной записи, произойдет ошибка. Таким образом можно использовать запись кэша, который поддерживает полный прокрутку через поставщика, который поддерживает только прямую прокрутку. Так как кэшированные записи загружаются в память, следует избегать кэширования больше записей, чем необходимо. Даже в том случае, если последовательным **записей** обратной поддерживает объект перемещается таким образом, вызов [MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) метод на любом последовательного **набор записей** объект будет по-прежнему приводят к ошибке.  
  
> [!NOTE]
>  Поддержка возврат к предыдущим последовательным **записей** не является прогнозируемым, в зависимости от поставщика. Если текущая запись позиционирует после последней записи в **записей**, **переместить** обратной может не привести правильный текущей позиции.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода Move (Visual Basic)](../../../ado/reference/ado-api/move-method-example-vb.md)   
 [Пример метода Move (VBScript)](../../../ado/reference/ado-api/move-method-example-vbscript.md)   
 [Пример метода Move (Visual C++)](../../../ado/reference/ado-api/move-method-example-vc.md)   
 [Примеры MoveFirst, MoveLast, MoveNext и MovePrevious методы (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [Примеры MoveFirst, MoveLast, MoveNext и MovePrevious методы (RDS)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)   
 [Метод MoveRecord (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)
