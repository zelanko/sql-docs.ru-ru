---
title: Ключ объекта (ADOX) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Key
helpviewer_keywords:
- Key object [ADOX]
ms.assetid: 55f116fe-4d56-4892-bffe-0cdd6fc727c9
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 07b51f604cd8099d3b11f7e748199dfe6a438abd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
-   [Свойства, методы и события объекта Key](../../../ado/reference/adox-api/key-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Ключи добавить метод, тип ключа, RelatedColumn, RelatedTable и UpdateRule-пример свойства (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Коллекция столбцов (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Коллекция Keys (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)
