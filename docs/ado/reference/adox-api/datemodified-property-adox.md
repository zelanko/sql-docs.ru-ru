---
description: Свойство DateModified (ADOX)
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
ms.openlocfilehash: 7ee921e1865530356e1fd88c97489b63a81a02ec
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440156"
---
# <a name="datemodified-property-adox"></a>Свойство DateModified (ADOX)
Указывает дату последнего изменения объекта.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает значение **типа Variant** , указывающее дату изменения. Значение равно null, если **DateModified** не поддерживается поставщиком.  
  
## <a name="remarks"></a>Remarks  
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
