---
title: Append-метод (коллекция Columns ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Columns::raw_Append
- Columns::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 7a46d23c-efef-4ec7-815d-cd3ac86787dd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 98ff605c2fb701f2451e3df4ba2068da6729ff86
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47845292"
---
# <a name="append-method-adox-columns"></a>Метод Append (коллекция Columns ADOX)
Добавляет новый [столбец](../../../ado/reference/adox-api/column-object-adox.md) объект [столбцы](../../../ado/reference/adox-api/columns-collection-adox.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Columns.Append Column [,Type] [,DefinedSize]  
```  
  
#### <a name="parameters"></a>Параметры  
 *Столбец*  
 **Столбец** добавляемый объект или имя столбца для создания и добавления.  
  
 *Тип*  
 Необязательный параметр. Объект **Long** значение, указывающее тип данных столбца. *Тип* параметр соответствует параметру [тип](../../../ado/reference/adox-api/type-property-column-adox.md) свойство **столбец** объекта.  
  
 *DefinedSize*  
 Необязательный параметр. Объект **Long** значение, указывающее размер столбца. *DefinedSize* параметр соответствует параметру [DefinedSize](../../../ado/reference/adox-api/definedsize-property-adox.md) свойство **столбец** объекта.  
  
> [!NOTE]
>  Произойдет ошибка при добавлении **столбец** для **столбцы** коллекцию [индекс](../../../ado/reference/adox-api/index-object-adox.md) Если **столбца** не существует в [Таблицы](../../../ado/reference/adox-api/table-object-adox.md) , добавляется к уже [таблиц](../../../ado/reference/adox-api/tables-collection-adox.md) коллекции.  
  
## <a name="applies-to"></a>Объект применения  
 [Коллекция Columns (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Столбцов и таблиц методов append для коллекций, пример свойства Name (Visual Basic)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Append коллекции Keys метод, тип ключа, RelatedColumn, RelatedTable и UpdateRule свойства (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Append-метод (коллекция Groups ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-метод (коллекция Indexes ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append-метод (коллекция Keys ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-метод (коллекция Procedures ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-метод (коллекция Tables ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append-метод (коллекция Users ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Метод Append (коллекция Views ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
