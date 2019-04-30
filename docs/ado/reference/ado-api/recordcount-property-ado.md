---
title: Свойство RecordCount (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::RecordCount
- Recordset15::GetRecordCount
- Recordset15::get_RecordCount
helpviewer_keywords:
- RecordCount property [ADO]
ms.assetid: 834f0121-394a-44d4-ad7d-999b43a6fe63
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fa6f29c480244919de71d06cf3d56e672f00c47f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63240062"
---
# <a name="recordcount-property-ado"></a>Свойство RecordCount (ADO)

Указывает количество записей в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.
  
## <a name="return-value"></a>Возвращаемое значение

Возвращает **Long** значение, указывающее количество записей в **записей**.
  
## <a name="remarks"></a>Примечания

Используйте **RecordCount** свойство, чтобы узнать, сколько записей находятся в **записей** объекта. Свойство возвращает -1, если ADO не удается определить число записей или если тип поставщика или курсор не поддерживает **RecordCount**. Чтение **RecordCount** закрытого свойства **записей** приводит к ошибке.

#### <a name="bookmarks-or-approximate-positioning"></a>Закладки или приблизительное расположение

Если объект Recordset *does* поддерживает либо закладки или приблизительно определить расположение, это свойство возвращает точное число записей в наборе записей. Это свойство возвращает точное значение независимо от того, является ли полностью заполнен набор записей.

Напротив, если объект Recordset *не* поддерживает закладки и приблизительное расположение, доступ к этому свойству может быть значительно тратой ресурсов. Утечка происходит, так как все записи необходимо получить и подсчитаны для возврата точное значение RecordCount.

- **adBookmark** связанные с закладки.
- **adApproxPosition** относится к Приблизительное расположение.

> [!NOTE]
> В версиях ADO 2.8 и более ранних версий поставщика SQLOLEDB извлекает все записи при использовании серверного курсора, несмотря на тот факт, что он возвращает **True** для обоих **(adApproxPosition) поддерживает** и **Поддерживает (adBookmark)**.
  
Тип курсора **записей** ли количество записей, можно определить, влияет на объект. **RecordCount** свойство возвратит значение -1 для однонаправленного курсора; фактическое число для статического или курсор набора ключей; и либо значение -1 или фактическое число к динамическому курсору, в зависимости от источника данных.
  
## <a name="applies-to"></a>Объект применения

[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также

[Filter и RecordCount свойства (Visual Basic)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vb.md)   
[Filter и RecordCount свойства (Visual C++)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vc.md)   
[Свойство AbsolutePosition (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)   
[Свойство PageCount (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)
