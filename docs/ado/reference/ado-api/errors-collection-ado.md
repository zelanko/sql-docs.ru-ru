---
title: "Коллекция ошибок (ADO) | Документы Microsoft"
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
- Connection15::Errors
- Connection15::get_Errors
- Connection15::GetErrors
helpviewer_keywords:
- Errors collection [ADO]
ms.assetid: 290819e1-7b39-4e1e-a93b-801257138b00
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 27ca46528314f34b769d505269ade0c73fb1b051
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="errors-collection-ado"></a>Коллекция ошибок (ADO)
Содержит все [ошибка](../../../ado/reference/ado-api/error-object.md) объектов, созданных в ответ на сбой одного поставщика.  
  
## <a name="remarks"></a>Замечания  
 Любая операция, включающее объекты ADO можно создать одну или несколько ошибок поставщика. Как возникли ошибки, один или несколько **ошибка** объектов может быть помещен в **ошибки** коллекцию [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта. Если другая операция ADO создает ошибку, **ошибки** коллекция очищается и новый набор **ошибка** объектов может быть помещен в **ошибки** коллекции.  
  
 Каждый **ошибка** представляет ошибку конкретного поставщика, а не ошибка ADO. Ошибки ADO предоставляется механизм обработки исключений во время выполнения. Например, в Visual Basic возникновение ошибки конкретного ADO активируют [onError](../../../ado/reference/rds-api/onerror-event-rds.md) событий и отображаются в **Err** объекта.  
  
 ADO операций, которые не вызывают ошибку не действуют **ошибки** коллекции. Используйте [снимите](../../../ado/reference/ado-api/clear-method-ado.md) метод, чтобы вручную удалить **ошибки** коллекции.  
  
 Набор **ошибка** объекты в **ошибки** коллекция описывает все ошибки, возникшие в ответ на одну инструкцию. Перечисление со списком ошибок в **ошибки** коллекция позволяет вашей процедуры обработки ошибок, чтобы точнее определить причину и источник ошибки и предпринять соответствующие действия для восстановления.  
  
 Некоторые свойства и методы возвращают предупреждения, которые отображаются в виде **ошибка** объекты в **ошибки** коллекции, но не остановить выполнение программы. Перед вызовом метода [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), или [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) методы [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта, [откройте](../../../ado/reference/ado-api/open-method-ado-connection.md) метод **подключения** объекта или набора [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство **записей** , вызовите **снимите**метод **ошибки** коллекции. Таким образом, можно прочитать [число](../../../ado/reference/ado-api/count-property-ado.md) свойство **ошибки** коллекцию для проверки возникли предупреждения.  
  
> [!NOTE]
>  В разделе **ошибка** разделе объекта более подробные объяснения способа за одну операцию ADO можно создать несколько ошибок.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства коллекции ошибок, методы и события](../../../ado/reference/ado-api/errors-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Объект Error](../../../ado/reference/ado-api/error-object.md)   
 [Поставщики приложение A:](../../../ado/guide/appendixes/appendix-a-providers.md)
