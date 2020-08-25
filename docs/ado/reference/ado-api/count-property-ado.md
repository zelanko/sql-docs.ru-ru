---
description: Свойство Count (ADO)
title: Свойство Count (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Collection::Count
helpviewer_keywords:
- Count property [ADO]
ms.assetid: da9ccd1f-d402-41a2-940c-45556fc5340d
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f821642915bdb01e67f673fab871df0541c63ad
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775693"
---
# <a name="count-property-ado"></a>Свойство Count (ADO)
Указывает количество объектов в коллекции.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение **типа Long** .  
  
## <a name="remarks"></a>Remarks  
 Для определения количества объектов в заданной коллекции используется свойство **Count** .  
  
 Поскольку нумерация элементов коллекции начинается с нуля, всегда следует создавать циклы кода, начиная с нуля и заканчивая значением свойства **Count** минус 1. Если вы используете Microsoft Visual Basic и хотите перебрать элементы коллекции, не проверяя свойство **Count** , используйте оператор **For Each... Следующая** команда.  
  
 Если свойство **Count** равно нулю, в коллекции отсутствуют объекты.  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Коллекция Axes (многомерные объекты ADO)](../ado-md-api/axes-collection-ado-md.md)  
        [Коллекция Columns (ADOX)](../adox-api/columns-collection-adox.md)  
        [Коллекция CubeDefs (многомерные объекты ADO)](../ado-md-api/cubedefs-collection-ado-md.md)  
        [Коллекция Dimensions (многомерные объекты ADO)](../ado-md-api/dimensions-collection-ado-md.md)  
        [Коллекция Errors (ADO)](./errors-collection-ado.md)  
        [Коллекция Fields (ADO)](./fields-collection-ado.md)  
        [Коллекция Groups (ADOX)](../adox-api/groups-collection-adox.md)  
    :::column-end:::
    :::column:::
        [Коллекция Hierarchies (многомерные объекты ADO)](../ado-md-api/hierarchies-collection-ado-md.md)  
        [Коллекция Indexes (ADOX)](../adox-api/indexes-collection-adox.md)  
        [Коллекция Keys (ADOX)](../adox-api/keys-collection-adox.md)  
        [Коллекция Levels (многомерные объекты ADO)](../ado-md-api/levels-collection-ado-md.md)  
        [Коллекция Members (многомерные объекты ADO)](../ado-md-api/members-collection-ado-md.md)  
        [Коллекция Parameters (ADO)](./parameters-collection-ado.md)  
    :::column-end:::
    :::column:::
        [Коллекция Positions (многомерные объекты ADO)](../ado-md-api/positions-collection-ado-md.md)  
        [Коллекция Procedures (ADOX)](../adox-api/procedures-collection-adox.md)  
        [Коллекция Properties (ADO)](./properties-collection-ado.md)  
        [Коллекция Tables (ADOX)](../adox-api/tables-collection-adox.md)  
        [Коллекция Users (ADOX)](../adox-api/users-collection-adox.md)  
        [Коллекция Views (ADOX)](../adox-api/views-collection-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также  
 [Пример свойства Count (Visual Basic)](./count-property-example-vb.md)   
 [Пример свойства Count (Visual c++)](./count-property-example-vc.md)   
 [Метод Refresh (ADO)](./refresh-method-ado.md)