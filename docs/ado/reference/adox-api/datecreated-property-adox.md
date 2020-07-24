---
title: Свойство DateCreated (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Table::get_DateCreated
- _Table::DateCreated
- _Table::GetDateCreated
helpviewer_keywords:
- DateCreated property [ADOX]
ms.assetid: 2bf4b00d-045c-444e-8af7-8af6297ed418
author: rothja
ms.author: jroth
ms.openlocfilehash: 2a94ea4d86d727bc2258b853285eaa7ebc1e48bc
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942437"
---
# <a name="datecreated-property-adox"></a>Свойство DateCreated (ADOX)
Указывает дату создания объекта.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает значение **типа Variant** , указывающее дату создания. Значение равно null, если **DateCreated** не поддерживается поставщиком.  
  
## <a name="remarks"></a>Комментарии  
 Для вновь добавляемых объектов свойство **DateCreated** имеет значение null. После добавления нового [представления](../../../ado/reference/adox-api/view-object-adox.md) или [процедуры](../../../ado/reference/adox-api/procedure-object-adox.md)необходимо вызвать метод [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) коллекции [представлений](../../../ado/reference/adox-api/views-collection-adox.md) или [процедур](../../../ado/reference/adox-api/procedures-collection-adox.md) , чтобы получить значения для свойства **DateCreated** .  
  
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

## <a name="see-also"></a>См. также  
 [Примеры свойств DateCreated и DateModified (Visual Basic)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [Свойство DateModified (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md)
