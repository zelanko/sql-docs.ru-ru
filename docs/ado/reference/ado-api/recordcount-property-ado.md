---
title: Свойство RecordCount (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::RecordCount
- Recordset15::GetRecordCount
- Recordset15::get_RecordCount
helpviewer_keywords:
- RecordCount property [ADO]
ms.assetid: 834f0121-394a-44d4-ad7d-999b43a6fe63
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7c2a7900d47b2e80227e470219fd7a7566dc41e4
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="recordcount-property-ado"></a>Свойство RecordCount (ADO)

Указывает количество записей в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.
  
## <a name="return-value"></a>Возвращаемое значение

Возвращает **длинные** значение, указывающее количество записей в **записей**.
  
## <a name="remarks"></a>Замечания

Используйте **RecordCount** , свойство, чтобы узнать, сколько записей в **записей** объекта. Свойство возвращает значение -1, если ADO не удается определить число записей или если тип поставщика или курсор не поддерживает **RecordCount**. Чтение **RecordCount** свойство для закрытого **записей** приводит к ошибке.

#### <a name="bookmarks-or-approximate-positioning"></a>Закладки или приблизительный позиционирования

Если объект Recordset *does* поддерживает либо закладки или приблизительного позиционирования, это свойство возвращает точное число записей в наборе записей. Это свойство возвращает точное число независимо от того, является ли набор записей был полностью заполнен.

Напротив, если объект набора записей не *не* поддерживает закладки и приблизительное позиционирования, доступ к этому свойству может быть пустой тратой значительных ресурсов. Стока возникает, поскольку все записи, необходимо получить и подсчитаны для возврата точного значения RecordCount.

- **adBookmark** связанные с закладки.
- **adApproxPosition** относится к приблизительное позиционирования.

> [!NOTE]
> В версиях ADO 2.8 и более ранних версий, поставщик SQLOLEDB выбирает все записи, если используется серверный курсор, несмотря на то что он возвращает **True** для обоих **(adApproxPosition) поддерживает** и **(AdBookmark) поддерживает**.
  
Тип курсора **записей** объекта влияет ли можно определить количество записей. **RecordCount** свойство будет возвращать значение -1 для однонаправленного курсора; Фактический подсчет для статического или курсор набора ключей; и -1 или фактический подсчет для динамический курсор, в зависимости от источника данных.
  
## <a name="applies-to"></a>Объект применения

[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также

[Фильтр и пример RecordCount свойства (Visual Basic)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vb.md)   
[Фильтр и пример использования свойств RecordCount (VC ++)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vc.md)   
[Свойство AbsolutePosition (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)   
[Свойство PageCount (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)
