---
title: Метод Append (таблицы ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: 19617c65b350527753895ed613f671c3ac0f88e8
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764015"
---
# <a name="append-method-adox-tables"></a>Метод Append (коллекция Tables ADOX)
Добавляет новый объект [Table](../../../ado/reference/adox-api/table-object-adox.md) в коллекцию [Tables](../../../ado/reference/adox-api/tables-collection-adox.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Tables.Append Table  
```  
  
#### <a name="parameters"></a>Параметры  
 *Таблица*  
 Значение **типа Variant** , содержащее ссылку на **таблицу** для добавления или имя таблицы для создания и добавления.  
  
## <a name="remarks"></a>Примечания  
 Если поставщик не поддерживает создание таблиц, возникнет ошибка.  
  
## <a name="applies-to"></a>Применяется к  
 [Коллекция Tables (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Методы добавления столбцов и таблиц, пример свойства Name (Visual Basic)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Метод Append (столбцы ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Метод Append (группы ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Метод Append (индексы ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Метод Append (ключи ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Метод Append (процедуры ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Метод Append (пользователи ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Метод Append (коллекция Views ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
