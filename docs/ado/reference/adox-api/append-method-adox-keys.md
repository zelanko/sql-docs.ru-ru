---
title: Append-метод (коллекция Keys ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Keys::Append
- Keys::raw_Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 215a5391-f422-42ec-99ea-4e6fbb5d3d64
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ea4e06fa790e8a360cfb1254b3064b3b540e7842
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66708345"
---
# <a name="append-method-adox-keys"></a>Метод Append (коллекция Keys ADOX)
Добавляет новый [ключ](../../../ado/reference/adox-api/key-object-adox.md) объект [ключи](../../../ado/reference/adox-api/keys-collection-adox.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Keys.Append Key [,KeyType] [,Column] [,RelatedTable] [,RelatedColumn]  
```  
  
#### <a name="parameters"></a>Параметры  
 *Key*  
 **Ключ** добавляемый объект или имя ключа для создания и добавления.  
  
 *KeyType*  
 Необязательный параметр. Объект **Long** значение, указывающее тип ключа. *Ключ* параметр соответствует параметру [тип](../../../ado/reference/adox-api/type-property-key-adox.md) свойство **ключ** объекта.  
  
 *Столбец*  
 Необязательный. Объект **строка** значение, указывающее имя столбца для индексирования. *Столбцы* параметр соответствует параметру значение [имя](../../../ado/reference/adox-api/name-property-adox.md) свойство [столбец](../../../ado/reference/adox-api/column-object-adox.md) объекта.  
  
 *RelatedTable*  
 Необязательный параметр. Объект **строка** значение, указывающее имя связанной таблицы. *RelatedTable* параметр соответствует параметру значение **имя** свойство [таблицы](../../../ado/reference/adox-api/table-object-adox.md) объекта.  
  
 *RelatedColumn*  
 Необязательный параметр. Объект **строка** значение, указывающее имя связанного столбца для внешнего ключа. *RelatedColumn* параметр соответствует параметру значение **имя** свойство [столбец](../../../ado/reference/adox-api/column-object-adox.md) объекта.  
  
## <a name="remarks"></a>Примечания  
 *Столбцы* параметр может принимать либо имя столбца, либо массив имен столбцов.  
  
## <a name="applies-to"></a>Объект применения  
 [Коллекция Keys (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Append коллекции Keys метод, тип ключа, RelatedColumn, RelatedTable и UpdateRule свойства (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Append-метод (коллекция Columns ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-метод (коллекция Groups ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-метод (коллекция Indexes ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append-метод (коллекция Procedures ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-метод (коллекция Tables ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append-метод (коллекция Users ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Метод Append (коллекция Views ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
