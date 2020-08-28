---
description: Свойство DrilledDown (многомерные объекты ADO)
title: Свойство Дрилледдовн (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 3e20e911eefabdf086c805d8b6cbaa87ea7b76b5
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88986735"
---
# <a name="drilleddown-property-ado-md"></a>Свойство DrilledDown (многомерные объекты ADO)
Указывает, следуют ли потомки непосредственно за [элементом](./member-object-ado-md.md) на оси.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **логическое** значение и доступно только для чтения. **Дрилледдовн** возвращает **значение true** , если на оси отсутствуют дочерние элементы текущего элемента. **Дрилледдовн** возвращает **значение false** , если текущий элемент содержит один или несколько дочерних элементов на оси.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **дрилледдовн** , чтобы определить, существует ли по меньшей мере один дочерний элемент этого элемента на оси, следующей за данным элементом. Эти сведения полезны при отображении элемента.  
  
 Это свойство поддерживается только для объектов- [членов](./member-object-ado-md.md) , принадлежащих объекту- [положению](./position-object-ado-md.md) . Ошибка возникает, когда на это свойство ссылаются объекты- **члены** , принадлежащие объекту [уровня](./level-object-ado-md.md) .  
  
## <a name="applies-to"></a>Применение  
 [Объект Member (многомерные объекты ADO)](./member-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство ParentSameAsPrev (многомерные объекты ADO)](./parentsameasprev-property-ado-md.md)