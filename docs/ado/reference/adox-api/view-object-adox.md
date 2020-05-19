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
author: rothja
ms.author: jroth
ms.openlocfilehash: b468ccc3edc4cc5453b4f08371cd2b4b962f0c72
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82753183"
---
# <a name="view-object-adox"></a>Объект View (ADOX)
Представляет отфильтрованный набор записей или виртуальную таблицу. При использовании в сочетании с объектом [команды](../../../ado/reference/ado-api/command-object-ado.md) ADO объект **View** можно использовать для добавления, удаления или изменения представлений.  
  
## <a name="remarks"></a>Remarks  
 Представление — это виртуальная таблица, созданная из других таблиц или представлений базы данных. Объект **View** позволяет создавать представления, не зная и не используя синтаксис создания представления поставщика.  
  
 Свойства объекта **представления** позволяют:  
  
-   Определяет представление с помощью свойства [Name](../../../ado/reference/adox-api/name-property-adox.md) .  
  
-   Укажите объект **команды** ADO, который может быть использован для добавления, удаления или изменения представлений с помощью свойства [Command](../../../ado/reference/adox-api/command-property-adox.md) .  
  
-   Возвращает сведения о дате с помощью свойств [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md) и [DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md) .  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта View](../../../ado/reference/adox-api/view-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример представлений и коллекций полей (Visual Basic)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Пример метода Append для представлений (Visual Basic)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Пример коллекции Views, свойство CommandText (Visual Basic)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Пример метода Delete представлений (Visual Basic)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Коллекция Views (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
