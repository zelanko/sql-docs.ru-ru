---
title: Свойство ChildCount (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ChildCount
- Member::ChildCount
helpviewer_keywords:
- ChildCount property [ADO MD]
ms.assetid: 5463be22-ca50-43ea-9c92-468fc8eda280
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a8e6f6a7cb749ff2b22a1f7563b43ce07e060aab
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67911556"
---
# <a name="childcount-property-ado-md"></a>Свойство ChildCount (многомерные объекты ADO)
Указывает количество элементов, для которых текущий объект- [элемент](../../../ado/reference/ado-md-api/member-object-ado-md.md) является родительским в иерархии.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **длинное** целое число и доступно только для чтения.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **ChildCount** , чтобы получить оценку количества дочерних элементов, которые имеет **элемент** . Фактические дочерние **элементы элемента могут возвращаться** свойством [Children](../../../ado/reference/ado-md-api/children-property-ado-md.md) .  
  
 Для объектов- **членов** из объекта [расположения](../../../ado/reference/ado-md-api/position-object-ado-md.md) максимальное число, возвращаемое, равно 65536. Если фактическое число дочерних элементов превышает 65536, возвращаемое значение по-прежнему будет равно 65536. Таким образом, приложение должно интерпретировать **ChildCount** , равный 65536, как или больше, чем 65536 потомков.  
  
 Для объектов- **членов** из объекта [уровня](../../../ado/reference/ado-md-api/level-object-ado-md.md) используйте свойство « [число](../../../ado/reference/ado-api/count-property-ado.md) коллекций ADO» в коллекции **Children** , чтобы определить точное число дочерних элементов. Определение точного числа дочерних элементов может выполняться очень долго, если количество дочерних элементов в коллекции велико.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Children (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/children-property-ado-md.md)   
 [Свойство Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Коллекция Members (многомерные объекты ADO)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)
