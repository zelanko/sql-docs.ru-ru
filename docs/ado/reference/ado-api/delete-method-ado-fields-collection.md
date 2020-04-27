---
title: Метод Delete (коллекция полей ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Fields20::Delete
- Fields20::raw_Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 25bedc25-c51c-4cab-96ce-930b959965d9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9db49905b6548e5cb21cca976683c8b387017d32
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67919136"
---
# <a name="delete-method-ado-fields-collection"></a>Метод Delete (коллекция Fields ADO)
Удаляет объект из коллекции [полей](../../../ado/reference/ado-api/fields-collection-ado.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Fields.Delete Field  
```  
  
#### <a name="parameters"></a>Параметры  
 *Поле*  
 **Вариант** , обозначающий объект [поля](../../../ado/reference/ado-api/field-object.md) для удаления. Этот параметр может быть именем объекта **поля** или порядком расположения самого объекта **поля** .  
  
## <a name="remarks"></a>Remarks  
 Вызов метода **Fields. Delete** для открытого [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) приводит к ошибке времени выполнения.  
  
## <a name="applies-to"></a>Применяется к  
 [Коллекция Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Delete (Коллекция параметров ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Метод Delete (набор записей ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Метод DeleteRecord (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
