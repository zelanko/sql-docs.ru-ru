---
title: Метод Append (индексы ADOX) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 6996f3a0a3ad9f2ffa727a6cbd7b48d3fbf32777
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764065"
---
# <a name="append-method-adox-indexes"></a>Метод Append (коллекция Indexes ADOX)
Добавляет новый объект [index](../../../ado/reference/adox-api/index-object-adox.md) в коллекцию [индексов](../../../ado/reference/adox-api/indexes-collection-adox.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Indexes.Append Index [,Columns]  
```  
  
#### <a name="parameters"></a>Параметры  
 *Номер*  
 Добавляемый объект **index** или имя создаваемого и добавляемого индекса.  
  
 *Столбцы*  
 Необязательный элемент. Значение **типа Variant** , указывающее имена столбцов, которые будут индексироваться. Параметр *Columns* соответствует значениям свойства [Name](../../../ado/reference/adox-api/name-property-adox.md) объекта [Column](../../../ado/reference/adox-api/column-object-adox.md) или объектов.  
  
## <a name="remarks"></a>Примечания  
 Параметр *Columns* может принимать либо имя столбца, либо массив имен столбцов.  
  
 Если поставщик не поддерживает создание индексов, возникнет ошибка.  
  
## <a name="applies-to"></a>Применяется к  
 [Коллекция Indexes (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода Append для индексов (Visual Basic)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [Метод Append (столбцы ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Метод Append (группы ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Метод Append (ключи ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Метод Append (процедуры ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Метод Append (таблицы ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Метод Append (пользователи ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Метод Append (коллекция Views ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
