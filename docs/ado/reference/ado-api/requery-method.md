---
description: Метод Requery
title: Метод Requery | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 12f60b295d569119a356631dc445bd034916665a
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989555"
---
# <a name="requery-method"></a>Метод Requery
Обновляет данные в объекте [набора записей](./recordset-object-ado.md) путем повторного выполнения запроса, на котором основан объект.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.Requery Options  
```  
  
#### <a name="parameters"></a>Параметры  
 *Параметры*  
 Необязательный элемент. Битовая маска, которая содержит значения [ексекутеоптионенум](./executeoptionenum.md) и [коммандтипинум](./commandtypeenum.md) , влияющие на эту операцию.  
  
> [!NOTE]
>  Если для *параметра options* задано значение **адасинцексекуте**, эта операция будет выполняться асинхронно и будет выдано событие [рекордсетчанжекомплете](./willchangerecordset-and-recordsetchangecomplete-events-ado.md) , когда завершается. Значения **ексекутеопененум** в **адексекутенорекордс** или **адексекутестреам** не следует использовать с параметром **Requery**.  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **Reissuing** , чтобы обновить все содержимое объекта **набора записей** из источника данных, повторно выполнив исходную команду и извлекая данные во второй раз. Вызов этого метода эквивалентен вызову методов [Close](./close-method-ado.md) и [Open](./open-method-ado-recordset.md) в случае успеха. Если редактируется текущая запись или добавляется новая запись, возникает ошибка.  
  
 Пока объект **Recordset** открыт, свойства, определяющие природу курсора ([примеры CursorType](./cursortype-property-ado.md), [LockType](./locktype-property-ado.md), [maxRecords](./maxrecords-property-ado.md)и т. д.), доступны только для чтения. Таким способом, метод **Requery** может обновить только текущий курсор. Чтобы изменить какие-либо свойства курсора и просмотреть результаты, необходимо использовать метод [Close](./close-method-ado.md) , чтобы свойства снова стали доступны для чтения и записи. Затем можно изменить параметры свойств и вызвать метод [Open](./open-method-ado-recordset.md) , чтобы снова открыть курсор.  
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов Execute, Requery и Clear (Visual Basic)](./execute-requery-and-clear-methods-example-vb.md)   
 [Пример методов Execute, Requery и Clear (VBScript)](./execute-requery-and-clear-methods-example-vbscript.md)   
 [Пример методов Execute, Requery и Clear (Visual c++)](./execute-requery-and-clear-methods-example-vc.md)   
 [Свойство CommandText (ADO)](./commandtext-property-ado.md)