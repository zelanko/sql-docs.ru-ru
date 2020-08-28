---
description: Метод Clear (ADO)
title: Метод Clear (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: d78980c1baee5aed1280f69c0d5224622a217ea0
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88975475"
---
# <a name="clear-method-ado"></a>Метод Clear (ADO)
Удаляет все объекты [Error](./error-object.md) из коллекции [ошибок](./errors-collection-ado.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Errors.Clear  
```  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **clear** в коллекции [Errors](./errors-collection-ado.md) , чтобы удалить из коллекции все существующие объекты [ошибок](./error-object.md) . При возникновении ошибки ADO автоматически очищает коллекцию **ошибок** и заполняет ее объектами с **ошибками** на основе новой ошибки.  
  
 Некоторые свойства и методы возвращают предупреждения, которые отображаются как объекты **ошибок** в коллекции **ошибок** , но не приводят к остановке выполнения программы. Перед вызовом методов [Resync](./resync-method.md), [UpdateBatch](./updatebatch-method.md)или [CancelBatch](./cancelbatch-method-ado.md) для объекта [набора записей](./recordset-object-ado.md) ; метод [Open](./open-method-ado-connection.md) для объекта [Connection](./connection-object-ado.md) ; или задайте свойство [Filter](./filter-property.md) для объекта **набора записей** , вызовите метод **clear** для коллекции **Errors** . Таким образом, можно прочитать свойство [Count](./count-property-ado.md) коллекции **Errors** , чтобы проверить наличие возвращаемых предупреждений.  
  
## <a name="applies-to"></a>Применение  
 [Коллекция Errors (ADO)](./errors-collection-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов Execute, Requery и Clear (Visual Basic)](./execute-requery-and-clear-methods-example-vb.md)   
 [Пример методов Execute, Requery и Clear (VBScript)](./execute-requery-and-clear-methods-example-vbscript.md)   
 [Пример методов Execute, Requery и Clear (Visual c++)](./execute-requery-and-clear-methods-example-vc.md)   
 [Метод CancelBatch (ADO)](./cancelbatch-method-ado.md)   
 [Метод Delete (коллекция полей ADO)](./delete-method-ado-fields-collection.md)   
 [Метод Delete (Коллекция параметров ADO)](./delete-method-ado-parameters-collection.md)   
 [Метод Delete (набор записей ADO)](./delete-method-ado-recordset.md)   
 [Свойство Filter](./filter-property.md)   
 [Повторно синхронизировать метод](./resync-method.md)   
 [Метод UpdateBatch](./updatebatch-method.md)