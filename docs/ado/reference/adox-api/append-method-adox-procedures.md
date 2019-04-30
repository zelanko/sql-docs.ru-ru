---
title: Append-метод (коллекция Procedures ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Procedures::Append
- Procedures::raw_Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 38e3492c-c1e1-42e3-a71a-befdc90204db
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 348b2876e4293ad912383859ace47e462da31bcf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63207181"
---
# <a name="append-method-adox-procedures"></a>Метод Append (коллекция Procedures ADOX)
Добавляет новый [процедуры](../../../ado/reference/adox-api/procedure-object-adox.md) объект [процедуры](../../../ado/reference/adox-api/procedures-collection-adox.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Procedures.Append Name, Command  
```  
  
#### <a name="parameters"></a>Параметры  
 *Name*  
 Объект **строка** значение, указывающее имя процедуры для создания и добавления.  
  
 *Command*  
 ADO [команда](../../../ado/reference/ado-api/command-object-ado.md) объект, который представляет процедуру для создания и добавления.  
  
## <a name="remarks"></a>Примечания  
 Создает новую процедуру в источнике данных с именем и атрибутами, заданными в **команда** объекта.  
  
 Если текст команды, который указывает пользователь представляет представление, а не процедуры, поведение зависит от используемого поставщика. **Добавление** завершится ошибкой, если поставщик не поддерживает сохранение команды.  
  
> [!NOTE]
>  При использовании поставщика OLE DB для Jet (Майкрософт), **процедуры** коллекции **Append** метод позволит вам указать **представление** вместо  **Процедура** в *команда* параметра. **Представление** будут добавляться к источнику данных и добавляется **процедуры** коллекции. После **Append**, если **процедуры** и **представления** обновляются коллекций, **представление** больше не будет в **Процедуры** коллекции и будет отображаться в **представления** коллекции.  
  
## <a name="applies-to"></a>Объект применения  
 [Коллекция Procedures (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Процедуры добавления пример метода (Visual Basic)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Append-метод (коллекция Columns ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-метод (коллекция Groups ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-метод (коллекция Indexes ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append-метод (коллекция Keys ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-метод (коллекция Tables ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append-метод (коллекция Users ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Метод Append (коллекция Views ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
