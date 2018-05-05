---
title: Append-метод (ADOX индексы) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Indexes::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 6695769f-275b-4b70-81bd-1a5f7d74926c
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b25f75f89181f2020238f3a113b7a9908c6a88d9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="append-method-adox-indexes"></a>Append-метод (ADOX индексы)
Добавляет новый [индекс](../../../ado/reference/adox-api/index-object-adox.md) объект [индексы](../../../ado/reference/adox-api/indexes-collection-adox.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Indexes.Append Index [,Columns]  
```  
  
#### <a name="parameters"></a>Параметры  
 *Index*  
 **Индекс** добавляемый объект или имя индекса для создания и добавления.  
  
 *Столбцы*  
 Необязательно. Объект **Variant** значение, указывающее имена столбцов для индексирования. *Столбцы* параметр соответствует параметру со значениями [имя](../../../ado/reference/adox-api/name-property-adox.md) свойство [столбца](../../../ado/reference/adox-api/column-object-adox.md) объекта или объектов.  
  
## <a name="remarks"></a>Замечания  
 *Столбцы* параметр может принимать либо имя столбца или массива имен столбцов.  
  
 Если поставщик не поддерживает создание индексов, произойдет ошибка.  
  
## <a name="applies-to"></a>Объект применения  
 [Коллекция Indexes (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Индексы Append пример метода (Visual Basic)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [Append-метод (ADOX столбцы)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-метод (ADOX группы)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-метод (ADOX ключи)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-метод (ADOX процедур)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-метод (ADOX таблицы)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append-метод (ADOX пользователей)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Метод Append (коллекция Views ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
