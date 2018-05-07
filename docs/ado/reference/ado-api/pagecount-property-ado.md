---
title: Свойство PageCount (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::PageCount
helpviewer_keywords:
- PageCount property [ADO]
ms.assetid: b601b56c-0ac4-44ee-bc91-c3d2d104f00a
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 31eecabefdc56da6f4a252e974cc8ff97f9190c8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="pagecount-property-ado"></a>Свойство PageCount (ADO)
Показывает, сколько страниц данных [записей](../../../ado/reference/ado-api/recordset-object-ado.md) содержит объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **длинные** значение, указывающее количество страниц в **записей**.  
  
## <a name="remarks"></a>Замечания  
 Используйте **PageCount** свойство, чтобы определить, сколько страниц данных в **записей** объекта. *Страницы* — это группы записи, размер которого равен размеру [PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md) значение свойства. Даже если последняя страница является неполным, поскольку меньше записей, чем **PageSize** значение, он считается дополнительную страницу в **PageCount** значение. Если **записей** объект не поддерживает это свойство, значение будет равно -1, чтобы указать, что **PageCount** невозможно определить.  
  
 В разделе **PageSize** и [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) свойства для дополнительных функциональных возможностей на страницы.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [AbsolutePage, PageCount и пример свойства PageSize (Visual Basic)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [AbsolutePage, PageCount и пример свойства PageSize (VC ++)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [Свойство AbsolutePage (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [Свойства PageSize (ADO)](../../../ado/reference/ado-api/pagesize-property-ado.md)   
 [Свойство RecordCount (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)
