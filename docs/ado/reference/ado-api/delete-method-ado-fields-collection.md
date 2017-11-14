---
title: "Метод Delete (ADO поля коллекции) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Fields20::Delete
- Fields20::raw_Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 25bedc25-c51c-4cab-96ce-930b959965d9
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: de4e5f85bad4849f4ace2ee4e32fbe6606cb667d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="delete-method-ado-fields-collection"></a>Метод Delete (ADO поля коллекции)
Удаляет объект из [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Fields.Delete Field  
```  
  
#### <a name="parameters"></a>Параметры  
 *Поле*  
 Объект **Variant** , указывающий [поле](../../../ado/reference/ado-api/field-object.md) удаляемого объекта. Этот параметр может иметь имя **поле** объекта или порядковый номер **поле** сам объект.  
  
## <a name="remarks"></a>Замечания  
 Вызов **Fields.Delete** метода на открытый [записей](../../../ado/reference/ado-api/recordset-object-ado.md) приводит к ошибке во время выполнения.  
  
## <a name="applies-to"></a>Объект применения  
 [Коллекция Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Удаление метода (коллекция параметров ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Удаление метода (набора записей ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Метод макрокоманду УдалитьЗапись (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)

