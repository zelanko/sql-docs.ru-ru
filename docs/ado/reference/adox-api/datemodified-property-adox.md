---
description: Свойство DateModified (ADOX)
title: Свойство DateModified (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 613dbf829009e4e471844b0d49285817d75316b6
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88984745"
---
# <a name="datemodified-property-adox"></a>Свойство DateModified (ADOX)
Указывает дату последнего изменения объекта.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает значение **типа Variant** , указывающее дату изменения. Значение равно null, если **DateModified** не поддерживается поставщиком.  
  
## <a name="remarks"></a>Remarks  
 Для вновь добавляемых объектов свойство **DateModified** имеет значение null. После добавления нового [представления](./view-object-adox.md) или [процедуры](./procedure-object-adox.md)необходимо вызвать метод [Refresh](../ado-api/refresh-method-ado.md) коллекции [представлений](./views-collection-adox.md) или [процедур](./procedures-collection-adox.md) , чтобы получить значения для свойства **DateModified** .  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Procedure (ADOX)](./procedure-object-adox.md)  
    :::column-end:::
    :::column:::
        [Объект Table (ADOX)](./table-object-adox.md)  
    :::column-end:::
    :::column:::
        [Объект View (ADOX)](./view-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также  
 [Примеры свойств DateCreated и DateModified (Visual Basic)](./datecreated-and-datemodified-properties-example-vb.md)   
 [Свойство DateCreated (ADOX)](./datecreated-property-adox.md)