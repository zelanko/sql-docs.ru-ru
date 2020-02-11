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
ms.openlocfilehash: c3626f91018714fa4d67304c92ce464d82fb5c8e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67917225"
---
# <a name="requery-method"></a>Метод Requery
Обновляет данные в объекте [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) путем повторного выполнения запроса, на котором основан объект.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.Requery Options  
```  
  
#### <a name="parameters"></a>Параметры  
 *Параметры*  
 Необязательный параметр. Битовая маска, которая содержит значения [ексекутеоптионенум](../../../ado/reference/ado-api/executeoptionenum.md) и [коммандтипинум](../../../ado/reference/ado-api/commandtypeenum.md) , влияющие на эту операцию.  
  
> [!NOTE]
>  Если для *параметра options* задано значение **адасинцексекуте**, эта операция будет выполняться асинхронно и будет выдано событие [рекордсетчанжекомплете](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md) , когда завершается. Значения **ексекутеопененум** в **адексекутенорекордс** или **адексекутестреам** не следует использовать с параметром **Requery**.  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **Reissuing** , чтобы обновить все содержимое объекта **набора записей** из источника данных, повторно выполнив исходную команду и извлекая данные во второй раз. Вызов этого метода эквивалентен вызову методов [Close](../../../ado/reference/ado-api/close-method-ado.md) и [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) в случае успеха. Если редактируется текущая запись или добавляется новая запись, возникает ошибка.  
  
 Пока объект **Recordset** открыт, свойства, определяющие природу курсора ([примеры CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md), [LockType](../../../ado/reference/ado-api/locktype-property-ado.md), [maxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)и т. д.), доступны только для чтения. Таким способом, метод **Requery** может обновить только текущий курсор. Чтобы изменить какие-либо свойства курсора и просмотреть результаты, необходимо использовать метод [Close](../../../ado/reference/ado-api/close-method-ado.md) , чтобы свойства снова стали доступны для чтения и записи. Затем можно изменить параметры свойств и вызвать метод [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) , чтобы снова открыть курсор.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Примеры методов Execute, Requery и Clear (Visual Basic)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Пример методов Execute, Requery и Clear (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Пример методов Execute, Requery и Clear (Visual c++)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [Свойство CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)
