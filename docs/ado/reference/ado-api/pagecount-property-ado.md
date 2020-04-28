---
title: Свойство PageCount (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::PageCount
helpviewer_keywords:
- PageCount property [ADO]
ms.assetid: b601b56c-0ac4-44ee-bc91-c3d2d104f00a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ea893a019ab6d1333cecc5da5f1f66928467adfc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67931787"
---
# <a name="pagecount-property-ado"></a>Свойство PageCount (ADO)
Указывает, сколько страниц данных содержит объект [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение **типа Long** , указывающее количество страниц в **наборе записей**.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **PageCount** , чтобы определить, сколько страниц данных находится в объекте **Recordset** . *Страницы* — это группы записей, размер которых равен значению свойства [pageSize](../../../ado/reference/ado-api/pagesize-property-ado.md) . Даже если последняя страница является неполной, так как число записей меньше, чем значение **pageSize** , оно считается дополнительной страницей в значении **PageCount** . Если объект **Recordset** не поддерживает это свойство, значение будет равно-1, чтобы указать, что **PageCount** недетерминирована.  
  
 Дополнительные сведения о функциях страницы см. в разделе Свойства **pageSize** и [примеры absolutepage](../../../ado/reference/ado-api/absolutepage-property-ado.md) .  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Примеры свойств примеры absolutepage, PageCount и PageSize (Visual Basic)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [Пример свойств примеры absolutepage, PageCount и PageSize (Visual c++)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [Свойство примеры absolutepage (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [Свойство PageSize (ADO)](../../../ado/reference/ado-api/pagesize-property-ado.md)   
 [Свойство RecordCount (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)
