---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f1175d2a70c376e3da1e079e4a3eb93a39235758
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67938462"
---
# <a name="drilleddown-property-ado-md"></a>Свойство DrilledDown (многомерные объекты ADO)
Указывает, следуют ли потомки непосредственно за [элементом](../../../ado/reference/ado-md-api/member-object-ado-md.md) на оси.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **логическое** значение и доступно только для чтения. **Дрилледдовн** возвращает **значение true** , если на оси отсутствуют дочерние элементы текущего элемента. **Дрилледдовн** возвращает **значение false** , если текущий элемент содержит один или несколько дочерних элементов на оси.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **дрилледдовн** , чтобы определить, существует ли по меньшей мере один дочерний элемент этого элемента на оси, следующей за данным элементом. Эти сведения полезны при отображении элемента.  
  
 Это свойство поддерживается только для объектов- [членов](../../../ado/reference/ado-md-api/member-object-ado-md.md) , принадлежащих объекту- [положению](../../../ado/reference/ado-md-api/position-object-ado-md.md) . Ошибка возникает, когда на это свойство ссылаются объекты- **члены** , принадлежащие объекту [уровня](../../../ado/reference/ado-md-api/level-object-ado-md.md) .  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>См. также:  
 [Свойство ParentSameAsPrev (многомерные объекты ADO)](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md)
