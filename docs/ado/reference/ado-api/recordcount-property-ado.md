---
title: "Свойство RecordCount (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::RecordCount
- Recordset15::GetRecordCount
- Recordset15::get_RecordCount
helpviewer_keywords: RecordCount property [ADO]
ms.assetid: 834f0121-394a-44d4-ad7d-999b43a6fe63
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 950b53501f84bdaebc1cdc0ce554d13860d894bd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="recordcount-property-ado"></a>Свойство RecordCount (ADO)
Указывает количество записей в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **длинные** значение, указывающее количество записей в **записей**.  
  
## <a name="remarks"></a>Замечания  
 Используйте **RecordCount** , свойство, чтобы узнать, сколько записей в **записей** объекта. Свойство возвращает значение -1, если ADO не удается определить число записей или если тип поставщика или курсор не поддерживает **RecordCount**. Чтение **RecordCount** свойство для закрытого **записей** приводит к ошибке.  
  
 Если **записей** объект поддерживает приблизительное позиционирование или закладки??? то есть **(adApproxPosition) поддерживает** или **(adBookmark) поддерживает**соответственно, возвращают **True**код Это значение будет точное число записей в **записей**независимо от того, является ли он полностью заполнен. Если **записей** объект не поддерживает приблизительное позиционирования, это свойство может быть значительно пустой тратой ресурсов, так как все записи должны быть получены и подсчитаны для возврата точный **RecordCount** значение.  
  
> [!NOTE]
>  В версиях ADO 2.8 и более ранних версий, поставщик SQLOLEDB выбирает все записи, если используется серверный курсор, несмотря на то что он возвращает **True** для обоих **(adApproxPosition) поддерживает** и **(AdBookmark) поддерживает**.  
  
 Тип курсора **записей** объекта влияет ли можно определить количество записей. **RecordCount** свойство будет возвращать значение -1 для однонаправленного курсора; Фактический подсчет для статического или курсор набора ключей; и -1 или фактический подсчет для динамический курсор, в зависимости от источника данных.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Фильтр и пример RecordCount свойства (Visual Basic)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vb.md)   
 [Фильтр и пример использования свойств RecordCount (VC ++)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vc.md)   
 [Свойство AbsolutePosition (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)   
 [Свойство PageCount (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)
