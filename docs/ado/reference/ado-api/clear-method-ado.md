---
description: Метод Clear (ADO)
title: Метод Clear (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Errors::raw_Clear
- Errors::Clear
helpviewer_keywords:
- Clear method [ADO]
ms.assetid: 0a61ba7a-20b8-426a-91a0-9040e7c5a98a
author: rothja
ms.author: jroth
ms.openlocfilehash: 502592df71938e31ff50462878659df52c95f127
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450996"
---
# <a name="clear-method-ado"></a>Метод Clear (ADO)
Удаляет все объекты [Error](../../../ado/reference/ado-api/error-object.md) из коллекции [ошибок](../../../ado/reference/ado-api/errors-collection-ado.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Errors.Clear  
```  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **clear** в коллекции [Errors](../../../ado/reference/ado-api/errors-collection-ado.md) , чтобы удалить из коллекции все существующие объекты [ошибок](../../../ado/reference/ado-api/error-object.md) . При возникновении ошибки ADO автоматически очищает коллекцию **ошибок** и заполняет ее объектами с **ошибками** на основе новой ошибки.  
  
 Некоторые свойства и методы возвращают предупреждения, которые отображаются как объекты **ошибок** в коллекции **ошибок** , но не приводят к остановке выполнения программы. Перед вызовом методов [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)или [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) для объекта [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) ; метод [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) для объекта [Connection](../../../ado/reference/ado-api/connection-object-ado.md) ; или задайте свойство [Filter](../../../ado/reference/ado-api/filter-property.md) для объекта **набора записей** , вызовите метод **clear** для коллекции **Errors** . Таким образом, можно прочитать свойство [Count](../../../ado/reference/ado-api/count-property-ado.md) коллекции **Errors** , чтобы проверить наличие возвращаемых предупреждений.  
  
## <a name="applies-to"></a>Применение  
 [Коллекция Errors (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов Execute, Requery и Clear (Visual Basic)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Пример методов Execute, Requery и Clear (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Пример методов Execute, Requery и Clear (Visual c++)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [Метод CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Метод Delete (коллекция полей ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Метод Delete (Коллекция параметров ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Метод Delete (набор записей ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Свойство Filter](../../../ado/reference/ado-api/filter-property.md)   
 [Повторно синхронизировать метод](../../../ado/reference/ado-api/resync-method.md)   
 [Метод UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)
