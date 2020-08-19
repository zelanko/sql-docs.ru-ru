---
description: Объект Key (ADOX)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: d622adac64a37d956fc71ee1399c2d147b2f993a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439866"
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
