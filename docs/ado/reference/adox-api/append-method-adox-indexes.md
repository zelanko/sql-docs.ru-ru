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
manager: craigg
ms.openlocfilehash: 18e9162c3c9a1b79c28ca6e0ae94f8680db0ac80
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47632252"
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
 Необязательный параметр. Объект **Variant** значение, указывающее имена столбцов для индексирования. *Столбцы* параметр соответствует параметру значения [имя](../../../ado/reference/adox-api/name-property-adox.md) свойство [столбец](../../../ado/reference/adox-api/column-object-adox.md) объекта или объектов.  
  
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
