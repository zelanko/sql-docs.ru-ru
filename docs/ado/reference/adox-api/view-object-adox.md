---
title: "Просмотр объекта (ADOX) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- View
helpviewer_keywords:
- View object [ADOX]
ms.assetid: 653421ce-7b94-43d0-9bc6-4900f8f2af45
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a9b3b61a1874528ab6bf649bc62a0c5114148691
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="view-object-adox"></a>Объект представления (ADOX)
Представляет отфильтрованного набора записей или виртуальную таблицу. При использовании в сочетании с ADO [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта, **представление** объект может использоваться для добавления, удаления или изменения представления.  
  
## <a name="remarks"></a>Замечания  
 Представление — это виртуальная таблица, созданные из других таблиц базы данных или представления. **Представление** позволяет создать представление без необходимости знать или с помощью синтаксиса «Создать ПРЕДСТАВЛЕНИЕ» поставщика.  
  
 С помощью свойств **представление** объекта, вы можете:  
  
-   Определить представление с [имя](../../../ado/reference/adox-api/name-property-adox.md) свойства.  
  
-   Укажите ADO **команда** объект, который можно использовать для добавления, удаления или изменения представлений с [команда](../../../ado/reference/adox-api/command-property-adox.md) свойство.  
  
-   Возвращает сведения о дате с [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md) и [DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md) свойства.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Просмотреть свойства объекта, методы и события](../../../ado/reference/adox-api/view-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Представления и пример поля коллекций (Visual Basic)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Представления Append пример метода (Visual Basic)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Коллекция представлений, пример свойства CommandText (Visual Basic)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Представления удаления пример метода (Visual Basic)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Коллекции представлений (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)

