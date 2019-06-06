---
title: Просмотр объекта (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- View
helpviewer_keywords:
- View object [ADOX]
ms.assetid: 653421ce-7b94-43d0-9bc6-4900f8f2af45
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d87b56716ed1876acc6ac139e7804036d5cdfb86
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66718809"
---
# <a name="view-object-adox"></a>Объект View (ADOX)
Представляет отфильтрованный набор записей или виртуальную таблицу. При использовании в сочетании с ADO [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта, **представление** объект может использоваться для добавления, удаления или изменения представления.  
  
## <a name="remarks"></a>Примечания  
 Представление — это виртуальная таблица, созданные из других таблиц базы данных или представления. **Представление** объекта позволяет создавать представления без необходимости знать или используйте синтаксис «Создание ПРЕДСТАВЛЕНИЯ» поставщика.  
  
 Со свойствами данного объекта **представление** объекта, вы можете:  
  
-   Определить представление с [имя](../../../ado/reference/adox-api/name-property-adox.md) свойство.  
  
-   Укажите ADO **команда** объект, который можно использовать для добавления, удаления или изменения представлений с помощью [команда](../../../ado/reference/adox-api/command-property-adox.md) свойство.  
  
-   Возвращает сведения о дате с [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md) и [DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md) свойства.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события объекта View](../../../ado/reference/adox-api/view-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Представления и коллекции полей (Visual Basic)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Представления метода пример Append (Visual Basic)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Коллекция Views, пример свойства CommandText (Visual Basic)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Delete коллекции Views пример метода (Visual Basic)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Коллекция Views (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
