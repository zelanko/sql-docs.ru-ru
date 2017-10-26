---
title: "Свойства источника OData | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fde5bb0-6d78-4ec4-8f0b-67f91c53fe99
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: ee79d0f1b31963b7d13aa07bf4603246139c3a7c
ms.openlocfilehash: 64e297a37c3b6449551968b5788f8c2c0ddd4ab6
ms.contentlocale: ru-ru
ms.lasthandoff: 08/23/2017

---
# <a name="odata-source-properties"></a>Свойства источника OData
При щелчке правой кнопкой мыши **источника OData** в потоке данных и выбрать **свойства**, открывается окно свойств для **источника OData** в **свойства** окна.  

## <a name="properties"></a>Свойства 
|property|Description|  
|-|-|  
|CollectionName|Имя коллекции для получения от службы OData. Свойство **CollectionName** используется в том случае, когда значение **UseResourcePath** равно False.<br /><br /> Это свойство является expressionable, который позволяет задать значение во время выполнения. Тем не менее если метаданные коллекции не соответствуют метаданным, которые существовали во время разработки, возникает ошибка проверки, что приводит к ошибке при выполнении потока данных.|  
|DefaultStringLength|Это значение указывает длину по умолчанию для строковых столбцов без максимальной длины.<br /><br /> **По умолчанию:** 4000|  
|Запрос|Параметры запроса OData. Это свойство является expressionable и можно задать во время выполнения.|  
|ResourcePath|Это свойство используется в том случае, когда необходимо указать полный путь к ресурсу, а не просто выбрать имя коллекции. Это свойство используется в том случае, если значение **UseResourcePath** равно True.|  
|UseResourcePath|Если задано значение True, то значение **ResourcePath** добавляется к базовому URL-адресу для определения расположения канала OData. Если значение равно False, то используется значение **CollectionName** .<br /><br /> **По умолчанию:** False|  
  
## <a name="see-also"></a>См. также:
[Источник «OData»](odata-source.md)

