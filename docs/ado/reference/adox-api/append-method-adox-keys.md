---
title: Метод Append (ключи ADOX) | Документация Майкрософт
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
ms.openlocfilehash: fd66edb75bec4f4b7e35c53c9ebeabd9b3c75d83
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67967298"
---
# <a name="append-method-adox-keys"></a>Метод Append (коллекция Keys ADOX)
Добавляет новый объект [Key](../../../ado/reference/adox-api/key-object-adox.md) в коллекцию [Keys](../../../ado/reference/adox-api/keys-collection-adox.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Keys.Append Key [,KeyType] [,Column] [,RelatedTable] [,RelatedColumn]  
```  
  
#### <a name="parameters"></a>Параметры  
 *Key*  
 Добавляемый объект **Key** или имя создаваемого и добавляемого ключа.  
  
 *KeyType*  
 Необязательный параметр. Значение типа **Long** , указывающее тип ключа. Параметр *Key* соответствует свойству [Type](../../../ado/reference/adox-api/type-property-key-adox.md) **ключевого** объекта.  
  
 *Столбец*  
 Необязательный параметр. **Строковое** значение, указывающее имя индексируемого столбца. Параметр *Columns* соответствует значению свойства [Name](../../../ado/reference/adox-api/name-property-adox.md) объекта [Column](../../../ado/reference/adox-api/column-object-adox.md) .  
  
 *RelatedTable*  
 Необязательный параметр. **Строковое** значение, указывающее имя связанной таблицы. Параметр *RelatedTable* соответствует значению свойства **Name** объекта [Table](../../../ado/reference/adox-api/table-object-adox.md) .  
  
 *RelatedColumn*  
 Необязательный параметр. **Строковое** значение, указывающее имя связанного столбца для внешнего ключа. Параметр *RelatedColumn* соответствует значению свойства **Name** объекта [Column](../../../ado/reference/adox-api/column-object-adox.md) .  
  
## <a name="remarks"></a>Remarks  
 Параметр *Columns* может принимать либо имя столбца, либо массив имен столбцов.  
  
## <a name="applies-to"></a>Применяется к  
 [Коллекция Keys (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойств для добавления ключей, типа ключа, RelatedColumn, RelatedTable и UpdateRule (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Метод Append (столбцы ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Метод Append (группы ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Метод Append (индексы ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Метод Append (процедуры ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Метод Append (таблицы ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Метод Append (пользователи ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Метод Append (коллекция Views ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
