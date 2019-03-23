---
title: Пользовательские свойства назначения "Обработка секций" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3eac4413-0c90-4b06-8f7e-d0d72f4d869d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3dbab24f756498d7427f9961e4176249daac8dfb
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58385062"
---
# <a name="partition-processing-destination-custom-properties"></a>Пользовательские свойства назначения «Обработка секций»
  Назначение «Обработка секций» обладает как пользовательскими свойствами, так и свойствами, общими для всех компонентов потока данных.  
  
 В следующей таблице описаны пользовательские свойства назначения «Обработка секций». Все свойства доступны для чтения и записи.  
  
|Свойство|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|Строка подключения к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или проекту служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|KeyDuplicate|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение `False`, значение, указывающее, как обрабатывать ошибки повторения ключа. Допустимые значения: `IgnoreError` (0), `ReportAndContinue` (1) и `ReportAndStop` (2). По умолчанию это свойство имеет значение `IgnoreError` (0).|  
|KeyErrorAction|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение `False`, значение, указывающее, как обрабатывать ошибки ключа. Допустимые значения — `ConvertToUnknown` (0) и `DiscardRecord` (1). По умолчанию это свойство имеет значение `ConvertToUnknown` (0).|  
|KeyErrorLimit|Целочисленный|Если свойство UseDefaultConfiguration имеет значение `False`, максимальное разрешенное количество ошибок ключа.|  
|KeyErrorLimitAction|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение `False`, значение, указывающее действие, выполняемое, когда `KeyErrorLimit` достижения. Возможные значения: `StopLogging` (1) и `StopProcessing` (0). По умолчанию это свойство имеет значение `StopProcessing` (0).|  
|KeyErrorLogFile|String|Если свойство UseDefaultConfiguration имеет значение `False`, путь и имя файла журнала ошибок.|  
|KeyNotFound|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение `False`, значение, указывающее, как обрабатывать ошибки отсутствующего ключа. Допустимые значения: `IgnoreError` (0), `ReportAndContinue` (1) и `ReportAndStop` (2). Значение по умолчанию этого свойства равно `ReportAndContinue` (1).|  
|NullKeyConvertedToUnknown|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение `False`, оно показывает, как обрабатывать ключи null, преобразованные в значение Unknown. Допустимые значения: `IgnoreError` (0), `ReportAndContinue` (1) и `ReportAndStop` (2). По умолчанию это свойство имеет значение `IgnoreError` (0).|  
|NullKeyNotAllowed|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение `False`, значение, указывающее, как обрабатывать запрещенные значения NULL. Допустимые значения: `IgnoreError` (0), `ReportAndContinue` (1) и `ReportAndStop` (2). Значение по умолчанию этого свойства равно `ReportAndContinue` (1).|  
|ProcessType|Integer (перечисление)|Тип обработки секций, используемый преобразованием. Допустимые значения — `ProcessAdd` (1) (добавочное), `ProcessFull` (0) и `ProcessUpdate` (2).|  
|UseDefaultConfiguration|Логическое значение|Значение, указывающее, используется ли преобразованием конфигурация ошибок по умолчанию. Если это свойство имеет `False`, преобразование использует значения пользовательских свойств обработки ошибок, перечисленные в этой таблице, в том числе KeyDuplicate, KeyErrorAction и т. д.|  
  
 Ввод и входные столбцы назначения «Обработка секций» не обладают пользовательскими свойствами.  
  
 Дополнительные сведения см. в статье [Partition Processing Destination](partition-processing-destination.md).  
  
## <a name="see-also"></a>См. также  
 [Common Properties](../common-properties.md)  
  
  
