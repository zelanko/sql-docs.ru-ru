---
title: Методического фрагмента данных (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::raw_GetChunk
- Field20::GetChunk
helpviewer_keywords:
- GetChunk method [ADO]
ms.assetid: fc268e22-205b-44a3-9038-ffed51e23e10
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 43c5fef08d22364b9842c58fc82d46ba4bfa00bd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67918563"
---
# <a name="getchunk-method-ado"></a>Метод GetChunk (ADO)
Возвращает все или часть содержимого большого текстового или двоичного объекта [поля](../../../ado/reference/ado-api/field-object.md) данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
variable = field.GetChunk(Size)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **значение типа Variant**.  
  
#### <a name="parameters"></a>Параметры  
 *Размер*  
 **Длинное** выражение, равное количеству байтов или символов, которое необходимо получить.  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **GetObject** для объекта **field** , чтобы получить часть или все его длинные двоичные или символьные данные. В ситуациях, когда память системы ограничена, можно использовать метод " **блока** " для обработки длинных значений в частях, а не полностью.  
  
 Данные, возвращаемые вызовом методаического **блока** , назначаются *переменной*. Если *Размер* больше остальных данных **, метод WebMethod** возвращает только оставшиеся данные без *переменной* заполнения пустыми пробелами. Если поле пустое **, метод WebMethod** возвращает значение null.  
  
 Каждый последующий вызов методаического **блока** извлекает данные, начиная с места, в **котором предыдущий вызов** метода Left был отключен. Однако если вы получаете данные из одного поля, а затем задаете или считываете значение другого поля в текущей записи, то ADO считает, что вы завершили извлечение данных из первого поля. При повторном вызове **метода WebMethod в первом** поле ADO интерпретирует вызов как новую операцию- **блок** и начинает чтение с начала данных. Доступ к полям других объектов [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) , которые не являются клонами первого объекта **набора записей** , не приведет **к нарушению** операций GetObject.  
  
 Если бит **адфлдлонг** в свойстве [Attributes](../../../ado/reference/ado-api/attributes-property-ado.md) объекта **field** имеет значение **true**, для этого поля можно **использовать метод GetObject** .  
  
 Если при **использовании метода GetObject** для объекта **поля** нет текущей записи, то происходит ошибка 3021 (нет текущей записи).  
  
> [!NOTE]
>  Метод **GetObject** не работает с объектами **полей** объекта [Record](../../../ado/reference/ado-api/record-object-ado.md) . Она не выполняет никаких операций и выдает ошибку во время выполнения.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов AppendChunk и-блока (Visual Basic)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vb.md)   
 [Примеры методов AppendChunk и-блока (Visual c++)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vc.md)   
 [Метод AppendChunk (ADO)](../../../ado/reference/ado-api/appendchunk-method-ado.md)   
 [Свойство Attributes (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
