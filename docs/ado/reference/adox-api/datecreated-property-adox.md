---
title: "Свойство DateCreated (ADOX) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Table::get_DateCreated
- _Table::DateCreated
- _Table::GetDateCreated
helpviewer_keywords: DateCreated property [ADOX]
ms.assetid: 2bf4b00d-045c-444e-8af7-8af6297ed418
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9e56ae8c4ec6a57f7fc50ca5d00f21bc77ce7d3e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="datecreated-property-adox"></a>Свойство DateCreated (ADOX)
Указывает дату создания объекта.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **Variant** значение, указывающее дату создания. Имеет значение null при **DateCreated** не поддерживается поставщиком.  
  
## <a name="remarks"></a>Remarks  
 **DateCreated** свойство имеет значение null для добавленного объектов. После добавления нового [представление](../../../ado/reference/adox-api/view-object-adox.md) или [процедура](../../../ado/reference/adox-api/procedure-object-adox.md), необходимо вызвать [обновление](../../../ado/reference/ado-api/refresh-method-ado.md) метод [представления](../../../ado/reference/adox-api/views-collection-adox.md) или [процедуры ](../../../ado/reference/adox-api/procedures-collection-adox.md) коллекции для получения значений для **DateCreated** свойство.  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Объект Procedure (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Объект Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[Объект View (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>См. также:  
 [DateCreated и DateModified-пример свойства (Visual Basic)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [Свойство DateModified (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md)
