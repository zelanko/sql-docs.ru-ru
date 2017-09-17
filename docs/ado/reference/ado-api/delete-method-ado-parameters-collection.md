---
title: "Удаление метода (коллекция параметров ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _DynaCollection::Delete
- _DynaCollection::raw_Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 160c575e-df63-4ade-a2d3-5fd8f72e70cc
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 770271da0c0b2b378adf2be5611428e05f7f5148
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="delete-method-ado-parameters-collection"></a>Удаление метода (коллекция параметров ADO)
Удаляет объект из [параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Parameters.Delete Index  
```  
  
#### <a name="parameters"></a>Параметры  
 *Индекс*  
 Объект **строка** значение, содержащее имя объекта, удалить или порядковый номер объекта (индекса) в коллекции.  
  
## <a name="remarks"></a>Замечания  
 С помощью **удалить** метод с коллекцией позволяет удалить один из объектов в коллекции. Этот метод доступен только для **параметры** коллекцию [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта. Необходимо использовать [параметр](../../../ado/reference/ado-api/parameter-object.md) объекта [имя](../../../ado/reference/ado-api/name-property-ado.md) свойства или индекса коллекции при вызове **удалить** метод — переменной объекта не является допустимым аргументом.  
  
## <a name="applies-to"></a>Объект применения  
 [Коллекция параметров (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Метод Delete (ADO поля коллекции)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Удаление метода (набора записей ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Метод макрокоманду УдалитьЗапись (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
