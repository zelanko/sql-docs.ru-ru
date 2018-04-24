---
title: Append-метод (ADOX ключи) | Документы Microsoft
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
- Keys::Append
- Keys::raw_Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 215a5391-f422-42ec-99ea-4e6fbb5d3d64
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5e8241f1e86a32f8ac768819b43ad0dfece067ce
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="append-method-adox-keys"></a>Append-метод (ADOX ключи)
Добавляет новый [ключ](../../../ado/reference/adox-api/key-object-adox.md) объект [ключей](../../../ado/reference/adox-api/keys-collection-adox.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Keys.Append Key [,KeyType] [,Column] [,RelatedTable] [,RelatedColumn]  
```  
  
#### <a name="parameters"></a>Параметры  
 *Key*  
 **Ключ** добавляемый объект или имя ключа для создания и добавления.  
  
 *KeyType*  
 Необязательно. Объект **длинные** значение, указывающее тип ключа. *Ключ* параметр соответствует параметру [тип](../../../ado/reference/adox-api/type-property-key-adox.md) свойство **ключ** объекта.  
  
 *Столбец*  
 Необязательно. Объект **строка** значение, указывающее имя столбца для индексирования. *Столбцы* параметр соответствует значению [имя](../../../ado/reference/adox-api/name-property-adox.md) свойство [столбца](../../../ado/reference/adox-api/column-object-adox.md) объекта.  
  
 *RelatedTable*  
 Необязательно. Объект **строка** значение, указывающее имя связанной таблицы. *RelatedTable* параметр соответствует значению **имя** свойство [таблицы](../../../ado/reference/adox-api/table-object-adox.md) объекта.  
  
 *RelatedColumn*  
 Необязательно. Объект **строка** значение, указывающее имя связанного столбца для внешнего ключа. *RelatedColumn* параметр соответствует значению **имя** свойство [столбца](../../../ado/reference/adox-api/column-object-adox.md) объекта.  
  
## <a name="remarks"></a>Замечания  
 *Столбцы* параметр может принимать либо имя столбца или массива имен столбцов.  
  
## <a name="applies-to"></a>Объект применения  
 [Коллекция Keys (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Ключи добавить метод, тип ключа, RelatedColumn, RelatedTable и UpdateRule-пример свойства (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Append-метод (ADOX столбцы)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-метод (ADOX группы)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-метод (ADOX индексы)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append-метод (ADOX процедур)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-метод (ADOX таблицы)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append-метод (ADOX пользователей)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Метод Append (коллекция Views ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
