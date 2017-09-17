---
title: "Requery-метод | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::Requery
- Recordset15::raw_Requery
helpviewer_keywords:
- Requery method [ADO]
ms.assetid: d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f59d4c6cdcdb3f34be4361969da15e5af117f995
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="requery-method"></a>Requery-метод
Обновляет данные в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта путем повторного выполнения запроса, на котором основан объект.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.Requery Options  
```  
  
#### <a name="parameters"></a>Параметры  
 *Параметры*  
 Необязательно. Битовая маска, содержащий [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) и [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) значения, влияющие на эту операцию.  
  
> [!NOTE]
>  Если *параметры* равно **adAsyncExecute**, эта операция будет выполняться асинхронно и [RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md) событий будет выдаваться при ее завершается. **ExecuteOpenEnum** значения **adExecuteNoRecords** или **adExecuteStream** не должны использоваться с **Requery**.  
  
## <a name="remarks"></a>Замечания  
 Используйте **Requery** метод для обновления все содержимое **записей** из источника данных, получения исходную команду и получения данных во второй раз. Вызов этого метода эквивалентен вызову [закрыть](../../../ado/reference/ado-api/close-method-ado.md) и [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) методы в течение промежутка времени. При изменении текущей записи или добавления новой записи, возникает ошибка.  
  
 Хотя **записей** открыт объект, свойства, определяющие характер курсора ([CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md), [LockType](../../../ado/reference/ado-api/locktype-property-ado.md), [MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md) и так далее) доступны только для чтения. Таким образом **Requery** метода можно обновить только текущий курсор. Чтобы изменить какие-либо свойства курсора и просмотреть результаты, необходимо использовать [закрыть](../../../ado/reference/ado-api/close-method-ado.md) метод, чтобы свойства становятся чтения и записи еще раз. Можно изменить значения свойств и вызовов [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) метода для повторного открытия курсора.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Выполнение и Requery снимите примере методы (Visual Basic)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Выполнение и Requery снимите примере методы (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Выполнение и Requery снимите примере методы (VC ++)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [Свойства CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)

