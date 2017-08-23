---
title: "«Обработка измерений» пользовательские назначения | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9700f663-53f2-49b6-b1ef-92c7b752d6a1
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3bdb4a8d56ab732b129007c73dab6535deabb890
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="dimension-processing-destination-custom-properies"></a>Пользовательские свойства назначения «Обработка измерений»
  Назначение «Обработка измерений» обладает как пользовательскими свойствами, так и свойствами, общими для всех компонентов потока данных.  
  
 В следующей таблице описаны пользовательские свойства назначения «Обработка измерений». Все свойства доступны для чтения и записи.  
  
|Свойство|Тип данных|Description|  
|--------------|---------------|-----------------|  
|ASConnectionString|Строковые значения|Строка соединения с экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или с проектом служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|KeyDuplicate|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение **False**, оно показывает, как обрабатывать ошибки повторения ключа. Возможные значения: **IgnoreError** (0), **ReportAndContinue** (1) и **ReportAndStop** (2). Значением по умолчанию для этого свойства является **IgnoreError** (0).|  
|KeyErrorAction|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение **False**, оно показывает, как обрабатывать ошибки ключа. Возможные значения: **ConvertToUnknown** (0) и **DiscardRecord** (1). Значением по умолчанию для этого свойства является **ConvertToUnknown** (0).|  
|KeyErrorLimit|Целочисленный|Если свойство UseDefaultConfiguration имеет значение **False**, значит, включено максимально разрешенное количество ошибок ключа.|  
|KeyErrorLimitAction|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение **False**, оно устанавливает действие при достижении предела **KeyErrorLimit** . Возможные значения: **StopLogging** (1) и **StopProcessing** (0). Значением по умолчанию для этого свойства является **StopProcessing** (0).|  
|KeyErrorLogFile|Строковые значения|Если свойство UseDefaultConfiguration имеет значение **False**, оно представляет собой путь и имя файла журнала ошибок.|  
|KeyNotFound|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение **False**, оно показывает, как обрабатывать ошибки отсутствующего ключа. Возможные значения: **IgnoreError** (0), **ReportAndContinue** (1) и **ReportAndStop** (2). Значением по умолчанию для этого свойства является **IgnoreError** (0).|  
|NullKeyConvertedToUnknown|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение **False**, оно показывает, как обрабатывать ключи NULL, преобразованные в значение Unknown. Возможные значения: **IgnoreError** (0), **ReportAndContinue** (1) и **ReportAndStop** (2). Значением по умолчанию для этого свойства является **IgnoreError** (0).|  
|NullKeyNotAllowed|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение **False**, оно показывает, как обрабатывать запрещенные значения NULL. Возможные значения: **IgnoreError** (0), **ReportAndContinue** (1) и **ReportAndStop** (2). Значением по умолчанию для этого свойства является **IgnoreError** (0).|  
|ProcessType|Integer (перечисление)|Тип обработки измерений, используемый преобразованием. Возможные значения: **ProcessAdd** (1) (добавочное), **ProcessFull** (0) и **ProcessUpdate** (2).|  
|UseDefaultConfiguration|Логическое значение|Значение, указывающее, используется ли преобразованием конфигурация ошибок по умолчанию. Если это свойство принимает значение **False**, в преобразование включаются сведения об обработке ошибок.|  
  
 Ввод и входные столбцы назначения «Обработка измерения» не обладают пользовательскими свойствами.  
  
 Дополнительные сведения см. в разделе [Dimension Processing Destination](../../integration-services/data-flow/dimension-processing-destination.md).  
  
## <a name="see-also"></a>См. также  
 [Общие свойства](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
