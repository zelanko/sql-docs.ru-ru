---
description: Метод Append (коллекция Procedures ADOX)
title: Метод Append (процедуры ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 2bc35ccb48211f6a849dc102ba2d1806a79b2426
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88985465"
---
# <a name="append-method-adox-procedures"></a>Метод Append (коллекция Procedures ADOX)
Добавляет новый объект [процедуры](./procedure-object-adox.md) в коллекцию [процедур](./procedures-collection-adox.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Procedures.Append Name, Command  
```  
  
#### <a name="parameters"></a>Параметры  
 *имя*;  
 **Строковое** значение, указывающее имя создаваемой и добавляемой процедуры.  
  
 *Команда*  
 Объект [команды](../ado-api/command-object-ado.md) ADO, представляющий процедуру, которую необходимо создать и добавить.  
  
## <a name="remarks"></a>Remarks  
 Создает новую процедуру в источнике данных с именем и атрибутами, указанными в объекте **Command** .  
  
 Если текст команды, который указывает пользователь, представляет представление, а не процедуру, то поведение зависит от используемого поставщика. Если поставщик не поддерживает хранимые команды, **Добавление** завершится ошибкой.  
  
> [!NOTE]
>  При использовании поставщика OLE DB для Microsoft Jet метод **append** коллекции **процедур** позволяет указать **представление** , а не **процедуру** в параметре *команды* . **Представление** будет добавлено в источник данных и будет добавлено в коллекцию **процедур** . После **добавления**, если коллекции **процедур** и **представлений** обновляются, **представление** больше не будет находиться в коллекции **процедур** и будет отображаться в коллекции **представлений** .  
  
## <a name="applies-to"></a>Применение  
 [Коллекция Procedures (ADOX)](./procedures-collection-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода Append для процедур (Visual Basic)](./procedures-append-method-example-vb.md)   
 [Метод Append (столбцы ADOX)](./append-method-adox-columns.md)   
 [Метод Append (группы ADOX)](./append-method-adox-groups.md)   
 [Метод Append (индексы ADOX)](./append-method-adox-indexes.md)   
 [Метод Append (ключи ADOX)](./append-method-adox-keys.md)   
 [Метод Append (таблицы ADOX)](./append-method-adox-tables.md)   
 [Метод Append (пользователи ADOX)](./append-method-adox-users.md)   
 [Метод Append (коллекция Views ADOX)](./append-method-adox-views.md)