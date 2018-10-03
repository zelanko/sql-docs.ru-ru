---
title: Удаление метода (коллекция Parameters ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _DynaCollection::Delete
- _DynaCollection::raw_Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 160c575e-df63-4ade-a2d3-5fd8f72e70cc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8eb7d5d58e0f6afe31304b6fce13da2d8c48e54e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47696923"
---
# <a name="delete-method-ado-parameters-collection"></a>Метод Delete (коллекция Parameters ADO)
Удаляет объект из [параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Parameters.Delete Index  
```  
  
#### <a name="parameters"></a>Параметры  
 *Index*  
 Объект **строка** значение, содержащее имя объекта, удалить или порядковый номер объекта (индекс) в коллекции.  
  
## <a name="remarks"></a>Примечания  
 С помощью **удалить** метод коллекции позволяет удалить один из объектов в коллекции. Этот метод доступен только на **параметры** коллекцию [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта. Необходимо использовать [параметр](../../../ado/reference/ado-api/parameter-object.md) объекта [имя](../../../ado/reference/ado-api/name-property-ado.md) свойство или его индекс коллекции, при вызове **удалить** метод — переменной объекта не является допустимым аргументом.  
  
## <a name="applies-to"></a>Объект применения  
 [Коллекция Parameters (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Delete (коллекция Fields ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Удаление метода (объект Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Метод DeleteRecord (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
