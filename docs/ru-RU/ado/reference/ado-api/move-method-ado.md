---
title: Move-метод (ADO) | Документы Microsoft
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
- Recordset15::Move
- Recordset15::raw_Move
helpviewer_keywords:
- Move method [ADO]
ms.assetid: 13fe9381-d00b-4f4a-9162-83c3f21b3837
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9a64cfae0055f3052a75886556b7493fb096105a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="move-method-ado"></a>Move-метод (ADO)
Перемещает позицию в текущей записи [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.Move NumRecords, Start  
```  
  
#### <a name="parameters"></a>Параметры  
 *NumRecords*  
 Со знаком **длинные** выражение, указывающее количество записей, перемещает текущую позицию записей.  
  
 *Запуск*  
 Необязательно. Объект **строка** значение или **Variant** , результатом которого является закладка. Можно также использовать [BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md) значение.  
  
## <a name="remarks"></a>Замечания  
 **Переместить** метод поддерживается на всех **записей** объектов.  
  
 Если *NumRecords* аргумент больше нуля, положение текущей записи перемещается вперед (ближе к концу **записей**). Если *NumRecords* меньше нуля, положение текущей записи выполняется перемещение назад (к началу **записей**).  
  
 Если **переместить** вызов перемещает положение текущей записи точку перед первой записи, ADO задает текущую запись в позицию перед первой записи в наборе записей ([BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) — **True** ). Переместить назад Если **BOF** свойство уже **True** приводит к ошибке.  
  
 Если **переместить** вызов перемещает положение текущей записи к точке после последней записи, ADO задает текущую запись на позицию после последней записи в наборе записей ([EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) — **True** ). Переместить вперед Если **EOF** свойство уже **True** приводит к ошибке.  
  
 Вызов **переместить** пустой метод **записей** возвращает ошибку.  
  
 При передаче *запустить* аргумента перемещения указывается относительно записи с этой закладкой, при условии, что **записей** объект поддерживает закладки. Если не указан, перемещение задается относительно текущей записи.  
  
 Если вы используете [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) свойство локально кэширование записи от поставщика, передавая *NumRecords* аргумент, который перемещает текущую позицию записей за пределами текущей группы кэшированных записей принудительно ADO, чтобы получить новую группу записи, начиная с записи назначения. **CacheSize** свойство определяет размер только что полученный группы и назначения запись является первой записи получены.  
  
 Если **записей** объекта является однонаправленным, пользователь по-прежнему можно передавать *NumRecords* аргумента меньше нуля, предоставляемые назначения, находится в пределах текущего кэшированных записей. Если **переместить** вызов перемещает положение текущей записи к записи перед первой записью кэшированных завершится ошибкой. Таким образом можно использовать кэш записи, который поддерживает полную прокрутку через поставщика, который поддерживает только прямую прокрутку. Так как кэшированные записи загружаются в память, следует кэширование больше записей, чем необходимо. Даже в том случае, если только для прямого **записей** перемещает объект поддерживает обратной таким образом, вызов [MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) метод для какого-либо последовательным **набора записей** объекта будет по-прежнему выдает ошибку.  
  
> [!NOTE]
>  Поддержка возврат к предыдущим последовательным **записей** не является прогнозируемым, зависящее от поставщика. Если текущая запись был помещен после последней записи в **записей**, **переместить** обратной он не может привести к правильный текущей позиции.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода Move (Visual Basic)](../../../ado/reference/ado-api/move-method-example-vb.md)   
 [Пример метода Move (VBScript)](../../../ado/reference/ado-api/move-method-example-vbscript.md)   
 [Пример метода Move (VC ++)](../../../ado/reference/ado-api/move-method-example-vc.md)   
 [MoveFirst, MoveLast, MoveNext и MovePrevious методов (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [MoveFirst, MoveLast, MoveNext и MovePrevious методов (RDS)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)   
 [Метод MoveRecord (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)
