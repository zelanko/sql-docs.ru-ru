---
description: Коллекция Procedures (ADOX)
title: Коллекция процедур (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Procedures
- Catalog::Procedures
helpviewer_keywords:
- Procedures collection [ADOX]
ms.assetid: dc7a38e1-93b9-4034-9af2-ff419e8fb2a3
author: rothja
ms.author: jroth
ms.openlocfilehash: 97421c9020750627dcd27f6188ae5cda72a2d90c
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88769633"
---
# <a name="procedures-collection-adox"></a>Коллекция Procedures (ADOX)
Содержит все объекты [процедур](./procedure-object-adox.md) каталога.  
  
## <a name="remarks"></a>Remarks  
 Метод [append](./append-method-adox-procedures.md) для коллекции **процедур** уникален для ADOX. Вы можете:  
  
-   Добавьте новую процедуру в коллекцию с помощью метода **append** .  
  
 Остальные свойства и методы являются стандартными для коллекций ADO. Вы можете:  
  
-   Получите доступ к процедуре в коллекции со свойством [Item](../ado-api/item-property-ado.md) .  
  
-   Возвращает количество процедур, содержащихся в коллекции, с помощью свойства [Count](../ado-api/count-property-ado.md) .  
  
-   Удалите процедуру из коллекции с помощью метода [Delete](./delete-method-adox-collections.md) .  
  
-   Обновите объекты в коллекции, чтобы отразить текущую схему базы данных методом [Refresh](../ado-api/refresh-method-ado.md) .  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события коллекции Indexes](./indexes-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойств Command и CommandText (Visual Basic)](./command-and-commandtext-properties-example-vb.md)   
 [Коллекция Parameters, пример свойства Command (Visual Basic)](./parameters-collection-command-property-example-vb.md)   
 [Пример метода Append для процедур (Visual Basic)](./procedures-append-method-example-vb.md)   
 [Пример метода Delete процедур (Visual Basic)](./procedures-delete-method-example-vb.md)   
 [Пример метода обновления процедур (Visual Basic)](./procedures-refresh-method-example-vb.md)   
 [Свойства, методы и события коллекции процедур](./procedures-collection-properties-methods-and-events.md)   
 [Объект каталога (ADOX)](./catalog-object-adox.md)   
 [Объект Procedure (ADOX)](./procedure-object-adox.md)