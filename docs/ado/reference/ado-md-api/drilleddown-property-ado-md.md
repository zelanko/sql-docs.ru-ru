---
description: Свойство DrilledDown (многомерные объекты ADO)
title: Свойство Дрилледдовн (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DrilledDown
- Member::DrilledDown
helpviewer_keywords:
- DrilledDown property [ADO MD]
ms.assetid: bf39dd36-fc7a-4f6e-86c0-fa71430c0d86
author: rothja
ms.author: jroth
ms.openlocfilehash: 132b1a7210a9fd37866f1a150430f0d1a6d29606
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441046"
---
# <a name="drilleddown-property-ado-md"></a>Свойство DrilledDown (многомерные объекты ADO)
Указывает, следуют ли потомки непосредственно за [элементом](../../../ado/reference/ado-md-api/member-object-ado-md.md) на оси.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **логическое** значение и доступно только для чтения. **Дрилледдовн** возвращает **значение true** , если на оси отсутствуют дочерние элементы текущего элемента. **Дрилледдовн** возвращает **значение false** , если текущий элемент содержит один или несколько дочерних элементов на оси.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **дрилледдовн** , чтобы определить, существует ли по меньшей мере один дочерний элемент этого элемента на оси, следующей за данным элементом. Эти сведения полезны при отображении элемента.  
  
 Это свойство поддерживается только для объектов- [членов](../../../ado/reference/ado-md-api/member-object-ado-md.md) , принадлежащих объекту- [положению](../../../ado/reference/ado-md-api/position-object-ado-md.md) . Ошибка возникает, когда на это свойство ссылаются объекты- **члены** , принадлежащие объекту [уровня](../../../ado/reference/ado-md-api/level-object-ado-md.md) .  
  
## <a name="applies-to"></a>Применение  
 [Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>См. также:  
 [Свойство ParentSameAsPrev (многомерные объекты ADO)](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md)
