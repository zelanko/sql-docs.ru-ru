---
title: "Объект процедуры (ADOX) | Документы Microsoft"
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
- Procedure
helpviewer_keywords:
- Procedure object [ADOX]
ms.assetid: 927bcf3e-32f5-4a80-98d3-600779f0732e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 225a864f43c9da7d67de58482f632b914822bd1b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="procedure-object-adox"></a>Объект процедуры (ADOX)
Представляет хранимую процедуру. При использовании в сочетании с ADO [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта, **процедура** объект может использоваться для добавления, удаления или изменения хранимой процедуры.  
  
## <a name="remarks"></a>Замечания  
 **Процедура** позволяет создать хранимую процедуру без необходимости знать или используйте синтаксис «CREATE PROCEDURE» поставщика.  
  
 С помощью свойств **процедура** объекта, вы можете:  
  
-   Определения процедуры с [имя](../../../ado/reference/adox-api/name-property-adox.md) свойства.  
  
-   Укажите ADO **команда** объекта, который может использоваться для создания или выполнения процедуры с [команда](../../../ado/reference/adox-api/command-property-adox.md) свойство.  
  
-   Возвращает сведения о дате с [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md) и [DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md) свойства.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Процедуры свойств объекта, методы и события](../../../ado/reference/adox-api/procedure-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Команда и пример свойства CommandText (Visual Basic)](../../../ado/reference/adox-api/command-and-commandtext-properties-example-vb.md)   
 [Коллекция параметров, пример команды свойства (Visual Basic)](../../../ado/reference/adox-api/parameters-collection-command-property-example-vb.md)   
 [Процедуры добавления пример метода (Visual Basic)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Процедуры удаления пример метода (Visual Basic)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Коллекция процедур (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)
