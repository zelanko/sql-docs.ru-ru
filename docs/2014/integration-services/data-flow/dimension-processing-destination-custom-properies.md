---
title: Пользовательские свойства назначения "Обработка измерений" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9700f663-53f2-49b6-b1ef-92c7b752d6a1
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4acc3794f07fe6c2ae4967781b90518f64407962
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328104"
---
# <a name="dimension-processing-destination-custom-properies"></a>Пользовательские свойства назначения «Обработка измерений»
  Назначение «Обработка измерений» обладает как пользовательскими свойствами, так и свойствами, общими для всех компонентов потока данных.  
  
 В следующей таблице описаны пользовательские свойства назначения «Обработка измерений». Все свойства доступны для чтения и записи.  
  
|Свойство|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|Строка соединения с экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или с проектом служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|KeyDuplicate|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение `False`, значение, указывающее, как обрабатывать ошибки повторения ключа. Возможные значения: `IgnoreError` (0), `ReportAndContinue` (1), и `ReportAndStop` (2). Значение по умолчанию этого свойства — `IgnoreError` (0).|  
|KeyErrorAction|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение `False`, значение, указывающее способ обработки ошибок ключа. Допустимые значения — `ConvertToUnknown` (0) и `DiscardRecord` (1). Значение по умолчанию этого свойства — `ConvertToUnknown` (0).|  
|KeyErrorLimit|Целочисленный|Если свойство UseDefaultConfiguration имеет значение `False`, максимальное количество ошибок ключа, которые включены.|  
|KeyErrorLimitAction|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение `False`, значение, указывающее действие, выполняемое, когда `KeyErrorLimit` достижения. Возможные значения: `StopLogging` (1) и `StopProcessing` (0). Значение по умолчанию этого свойства — `StopProcessing` (0).|  
|KeyErrorLogFile|String|Если свойство UseDefaultConfiguration имеет значение `False`, путь и имя файла журнала ошибок.|  
|KeyNotFound|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение `False`, значение, указывающее, как обрабатывать ошибки отсутствующего ключа. Возможные значения: `IgnoreError` (0), `ReportAndContinue` (1), и `ReportAndStop` (2). Значение по умолчанию этого свойства — `IgnoreError` (0).|  
|NullKeyConvertedToUnknown|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение `False`, оно показывает, как обрабатывать ключи null, преобразованные в значение unknown. Возможные значения: `IgnoreError` (0), `ReportAndContinue` (1), и `ReportAndStop` (2). Значение по умолчанию этого свойства — `IgnoreError` (0).|  
|NullKeyNotAllowed|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение `False`, значение, указывающее, как обрабатывать запрещенные значения NULL. Возможные значения: `IgnoreError` (0), `ReportAndContinue` (1), и `ReportAndStop` (2). Значение по умолчанию этого свойства — `IgnoreError` (0).|  
|ProcessType|Integer (перечисление)|Тип обработки измерений, используемый преобразованием. Допустимые значения — `ProcessAdd` (1) (добавочное), `ProcessFull` (0) и `ProcessUpdate` (2).|  
|UseDefaultConfiguration|Логическое значение|Значение, указывающее, используется ли преобразованием конфигурация ошибок по умолчанию. Если это свойство имеет `False`, в преобразование включаются сведения об обработке ошибок.|  
  
 Ввод и входные столбцы назначения «Обработка измерения» не обладают пользовательскими свойствами.  
  
 Дополнительные сведения см. в разделе [Dimension Processing Destination](dimension-processing-destination.md).  
  
## <a name="see-also"></a>См. также  
 [Common Properties](../common-properties.md)  
  
  
