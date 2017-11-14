---
title: "Append-метод (ADOX индексы) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Indexes::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 6695769f-275b-4b70-81bd-1a5f7d74926c
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fb25d4ce8ab95f1311460f67b79a2b2199b96e62
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="append-method-adox-indexes"></a>Append-метод (ADOX индексы)
Добавляет новый [индекс](../../../ado/reference/adox-api/index-object-adox.md) объект [индексы](../../../ado/reference/adox-api/indexes-collection-adox.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Indexes.Append Index [,Columns]  
```  
  
#### <a name="parameters"></a>Параметры  
 *Индекс*  
 **Индекс** добавляемый объект или имя индекса для создания и добавления.  
  
 *Столбцы*  
 Необязательно. Объект **Variant** значение, указывающее имена столбцов для индексирования. *Столбцы* параметр соответствует параметру со значениями [имя](../../../ado/reference/adox-api/name-property-adox.md) свойство [столбца](../../../ado/reference/adox-api/column-object-adox.md) объекта или объектов.  
  
## <a name="remarks"></a>Замечания  
 *Столбцы* параметр может принимать либо имя столбца или массива имен столбцов.  
  
 Если поставщик не поддерживает создание индексов, произойдет ошибка.  
  
## <a name="applies-to"></a>Объект применения  
 [Коллекция индексов (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)  
  
## <a name="see-also"></a>См. также:  
 [Индексы Append пример метода (Visual Basic)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [Append-метод (ADOX столбцы)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-метод (ADOX группы)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-метод (ADOX ключи)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-метод (ADOX процедур)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-метод (ADOX таблицы)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append-метод (ADOX пользователей)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append-метод (ADOX представления)](../../../ado/reference/adox-api/append-method-adox-views.md)

