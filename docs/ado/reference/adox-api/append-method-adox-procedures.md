---
title: "Append-метод (процедуры ADOX) | Документы Microsoft"
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
- Procedures::Append
- Procedures::raw_Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 38e3492c-c1e1-42e3-a71a-befdc90204db
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 679f7691a8f93026ce1f6a68ea232d01818e6dc9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="append-method-adox-procedures"></a>Append-метод (ADOX процедур)
Добавляет новый [процедура](../../../ado/reference/adox-api/procedure-object-adox.md) объект [процедуры](../../../ado/reference/adox-api/procedures-collection-adox.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Procedures.Append Name, Command  
```  
  
#### <a name="parameters"></a>Параметры  
 *Название*  
 Объект **строка** значение, указывающее имя процедуры для создания и добавления.  
  
 *Command*  
 ADO [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта, который представляет процедуру для создания и добавления.  
  
## <a name="remarks"></a>Замечания  
 Создает новую процедуру в источнике данных с именем и атрибутами, заданными в **команда** объекта.  
  
 Если текст команды, который пользователь указывает представляет представление, а не является процедурой, поведение зависит от используемого поставщика. **Добавление** завершится ошибкой, если поставщик не поддерживает сохранение команды.  
  
> [!NOTE]
>  При использовании поставщика OLE DB для Microsoft Jet **процедуры** коллекции **Append** метод дает возможность указать **представление** вместо  **Процедура** в *команда* параметра. **Представление** и добавляются к источнику данных будут добавлены **процедуры** коллекции. После **Append**, если **процедуры** и **представления** обновляются коллекций, **представление** больше не будет в **Процедуры** коллекции и будет отображаться в **представления** коллекции.  
  
## <a name="applies-to"></a>Объект применения  
 [Коллекция процедур (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)  
  
## <a name="see-also"></a>См. также:  
 [Процедуры добавления пример метода (Visual Basic)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Append-метод (ADOX столбцы)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-метод (ADOX группы)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-метод (ADOX индексы)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append-метод (ADOX ключи)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-метод (ADOX таблицы)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append-метод (ADOX пользователей)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append-метод (ADOX представления)](../../../ado/reference/adox-api/append-method-adox-views.md)

