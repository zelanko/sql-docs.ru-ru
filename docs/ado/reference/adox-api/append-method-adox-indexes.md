---
description: Метод Append (коллекция Indexes ADOX)
title: Метод Append (индексы ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Indexes::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 6695769f-275b-4b70-81bd-1a5f7d74926c
author: rothja
ms.author: jroth
ms.openlocfilehash: 00b37055efe15f204049d02c337b54c228468419
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88985515"
---
# <a name="append-method-adox-indexes"></a>Метод Append (коллекция Indexes ADOX)
Добавляет новый объект [index](./index-object-adox.md) в коллекцию [индексов](./indexes-collection-adox.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Indexes.Append Index [,Columns]  
```  
  
#### <a name="parameters"></a>Параметры  
 *Index*  
 Добавляемый объект **index** или имя создаваемого и добавляемого индекса.  
  
 *Столбцы*  
 Необязательный элемент. Значение **типа Variant** , указывающее имена столбцов, которые будут индексироваться. Параметр *Columns* соответствует значениям свойства [Name](./name-property-adox.md) объекта [Column](./column-object-adox.md) или объектов.  
  
## <a name="remarks"></a>Remarks  
 Параметр *Columns* может принимать либо имя столбца, либо массив имен столбцов.  
  
 Если поставщик не поддерживает создание индексов, возникнет ошибка.  
  
## <a name="applies-to"></a>Применение  
 [Коллекция Indexes (ADOX)](./indexes-collection-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода Append для индексов (Visual Basic)](./indexes-append-method-example-vb.md)   
 [Метод Append (столбцы ADOX)](./append-method-adox-columns.md)   
 [Метод Append (группы ADOX)](./append-method-adox-groups.md)   
 [Метод Append (ключи ADOX)](./append-method-adox-keys.md)   
 [Метод Append (процедуры ADOX)](./append-method-adox-procedures.md)   
 [Метод Append (таблицы ADOX)](./append-method-adox-tables.md)   
 [Метод Append (пользователи ADOX)](./append-method-adox-users.md)   
 [Метод Append (коллекция Views ADOX)](./append-method-adox-views.md)