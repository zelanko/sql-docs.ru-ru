---
title: Свойство DateModified (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Table::get_DateModified
- _Table::DateModified
- _Table::GetDateModified
helpviewer_keywords:
- DateModified property [ADOX]
ms.assetid: fed09266-1547-4bda-9088-c254d81cc738
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c3a2a8ba0890dd50621fac143aa102091abcc19
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942716"
---
# <a name="datemodified-property-adox"></a>Свойство DateModified (ADOX)
Указывает дату последнего изменения объекта.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает значение **типа Variant** , указывающее дату изменения. Значение равно null, если **DateModified** не поддерживается поставщиком.  
  
## <a name="remarks"></a>Примечания  
 Для вновь добавляемых объектов свойство **DateModified** имеет значение null. После добавления нового [представления](../../../ado/reference/adox-api/view-object-adox.md) или [процедуры](../../../ado/reference/adox-api/procedure-object-adox.md)необходимо вызвать метод [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) коллекции [представлений](../../../ado/reference/adox-api/views-collection-adox.md) или [процедур](../../../ado/reference/adox-api/procedures-collection-adox.md) , чтобы получить значения для свойства **DateModified** .  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Procedure (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)  
    :::column-end:::
    :::column:::
        [Объект Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)  
    :::column-end:::
    :::column:::
        [Объект View (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также:  
 [Примеры свойств DateCreated и DateModified (Visual Basic)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [Свойство DateCreated (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md)
