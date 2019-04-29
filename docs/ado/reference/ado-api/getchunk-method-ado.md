---
title: Метод GetChunk (ADO) | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 538ccfd71375521bf0ba035ccfa55746c4d76af9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63028051"
---
# <a name="getchunk-method-ado"></a>Метод GetChunk (ADO)
Возвращает все или часть, содержимое большие текстовые или двоичные данные [поле](../../../ado/reference/ado-api/field-object.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
variable = field.GetChunk(Size)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **Variant**.  
  
#### <a name="parameters"></a>Параметры  
 *Размер*  
 Объект **Long** выражение, которое равно числу байт или символов, которые вы хотите получить.  
  
## <a name="remarks"></a>Примечания  
 Используйте **GetChunk** метод **поле** объекта для извлечения всех или части ее долго двоичных или символьных данных. В ситуациях, где ограничена системной памяти, можно использовать **GetChunk** метод для обработки длинных значений в части, а не полностью.  
  
 Данные, **GetChunk** вызов возвращает назначается *переменной*. Если *размер* больше, чем оставшиеся данные, **GetChunk** метод возвращает только оставшиеся данные без заполнения *переменной* пробелами. Если поле пусто, **GetChunk** метод возвращает значение null.  
  
 Каждое последующее **GetChunk** вызов извлекает данные, начиная с которого предыдущего **GetChunk** вызов остановились. Тем не менее если необходимо извлечь данные из одного поля и затем устанавливать или считывать значение другого поля в текущей записи, ADO предполагается, что вы изучили, извлечение данных из первого поля. При вызове метода **GetChunk** метод на первое поле, ADO интерпретирует как новый вызов **GetChunk** операции и начинает чтение с самого начала данных. Доступ к полям в других [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекты, не являющиеся клонов первого **набор записей** объекта не приведет к нарушению **GetChunk** операций.  
  
 Если **adFldLong** бит в [атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md) свойство **поле** присваивается **True**, можно использовать **GetChunk**  метод для этого поля.  
  
 Если имеется текущая запись, при использовании **GetChunk** метод **поле** объекта, возникает ошибка 3021 (текущая запись).  
  
> [!NOTE]
>  **GetChunk** метод не работает на **поле** объектов [записи](../../../ado/reference/ado-api/record-object-ado.md) объекта. Он не осуществляет никаких операций и приведет к ошибке времени выполнения.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры AppendChunk и GetChunk методы (Visual Basic)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vb.md)   
 [Примеры AppendChunk и GetChunk методы (Visual C++)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vc.md)   
 [Метод AppendChunk (ADO)](../../../ado/reference/ado-api/appendchunk-method-ado.md)   
 [Свойство Attributes (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
