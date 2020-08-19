---
description: Свойство ChildCount (многомерные объекты ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 713958259b274e779802828d1940cabf25c5c222
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441206"
---
# <a name="childcount-property-ado-md"></a>Свойство ChildCount (многомерные объекты ADO)
Указывает количество элементов, для которых текущий объект- [элемент](../../../ado/reference/ado-md-api/member-object-ado-md.md) является родительским в иерархии.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **длинное** целое число и доступно только для чтения.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **ChildCount** , чтобы получить оценку количества дочерних элементов, которые имеет **элемент** . Фактические дочерние **элементы элемента могут возвращаться** свойством [Children](../../../ado/reference/ado-md-api/children-property-ado-md.md) .  
  
 Для объектов- **членов** из объекта [расположения](../../../ado/reference/ado-md-api/position-object-ado-md.md) максимальное число, возвращаемое, равно 65536. Если фактическое число дочерних элементов превышает 65536, возвращаемое значение по-прежнему будет равно 65536. Таким образом, приложение должно интерпретировать **ChildCount** , равный 65536, как или больше, чем 65536 потомков.  
  
 Для объектов- **членов** из объекта [уровня](../../../ado/reference/ado-md-api/level-object-ado-md.md) используйте свойство « [число](../../../ado/reference/ado-api/count-property-ado.md) коллекций ADO» в коллекции **Children** , чтобы определить точное число дочерних элементов. Определение точного числа дочерних элементов может выполняться очень долго, если количество дочерних элементов в коллекции велико.  
  
## <a name="applies-to"></a>Применение  
 [Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>См. также:  
 [Свойство Children (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/children-property-ado-md.md)   
 [Свойство Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Коллекция Members (многомерные объекты ADO)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)
