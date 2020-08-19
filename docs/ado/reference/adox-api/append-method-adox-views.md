---
description: Метод Append (коллекция Views ADOX)
title: Метод Append (представления ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Views::raw_Append
- Views::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 6070fd58-3237-4c77-a966-5b39ce5d57e4
author: rothja
ms.author: jroth
ms.openlocfilehash: e022afd65b6ea37eda07f6ddb4d35ab135664a8f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440456"
---
# <a name="append-method-adox-views"></a>Метод Append (коллекция Views ADOX)
Создает новый объект [представления](../../../ado/reference/adox-api/view-object-adox.md) и добавляет его в коллекцию [представлений](../../../ado/reference/adox-api/views-collection-adox.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Views.Append Name, Command  
```  
  
#### <a name="parameters"></a>Параметры  
 *имя*;  
 **Строковое** значение, указывающее имя создаваемого представления.  
  
 *Command*  
 Объект [команды](../../../ado/reference/ado-api/command-object-ado.md) ADO, представляющий создаваемое представление.  
  
## <a name="remarks"></a>Remarks  
 Создает новое представление в источнике данных с именем и атрибутами, указанными в объекте **Command** .  
  
 Если текст команды, который указывает пользователь, представляет процедуру, а не представление, то поведение зависит от поставщика. Если поставщик не поддерживает хранимые команды, **Добавление** завершится ошибкой.  
  
> [!NOTE]
>  При использовании поставщика OLE DB для Microsoft Jet метод **append** коллекции **views** позволяет указать **процедуру** , а не **представление** в параметре *команды* . **Процедура** будет добавлена в источник данных и будет добавлена в коллекцию **представлений** . После **добавления**, если коллекции **процедур** и **представлений** обновляются, **процедура** больше не будет находиться в коллекции **представлений** и будет отображаться в коллекции **процедур** .  
  
## <a name="applies-to"></a>Применение  
 [Коллекция Views (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример метода Append для представлений (Visual Basic)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Метод Append (столбцы ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Метод Append (группы ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Метод Append (индексы ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Метод Append (ключи ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Метод Append (процедуры ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Метод Append (таблицы ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Метод Append (коллекция Users ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)
