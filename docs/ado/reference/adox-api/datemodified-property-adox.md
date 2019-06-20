---
title: Свойство DateModified (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Table::get_DateModified
- _Table::DateModified
- _Table::GetDateModified
helpviewer_keywords:
- DateModified property [ADOX]
ms.assetid: fed09266-1547-4bda-9088-c254d81cc738
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 5d0cd8a6196bdc0f933470a52dbb3567f64df05e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718919"
---
# <a name="datemodified-property-adox"></a>Свойство DateModified (ADOX)
Указывает дату последнего изменения объекта.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **Variant** значение, указывающее, Дата изменения. Имеет значение null Если **DateModified** не поддерживается поставщиком.  
  
## <a name="remarks"></a>Примечания  
 **DateModified** свойство имеет значение null для вновь добавленных объектов. После добавления нового [представление](../../../ado/reference/adox-api/view-object-adox.md) или [процедуры](../../../ado/reference/adox-api/procedure-object-adox.md), необходимо вызвать [обновить](../../../ado/reference/ado-api/refresh-method-ado.md) метод [представления](../../../ado/reference/adox-api/views-collection-adox.md) или [процедуры ](../../../ado/reference/adox-api/procedures-collection-adox.md) коллекции, чтобы получить значения для **DateModified** свойство.  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Объект Procedure (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Объект Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[Объект View (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>См. также  
 [DateCreated и DateModified свойства (Visual Basic)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [Свойство DateCreated (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md)
