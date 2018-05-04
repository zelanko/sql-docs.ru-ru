---
title: Append-метод (ADOX таблицы) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Tables::Append
- Tables::raw_Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: a362ed51-314c-4783-9598-538dbf755f3d
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e6c474330f68993f41a83b0f34313fe0f7ed4f76
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="append-method-adox-tables"></a>Append-метод (ADOX таблицы)
Добавляет новый [таблицы](../../../ado/reference/adox-api/table-object-adox.md) объект [таблиц](../../../ado/reference/adox-api/tables-collection-adox.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Tables.Append Table  
```  
  
#### <a name="parameters"></a>Параметры  
 *Таблица*  
 Объект **Variant** значение, которое содержит ссылку на **таблицы** для добавления или имя таблицы для создания и добавления.  
  
## <a name="remarks"></a>Замечания  
 Если поставщик не поддерживает создание таблиц, произойдет ошибка.  
  
## <a name="applies-to"></a>Объект применения  
 [Коллекция Tables (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Столбцы и таблицы добавьте методы примера имя свойства (Visual Basic)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Append-метод (ADOX столбцы)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-метод (ADOX группы)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-метод (ADOX индексы)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append-метод (ADOX ключи)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-метод (ADOX процедур)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-метод (ADOX пользователей)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Метод Append (коллекция Views ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
