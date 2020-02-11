---
title: Метод Append (процедуры ADOX) | Документация Майкрософт
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
ms.openlocfilehash: dd64ba8119db1ecf2d2b621cd202c9f700b53475
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67967283"
---
# <a name="append-method-adox-procedures"></a>Метод Append (коллекция Procedures ADOX)
Добавляет новый объект [процедуры](../../../ado/reference/adox-api/procedure-object-adox.md) в коллекцию [процедур](../../../ado/reference/adox-api/procedures-collection-adox.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Procedures.Append Name, Command  
```  
  
#### <a name="parameters"></a>Параметры  
 *Название*  
 **Строковое** значение, указывающее имя создаваемой и добавляемой процедуры.  
  
 *Command*  
 Объект [команды](../../../ado/reference/ado-api/command-object-ado.md) ADO, представляющий процедуру, которую необходимо создать и добавить.  
  
## <a name="remarks"></a>Remarks  
 Создает новую процедуру в источнике данных с именем и атрибутами, указанными в объекте **Command** .  
  
 Если текст команды, который указывает пользователь, представляет представление, а не процедуру, то поведение зависит от используемого поставщика. Если поставщик не поддерживает хранимые команды, **Добавление** завершится ошибкой.  
  
> [!NOTE]
>  При использовании поставщика OLE DB для Microsoft Jet метод **append** коллекции **процедур** позволяет указать **представление** , а не **процедуру** в параметре *команды* . **Представление** будет добавлено в источник данных и будет добавлено в коллекцию **процедур** . После **добавления**, если коллекции **процедур** и **представлений** обновляются, **представление** больше не будет находиться в коллекции **процедур** и будет отображаться в коллекции **представлений** .  
  
## <a name="applies-to"></a>Применяется к  
 [Коллекция Procedures (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример метода Append для процедур (Visual Basic)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Метод Append (столбцы ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Метод Append (группы ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Метод Append (индексы ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Метод Append (ключи ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Метод Append (таблицы ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Метод Append (пользователи ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Метод Append (коллекция Views ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
