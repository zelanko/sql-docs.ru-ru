---
title: Метод Requery | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Requery
- Recordset15::raw_Requery
helpviewer_keywords:
- Requery method [ADO]
ms.assetid: d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 433f5d279e638e3ccdf7ba3a7bb2590f80b04a6b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706922"
---
# <a name="requery-method"></a>Метод Requery
Обновляет данные в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта путем повторного выполнения запроса, на котором основан объект.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.Requery Options  
```  
  
#### <a name="parameters"></a>Параметры  
 *Параметры*  
 Необязательный параметр. Битовая маска, которая содержит [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) и [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) значения, влияющие на эту операцию.  
  
> [!NOTE]
>  Если *параметры* присваивается **adAsyncExecute**, эта операция будет выполняться асинхронно и [RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md) событие выдается, когда она завершается. **ExecuteOpenEnum** значения **adExecuteNoRecords** или **adExecuteStream** не должны использоваться с **Requery**.  
  
## <a name="remarks"></a>Примечания  
 Используйте **Requery** метод для обновления всего содержимого **записей** из источника данных, получения исходную команду и получения данных во второй раз. Вызов этого метода эквивалентен вызову [закрыть](../../../ado/reference/ado-api/close-method-ado.md) и [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) методы подряд. Если вы изменяете текущей записи или добавления новой записи, возникает ошибка.  
  
 Хотя **записей** открыт объект, свойства, определяющие характер курсор ([CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md), [LockType](../../../ado/reference/ado-api/locktype-property-ado.md), [MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md) и т.д) доступны только для чтения. Таким образом **Requery** метода можно обновлять только текущий курсор. Чтобы изменить какие-либо свойства курсора и просмотреть результаты, необходимо использовать [закрыть](../../../ado/reference/ado-api/close-method-ado.md) метод таким образом, свойства, снова становятся чтения и записи. Можно изменить значения свойств и вызов [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) метод для повторного открытия курсора.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [EXECUTE, Requery и Clear методы (Visual Basic)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [EXECUTE, Requery и Clear методы (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [EXECUTE, Requery и Clear методы (Visual C++)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [Свойство CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)
