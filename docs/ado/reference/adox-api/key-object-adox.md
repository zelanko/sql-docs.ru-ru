---
title: "Ключ объекта (ADOX) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Key
helpviewer_keywords:
- Key object [ADOX]
ms.assetid: 55f116fe-4d56-4892-bffe-0cdd6fc727c9
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7d05a52614694bc9464c609ab4f4ed0965f3b81e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="key-object-adox"></a>Объект ключа (ADOX)
Представляет внешний, первичный или уникальный ключевое поле из таблицы базы данных.  
  
## <a name="remarks"></a>Замечания  
 Следующий код создает новый **ключ**:  
  
```  
Dim obj As New Key  
```  
  
 С помощью свойств и коллекций **ключ** объекта, вы можете:  
  
-   Идентификация ключа с [имя](../../../ado/reference/adox-api/name-property-adox.md) свойства.  
  
-   Определить, является ли ключ первичный, внешний или уникальными [тип](../../../ado/reference/adox-api/type-property-key-adox.md) свойства.  
  
-   Доступ к столбцам базы данных ключа с [столбцы](../../../ado/reference/adox-api/columns-collection-adox.md) коллекции.  
  
-   Укажите имя таблицы, связанные с [RelatedTable](../../../ado/reference/adox-api/relatedtable-property-adox.md) свойство.  
  
-   Определить действие, выполняемое для удаления или обновления первичного ключа с [DeleteRule](../../../ado/reference/adox-api/deleterule-property-adox.md) и [UpdateRule](../../../ado/reference/adox-api/updaterule-property-adox.md) свойства.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Ключевой объект свойства, методы и события](../../../ado/reference/adox-api/key-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Ключи добавить метод, тип ключа, RelatedColumn, RelatedTable и UpdateRule-пример свойства (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Коллекция столбцов (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Коллекция ключей (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)
