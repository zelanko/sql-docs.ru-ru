---
title: Ключевой объект (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Key
helpviewer_keywords:
- Key object [ADOX]
ms.assetid: 55f116fe-4d56-4892-bffe-0cdd6fc727c9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f7e405cfdde86a4f19590a87035ff574e1d255c9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67965902"
---
# <a name="key-object-adox"></a>Объект Key (ADOX)
Представляет первичное, внешнее или уникальное ключевое поле из таблицы базы данных.  
  
## <a name="remarks"></a>Remarks  
 Следующий код создает новый **ключ**:  
  
```  
Dim obj As New Key  
```  
  
 Свойства и коллекции **ключевого** объекта позволяют:  
  
-   Найдите ключ со свойством [Name](../../../ado/reference/adox-api/name-property-adox.md) .  
  
-   Определите, является ли ключ первичным, внешним или уникальным с помощью свойства [Type](../../../ado/reference/adox-api/type-property-key-adox.md) .  
  
-   Получите доступ к столбцам базы данных ключа с помощью коллекции [Columns](../../../ado/reference/adox-api/columns-collection-adox.md) .  
  
-   Укажите имя связанной таблицы со свойством [RelatedTable](../../../ado/reference/adox-api/relatedtable-property-adox.md) .  
  
-   Определите действие, выполняемое при удалении или обновлении первичного ключа с помощью свойств [DeleteRule](../../../ado/reference/adox-api/deleterule-property-adox.md) и [UpdateRule](../../../ado/reference/adox-api/updaterule-property-adox.md) .  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Key](../../../ado/reference/adox-api/key-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойств для добавления ключей, типа ключа, RelatedColumn, RelatedTable и UpdateRule (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Коллекция Columns (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Коллекция Keys (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)
