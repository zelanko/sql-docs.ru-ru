---
description: Метод Append (коллекция Tables ADOX)
title: Метод Append (таблицы ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Tables::Append
- Tables::raw_Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: a362ed51-314c-4783-9598-538dbf755f3d
author: rothja
ms.author: jroth
ms.openlocfilehash: ffd2ef32cae3fafb7179568d1342606d32236657
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88985475"
---
# <a name="append-method-adox-tables"></a>Метод Append (коллекция Tables ADOX)
Добавляет новый объект [Table](./table-object-adox.md) в коллекцию [Tables](./tables-collection-adox.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Tables.Append Table  
```  
  
#### <a name="parameters"></a>Параметры  
 *Таблица*  
 Значение **типа Variant** , содержащее ссылку на **таблицу** для добавления или имя таблицы для создания и добавления.  
  
## <a name="remarks"></a>Remarks  
 Если поставщик не поддерживает создание таблиц, возникнет ошибка.  
  
## <a name="applies-to"></a>Применение  
 [Коллекция Tables (ADOX)](./tables-collection-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Методы добавления столбцов и таблиц, пример свойства Name (Visual Basic)](./columns-and-tables-append-methods-name-property-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](./parentcatalog-property-example-vb.md)   
 [Метод Append (столбцы ADOX)](./append-method-adox-columns.md)   
 [Метод Append (группы ADOX)](./append-method-adox-groups.md)   
 [Метод Append (индексы ADOX)](./append-method-adox-indexes.md)   
 [Метод Append (ключи ADOX)](./append-method-adox-keys.md)   
 [Метод Append (процедуры ADOX)](./append-method-adox-procedures.md)   
 [Метод Append (пользователи ADOX)](./append-method-adox-users.md)   
 [Метод Append (коллекция Views ADOX)](./append-method-adox-views.md)