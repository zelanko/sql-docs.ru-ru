---
title: Свойство DrilledDown (многомерные Объекты ADO) | Документация Майкрософт
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
manager: jroth
ms.openlocfilehash: 83db7cfc6cac6dde34ca8d2a974c9d926ba9f086
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66709444"
---
# <a name="drilleddown-property-ado-md"></a>Свойство DrilledDown (многомерные объекты ADO)
Указывает ли дочерние элементы немедленно следовать [член](../../../ado/reference/ado-md-api/member-object-ado-md.md) на оси.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **логическое** значение и доступен только для чтения. **DrilledDown** возвращает **True** Если нет дочерних элементов текущего элемента по оси. **DrilledDown** возвращает **False** Если текущий элемент имеет один или несколько дочерних элементов по оси.  
  
## <a name="remarks"></a>Примечания  
 Используйте **DrilledDown** свойства, чтобы определить, существует ли хотя бы одного дочернего элемента этот элемент на оси сразу после этого члена. Эта информация полезна при отображении элемента.  
  
 Это свойство поддерживается только в [член](../../../ado/reference/ado-md-api/member-object-ado-md.md) объекты, принадлежащие [позиции](../../../ado/reference/ado-md-api/position-object-ado-md.md) объекта. Произошла ошибка при ссылке на это свойство из **член** объекты, принадлежащие [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md) объекта.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство ParentSameAsPrev (многомерные объекты ADO)](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md)
