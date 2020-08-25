---
description: Метод Append (коллекция Keys ADOX)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 6334f4edb0d98e7fa0dca49f1c024f63e471c7f8
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88771433"
---
# <a name="append-method-adox-keys"></a>Метод Append (коллекция Keys ADOX)
Добавляет новый объект [Key](./key-object-adox.md) в коллекцию [Keys](./keys-collection-adox.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Keys.Append Key [,KeyType] [,Column] [,RelatedTable] [,RelatedColumn]  
```  
  
#### <a name="parameters"></a>Параметры  
 *Key*  
 Добавляемый объект **Key** или имя создаваемого и добавляемого ключа.  
  
 *KeyType*  
 Необязательный элемент. Значение типа **Long** , указывающее тип ключа. Параметр *Key* соответствует свойству [Type](./type-property-key-adox.md) **ключевого** объекта.  
  
 *Столбец*  
 Необязательный элемент. **Строковое** значение, указывающее имя индексируемого столбца. Параметр *Columns* соответствует значению свойства [Name](./name-property-adox.md) объекта [Column](./column-object-adox.md) .  
  
 *RelatedTable*  
 Необязательный элемент. **Строковое** значение, указывающее имя связанной таблицы. Параметр *RelatedTable* соответствует значению свойства **Name** объекта [Table](./table-object-adox.md) .  
  
 *RelatedColumn*  
 Необязательный элемент. **Строковое** значение, указывающее имя связанного столбца для внешнего ключа. Параметр *RelatedColumn* соответствует значению свойства **Name** объекта [Column](./column-object-adox.md) .  
  
## <a name="remarks"></a>Remarks  
 Параметр *Columns* может принимать либо имя столбца, либо массив имен столбцов.  
  
## <a name="applies-to"></a>Применение  
 [Коллекция Keys (ADOX)](./keys-collection-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойств для добавления ключей, типа ключа, RelatedColumn, RelatedTable и UpdateRule (Visual Basic)](./keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Метод Append (столбцы ADOX)](./append-method-adox-columns.md)   
 [Метод Append (группы ADOX)](./append-method-adox-groups.md)   
 [Метод Append (индексы ADOX)](./append-method-adox-indexes.md)   
 [Метод Append (процедуры ADOX)](./append-method-adox-procedures.md)   
 [Метод Append (таблицы ADOX)](./append-method-adox-tables.md)   
 [Метод Append (пользователи ADOX)](./append-method-adox-users.md)   
 [Метод Append (коллекция Views ADOX)](./append-method-adox-views.md)