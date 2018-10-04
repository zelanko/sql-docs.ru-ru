---
title: Пользовательские свойства назначения "Обработка секций" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 3eac4413-0c90-4b06-8f7e-d0d72f4d869d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9139ff2af92d861f356514e9e78073c3e858ab81
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048594"
---
# <a name="partition-processing-destination-custom-properties"></a>Пользовательские свойства назначения «Обработка секций»
  Назначение «Обработка секций» обладает как пользовательскими свойствами, так и свойствами, общими для всех компонентов потока данных.  
  
 В следующей таблице описаны пользовательские свойства назначения «Обработка секций». Все свойства доступны для чтения и записи.  
  
|Свойство|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|Строка подключения к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или проекту служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|KeyDuplicate|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение `False`, значение, указывающее, как обрабатывать ошибки повторения ключа. Возможные значения: `IgnoreError` (0), `ReportAndContinue` (1), и `ReportAndStop` (2). Значение по умолчанию этого свойства — `IgnoreError` (0).|  
|KeyErrorAction|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение `False`, значение, указывающее, как обрабатывать ошибки ключа. Допустимые значения — `ConvertToUnknown` (0) и `DiscardRecord` (1). Значение по умолчанию этого свойства — `ConvertToUnknown` (0).|  
|KeyErrorLimit|Целочисленный|Если свойство UseDefaultConfiguration имеет значение `False`, максимальное разрешенное количество ошибок ключа.|  
|KeyErrorLimitAction|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение `False`, значение, указывающее действие, выполняемое, когда `KeyErrorLimit` достижения. Возможные значения: `StopLogging` (1) и `StopProcessing` (0). Значение по умолчанию этого свойства — `StopProcessing` (0).|  
|KeyErrorLogFile|String|Если свойство UseDefaultConfiguration имеет значение `False`, путь и имя файла журнала ошибок.|  
|KeyNotFound|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение `False`, значение, указывающее, как обрабатывать ошибки отсутствующего ключа. Возможные значения: `IgnoreError` (0), `ReportAndContinue` (1), и `ReportAndStop` (2). Значение по умолчанию этого свойства — `ReportAndContinue` (1).|  
|NullKeyConvertedToUnknown|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение `False`, оно показывает, как обрабатывать ключи null, преобразованные в значение Unknown. Возможные значения: `IgnoreError` (0), `ReportAndContinue` (1), и `ReportAndStop` (2). Значение по умолчанию этого свойства — `IgnoreError` (0).|  
|NullKeyNotAllowed|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение `False`, значение, указывающее, как обрабатывать запрещенные значения NULL. Возможные значения: `IgnoreError` (0), `ReportAndContinue` (1), и `ReportAndStop` (2). Значение по умолчанию этого свойства — `ReportAndContinue` (1).|  
|ProcessType|Integer (перечисление)|Тип обработки секций, используемый преобразованием. Допустимые значения — `ProcessAdd` (1) (добавочное), `ProcessFull` (0) и `ProcessUpdate` (2).|  
|UseDefaultConfiguration|Логическое значение|Значение, указывающее, используется ли преобразованием конфигурация ошибок по умолчанию. Если это свойство имеет `False`, преобразование использует значения пользовательских свойств обработки ошибок, перечисленные в этой таблице, в том числе KeyDuplicate, KeyErrorAction и т. д.|  
  
 Ввод и входные столбцы назначения «Обработка секций» не обладают пользовательскими свойствами.  
  
 Дополнительные сведения см. в статье [Partition Processing Destination](partition-processing-destination.md).  
  
## <a name="see-also"></a>См. также  
 [Common Properties](../common-properties.md)  
  
  
