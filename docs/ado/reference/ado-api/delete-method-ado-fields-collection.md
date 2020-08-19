---
description: Метод Delete (коллекция Fields ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: fb60cea6ef2e741103e94f38955bb2afc688e228
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444176"
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
  
## <a name="applies-to"></a>Применение  
 [Коллекция Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Метод Delete (Коллекция параметров ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Метод Delete (набор записей ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Метод DeleteRecord (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
