---
title: Объект Procedure (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Procedure
helpviewer_keywords:
- Procedure object [ADOX]
ms.assetid: 927bcf3e-32f5-4a80-98d3-600779f0732e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2c275322fbe65585e100907f25009d2d3e6e0d0f
ms.sourcegitcommit: fc341b2e08937fdd07ea5f4d74a90677fcdac354
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66718848"
---
# <a name="procedure-object-adox"></a>Объект Procedure (ADOX)
Представляет хранимую процедуру. При использовании в сочетании с ADO [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта, **процедуры** объект может использоваться для добавления, удаления или изменения хранимой процедуры.  
  
## <a name="remarks"></a>Примечания  
 **Процедуры** объект позволяет создать хранимую процедуру без необходимости знать или используйте синтаксис «CREATE PROCEDURE» поставщика.  
  
 Со свойствами данного объекта **процедуры** объекта, вы можете:  
  
-   Определения процедуры с [имя](../../../ado/reference/adox-api/name-property-adox.md) свойство.  
  
-   Укажите ADO **команда** объект, который может использоваться для создания или выполнения процедуры с [команда](../../../ado/reference/adox-api/command-property-adox.md) свойство.  
  
-   Возвращает сведения о дате с [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md) и [DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md) свойства.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события объекта Procedure](../../../ado/reference/adox-api/procedure-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Команды и свойства CommandText (Visual Basic)](../../../ado/reference/adox-api/command-and-commandtext-properties-example-vb.md)   
 [Примеры коллекции Parameters, команда свойства (Visual Basic)](../../../ado/reference/adox-api/parameters-collection-command-property-example-vb.md)   
 [Процедуры добавления пример метода (Visual Basic)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Процедуры удаления пример метода (Visual Basic)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Коллекция Procedures (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)
