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
ms.topic: article
ms.assetid: 9700f663-53f2-49b6-b1ef-92c7b752d6a1
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f4dae4c9661e8a04e34b5d2b78ccdd0f556bfa7c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087905"
---
# <a name="dimension-processing-destination-custom-properies"></a>Пользовательские свойства назначения «Обработка измерений»
  Назначение «Обработка измерений» обладает как пользовательскими свойствами, так и свойствами, общими для всех компонентов потока данных.  
  
 В следующей таблице описаны пользовательские свойства назначения «Обработка измерений». Все свойства доступны для чтения и записи.  
  
|Свойство|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|Строка соединения с экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или с проектом служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|KeyDuplicate|Integer (перечисление)|При UseDefaultConfiguration `False`, значение, указывающее, как обрабатывать ошибки повторения ключа. Возможными значениями являются `IgnoreError` (0), `ReportAndContinue` (1) и `ReportAndStop` (2). Значение по умолчанию этого свойства — `IgnoreError` (0).|  
|KeyErrorAction|Integer (перечисление)|При UseDefaultConfiguration `False`, значение, указывающее способ обработки ошибок ключа. Допустимые значения — `ConvertToUnknown` (0) и `DiscardRecord` (1). Значение по умолчанию этого свойства — `ConvertToUnknown` (0).|  
|KeyErrorLimit|Целочисленный|При UseDefaultConfiguration `False`, верхний предел ошибок ключей, которые включены.|  
|KeyErrorLimitAction|Integer (перечисление)|При UseDefaultConfiguration `False`, значение, указывающее действие, выполняемое при `KeyErrorLimit` достигается. Возможными значениями являются `StopLogging` (1) и `StopProcessing` (0). Значение по умолчанию этого свойства — `StopProcessing` (0).|  
|KeyErrorLogFile|String|При UseDefaultConfiguration `False`, путь и имя файла журнала ошибок.|  
|KeyNotFound|Integer (перечисление)|При UseDefaultConfiguration `False`, значение, указывающее, как обрабатывать ошибки отсутствия ключа. Возможными значениями являются `IgnoreError` (0), `ReportAndContinue` (1) и `ReportAndStop` (2). Значение по умолчанию этого свойства — `IgnoreError` (0).|  
|NullKeyConvertedToUnknown|Integer (перечисление)|При UseDefaultConfiguration `False`, значение, указывающее, как обрабатывать ключи null преобразован в значение unknown. Возможными значениями являются `IgnoreError` (0), `ReportAndContinue` (1) и `ReportAndStop` (2). Значение по умолчанию этого свойства — `IgnoreError` (0).|  
|NullKeyNotAllowed|Integer (перечисление)|При UseDefaultConfiguration `False`, значение, указывающее, как обрабатывать запрещенные значения NULL. Возможными значениями являются `IgnoreError` (0), `ReportAndContinue` (1) и `ReportAndStop` (2). Значение по умолчанию этого свойства — `IgnoreError` (0).|  
|ProcessType|Integer (перечисление)|Тип обработки измерений, используемый преобразованием. Допустимые значения — `ProcessAdd` (1) (добавочное), `ProcessFull` (0) и `ProcessUpdate` (2).|  
|UseDefaultConfiguration|Логическое значение|Значение, указывающее, используется ли преобразованием конфигурация ошибок по умолчанию. Если это свойство имеет `False`, в преобразование включаются сведения об обработке ошибок.|  
  
 Ввод и входные столбцы назначения «Обработка измерения» не обладают пользовательскими свойствами.  
  
 Дополнительные сведения см. в разделе [Dimension Processing Destination](dimension-processing-destination.md).  
  
## <a name="see-also"></a>См. также  
 [Common Properties](../common-properties.md)  
  
  