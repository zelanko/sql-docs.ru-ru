---
description: Коллекция Views (ADOX)
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
ms.openlocfilehash: aaf12e802e41b2dab638858eb2a08aacc3140ab6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439316"
---
# <a name="views-collection-adox"></a>Коллекция Views (ADOX)
Содержит все объекты [представления](../../../ado/reference/adox-api/view-object-adox.md) каталога.  
  
## <a name="remarks"></a>Remarks  
 Метод [append](../../../ado/reference/adox-api/append-method-adox-views.md) для коллекции **views** уникален для ADOX. Вы можете:  
  
-   Добавьте новое представление в коллекцию с помощью метода **append** .  
  
 Остальные свойства и методы являются стандартными для коллекций ADO. Вы можете:  
  
-   Доступ к представлению в коллекции со свойством [Item](../../../ado/reference/ado-api/item-property-ado.md) .  
  
-   Возвращает количество представлений, содержащихся в коллекции, с помощью свойства [Count](../../../ado/reference/ado-api/count-property-ado.md) .  
  
-   Удалите представление из коллекции с помощью метода [Delete](../../../ado/reference/adox-api/delete-method-adox-collections.md) .  
  
-   Обновите объекты в коллекции, чтобы отразить текущую схему базы данных методом [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) .  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события коллекции Views](../../../ado/reference/adox-api/views-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример представлений и коллекций полей (Visual Basic)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Пример метода Append для представлений (Visual Basic)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Пример коллекции Views, свойство CommandText (Visual Basic)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Пример метода Delete представлений (Visual Basic)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Пример метода Refresh для представлений (Visual Basic)](../../../ado/reference/adox-api/views-refresh-method-example-vb.md)   
 [Объект каталога (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Объект View (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)
