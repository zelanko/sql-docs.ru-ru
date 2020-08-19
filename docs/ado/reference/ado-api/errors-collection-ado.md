---
description: Коллекция Errors (ADO)
title: Коллекция Errors (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Errors
- Connection15::get_Errors
- Connection15::GetErrors
helpviewer_keywords:
- Errors collection [ADO]
ms.assetid: 290819e1-7b39-4e1e-a93b-801257138b00
author: rothja
ms.author: jroth
ms.openlocfilehash: 6f4719c9dcf182b6840ad950373b35c7ea8f0361
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443956"
---
# <a name="errors-collection-ado"></a>Коллекция Errors (ADO)
Содержит все объекты [ошибок](../../../ado/reference/ado-api/error-object.md) , созданные в ответ на одну ошибку, связанную с поставщиком.  
  
## <a name="remarks"></a>Remarks  
 Любая операция, включающая объекты ADO, может формировать одну или несколько ошибок поставщика. При возникновении каждой ошибки в коллекцию **Errors** объекта [Connection](../../../ado/reference/ado-api/connection-object-ado.md) можно поместить один или несколько объектов **ошибок** . Если другая операция ADO создает ошибку, коллекция **Errors** удаляется, а новый набор объектов **ошибок** может быть помещен в коллекцию **Errors** .  
  
 Каждый объект **ошибки** представляет определенную ошибку поставщика, а не ошибку ADO. Ошибки ADO предоставляются механизмом обработки исключений времени выполнения. Например, в Microsoft Visual Basic возникновение ошибки, относящейся к ADO, вызывает событие [OnError](../../../ado/reference/rds-api/onerror-event-rds.md) и появляется в объекте **Err** .  
  
 Операции ADO, не создающие ошибку, не влияют на сбор **ошибок** . Чтобы вручную очистить коллекцию **ошибок** , используйте метод [clear](../../../ado/reference/ado-api/clear-method-ado.md) .  
  
 Набор объектов **ошибок** в коллекции **Errors** описывает все ошибки, произошедшие в ответ на одну инструкцию. Перечисление конкретных ошибок в коллекции **Errors** позволяет процедурам обработки ошибок более точно определить причину и происхождение ошибки и предпринять соответствующие шаги для восстановления.  
  
 Некоторые свойства и методы возвращают предупреждения, которые отображаются как объекты **ошибок** в коллекции **ошибок** , но не приводят к остановке выполнения программы. Перед вызовом методов [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)или [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) для объекта [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) , метода [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) для объекта **Connection** или установки свойства [Filter](../../../ado/reference/ado-api/filter-property.md) для объекта **набора записей** вызовите метод **clear** для коллекции **Errors** . Таким образом, можно прочитать свойство [Count](../../../ado/reference/ado-api/count-property-ado.md) коллекции **Errors** , чтобы проверить наличие возвращаемых предупреждений.  
  
> [!NOTE]
>  Более подробное объяснение того, как одна операция ADO может формировать несколько ошибок, см. в разделе Object **Error** .  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события коллекции ошибок](../../../ado/reference/ado-api/errors-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Объект Error](../../../ado/reference/ado-api/error-object.md)   
 [Приложение А. Поставщики](../../../ado/guide/appendixes/appendix-a-providers.md)
