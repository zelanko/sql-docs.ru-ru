---
title: Коллекция Views (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Catalog::Views
- Views
helpviewer_keywords:
- Views collection [ADOX]
ms.assetid: a55d380c-2b7b-4b57-af74-8ba0b3de0db9
author: rothja
ms.author: jroth
ms.openlocfilehash: 355a18d172939113eb71e58655811a44e89aa7c2
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82752986"
---
# <a name="views-collection-adox"></a>Коллекция Views (ADOX)
Содержит все объекты [представления](../../../ado/reference/adox-api/view-object-adox.md) каталога.  
  
## <a name="remarks"></a>Примечания  
 Метод [append](../../../ado/reference/adox-api/append-method-adox-views.md) для коллекции **views** уникален для ADOX. Можно сделать следующее:  
  
-   Добавьте новое представление в коллекцию с помощью метода **append** .  
  
 Остальные свойства и методы являются стандартными для коллекций ADO. Можно сделать следующее:  
  
-   Доступ к представлению в коллекции со свойством [Item](../../../ado/reference/ado-api/item-property-ado.md) .  
  
-   Возвращает количество представлений, содержащихся в коллекции, с помощью свойства [Count](../../../ado/reference/ado-api/count-property-ado.md) .  
  
-   Удалите представление из коллекции с помощью метода [Delete](../../../ado/reference/adox-api/delete-method-adox-collections.md) .  
  
-   Обновите объекты в коллекции, чтобы отразить текущую схему базы данных методом [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) .  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события коллекции Views](../../../ado/reference/adox-api/views-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример представлений и коллекций полей (Visual Basic)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Пример метода Append для представлений (Visual Basic)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Пример коллекции Views, свойство CommandText (Visual Basic)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Пример метода Delete представлений (Visual Basic)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Пример метода Refresh для представлений (Visual Basic)](../../../ado/reference/adox-api/views-refresh-method-example-vb.md)   
 [Объект каталога (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Объект View (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)
