---
title: Append-метод (коллекция Indexes ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7190fa68b8204e6b1cfea68a6571e07fd78a9bbc
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66718959"
---
# <a name="append-method-adox-indexes"></a>Метод Append (коллекция Indexes ADOX)
Добавляет новый [индекс](../../../ado/reference/adox-api/index-object-adox.md) объект [индексы](../../../ado/reference/adox-api/indexes-collection-adox.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Indexes.Append Index [,Columns]  
```  
  
#### <a name="parameters"></a>Параметры  
 *Index*  
 **Индекс** добавляемый объект или имя индекса для создания и добавления.  
  
 *Столбцы*  
 Необязательный. Объект **Variant** значение, указывающее имена столбцов для индексирования. *Столбцы* параметр соответствует параметру значения [имя](../../../ado/reference/adox-api/name-property-adox.md) свойство [столбец](../../../ado/reference/adox-api/column-object-adox.md) объекта или объектов.  
  
## <a name="remarks"></a>Примечания  
 *Столбцы* параметр может принимать либо имя столбца, либо массив имен столбцов.  
  
 Если поставщик не поддерживает создание индексов, произойдет ошибка.  
  
## <a name="applies-to"></a>Объект применения  
 [Коллекция Indexes (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода (Visual Basic) Append](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [Append-метод (коллекция Columns ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-метод (коллекция Groups ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-метод (коллекция Keys ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-метод (коллекция Procedures ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-метод (коллекция Tables ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append-метод (коллекция Users ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Метод Append (коллекция Views ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
