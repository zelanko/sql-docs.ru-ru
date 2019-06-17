---
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 109b7ff83e6b3f722560dae0a034c4bf37da137f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66719267"
---
# <a name="errors-collection-ado"></a>Коллекция Errors (ADO)
Содержит все [ошибка](../../../ado/reference/ado-api/error-object.md) объекты, созданные в ответ на сбой одного поставщика.  
  
## <a name="remarks"></a>Примечания  
 Любая операция, включающее объекты ADO можно создать один или несколько ошибок поставщика. Так как возникли ошибки, один или несколько **ошибка** объекты могут быть помещены в **ошибки** коллекцию [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта. Если другая операция ADO создает ошибку, **ошибки** коллекции установлен и новый набор **ошибка** объекты могут быть помещены в **ошибки** коллекции.  
  
 Каждый **ошибка** представляет ошибку конкретного поставщика, а не ошибка ADO. Ошибки ADO предоставляются механизм обработки исключений среды выполнения. Например, в Microsoft Visual Basic, возникновение ошибки ADO конкретных активирует [onError](../../../ado/reference/rds-api/onerror-event-rds.md) событий и отображаются в **Err** объекта.  
  
 ADO операций, которые не создают ошибку не оказывают влияния на **ошибки** коллекции. Используйте [снимите](../../../ado/reference/ado-api/clear-method-ado.md) метод, чтобы вручную удалить **ошибки** коллекции.  
  
 Набор **ошибка** объекты в **ошибки** коллекции описывает все ошибки, возникшие в ответ на одну инструкцию. Перечисление конкретные ошибки в **ошибки** коллекции позволяет вашей процедуры обработки ошибок, чтобы точнее определить причину и источник ошибки и предпринять соответствующие действия для восстановления.  
  
 Некоторые свойства и методы возвращают предупреждения, которые отображаются в виде **ошибка** объекты в **ошибки** коллекции, но не приостанавливает выполнение программы. Перед вызовом метода [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), или [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) методы [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта, [откройте](../../../ado/reference/ado-api/open-method-ado-connection.md) метод **подключения** , задана объекта или [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство **набор записей** , вызовите **снимите**метод **ошибки** коллекции. Таким образом, можно прочитать [число](../../../ado/reference/ado-api/count-property-ado.md) свойство **ошибки** коллекцию для проверки возникли предупреждения.  
  
> [!NOTE]
>  См. в разделе **ошибка** разделе объекта более подробное описание того, за одну операцию ADO можно создать несколько ошибок.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства коллекции ошибок, методы и события](../../../ado/reference/ado-api/errors-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Объект ошибки](../../../ado/reference/ado-api/error-object.md)   
 [Приложение а. Поставщики](../../../ado/guide/appendixes/appendix-a-providers.md)
