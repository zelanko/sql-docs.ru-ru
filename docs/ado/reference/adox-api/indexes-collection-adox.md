---
title: Коллекция indexes (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Table::Indexes
- Indexes
helpviewer_keywords:
- Indexes collection [ADOX]
ms.assetid: 184cf536-455c-42be-bf1c-a5c25bade961
author: rothja
ms.author: jroth
ms.openlocfilehash: af209229519470b121e3c69ba857b145c0874e73
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763856"
---
# <a name="indexes-collection-adox"></a>Коллекция Indexes (ADOX)
Содержит все объекты [индекса](../../../ado/reference/adox-api/index-object-adox.md) таблицы.  
  
## <a name="remarks"></a>Примечания  
 Метод [append](../../../ado/reference/adox-api/append-method-adox-indexes.md) для коллекции **индексов** уникален для ADOX. Можно сделать следующее:  
  
-   Добавьте новый индекс в коллекцию с помощью метода **append** .  
  
 Остальные свойства и методы являются стандартными для коллекций ADO. Можно сделать следующее:  
  
-   Доступ к индексу в коллекции со свойством [Item](../../../ado/reference/ado-api/item-property-ado.md) .  
  
-   Возвращает количество индексов, содержащихся в коллекции, со свойством [Count](../../../ado/reference/ado-api/count-property-ado.md) .  
  
-   Удалите индекс из коллекции с помощью метода [Delete](../../../ado/reference/adox-api/delete-method-adox-collections.md) .  
  
-   Обновите объекты в коллекции, чтобы отразить текущую схему базы данных методом [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) .  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события коллекции Indexes](../../../ado/reference/adox-api/indexes-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода Append для индексов (Visual Basic)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [Объект Index (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)
