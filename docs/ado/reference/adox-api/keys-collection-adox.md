---
description: Коллекция Keys (ADOX)
title: Коллекция Keys (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Table::Keys
- Keys
helpviewer_keywords:
- Keys collection [ADOX]
ms.assetid: cdb31c76-e559-475c-b33a-aac24f73e70e
author: rothja
ms.author: jroth
ms.openlocfilehash: 05e36f05cd59cc099abf0b1fa1f96418ccea8bf5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439816"
---
# <a name="keys-collection-adox"></a>Коллекция Keys (ADOX)
Содержит все [Ключевые](../../../ado/reference/adox-api/key-object-adox.md) объекты [таблицы](../../../ado/reference/adox-api/table-object-adox.md).  
  
## <a name="remarks"></a>Remarks  
 Метод [append](../../../ado/reference/adox-api/append-method-adox-keys.md) для [коллекции Keys](../../../ado/reference/adox-api/keys-collection-adox.md) уникален для ADOX. Вы можете:  
  
-   Добавьте новый ключ в коллекцию с помощью метода [append](../../../ado/reference/adox-api/append-method-adox-keys.md) .  
  
 Остальные свойства и методы являются стандартными для коллекций ADO. Вы можете:  
  
-   Доступ к ключу в коллекции со свойством [Item](../../../ado/reference/ado-api/item-property-ado.md) .  
  
-   Возвращает количество ключей, содержащихся в коллекции, со свойством [Count](../../../ado/reference/ado-api/count-property-ado.md) .  
  
-   Удалите ключ из коллекции с помощью метода [Delete](../../../ado/reference/adox-api/delete-method-adox-collections.md) .  
  
-   Обновите объекты в коллекции, чтобы отразить схему текущей базы данных методом [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) .  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события коллекции Indexes](../../../ado/reference/adox-api/indexes-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойств для добавления ключей, типа ключа, RelatedColumn, RelatedTable и UpdateRule (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Свойства, методы и события коллекции Keys](../../../ado/reference/adox-api/keys-collection-properties-methods-and-events.md)   
 [Объект Key (ADOX)](../../../ado/reference/adox-api/key-object-adox.md)
