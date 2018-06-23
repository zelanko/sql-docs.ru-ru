---
title: Пользовательские свойства назначения "Обработка секций" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3eac4413-0c90-4b06-8f7e-d0d72f4d869d
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 2724682cebfcae1e5c6a14b9c7cd815c96ad4a7c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101573"
---
# <a name="partition-processing-destination-custom-properties"></a>Пользовательские свойства назначения «Обработка секций»
  Назначение «Обработка секций» обладает как пользовательскими свойствами, так и свойствами, общими для всех компонентов потока данных.  
  
 В следующей таблице описаны пользовательские свойства назначения «Обработка секций». Все свойства доступны для чтения и записи.  
  
|Свойство|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|Строка подключения к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или проекту служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|KeyDuplicate|Integer (перечисление)|При UseDefaultConfiguration `False`, значение, указывающее, как обрабатывать ошибки повторения ключа. Возможными значениями являются `IgnoreError` (0), `ReportAndContinue` (1) и `ReportAndStop` (2). Значение по умолчанию этого свойства — `IgnoreError` (0).|  
|KeyErrorAction|Integer (перечисление)|При UseDefaultConfiguration `False`, значение, указывающее, как обрабатывать ошибки ключа. Допустимые значения — `ConvertToUnknown` (0) и `DiscardRecord` (1). Значение по умолчанию этого свойства — `ConvertToUnknown` (0).|  
|KeyErrorLimit|Целочисленный|При UseDefaultConfiguration `False`, максимальное разрешенное количество ошибок ключа.|  
|KeyErrorLimitAction|Integer (перечисление)|При UseDefaultConfiguration `False`, значение, указывающее действие, выполняемое при `KeyErrorLimit` достигается. Возможными значениями являются `StopLogging` (1) и `StopProcessing` (0). Значение по умолчанию этого свойства — `StopProcessing` (0).|  
|KeyErrorLogFile|String|При UseDefaultConfiguration `False`, путь и имя файла журнала ошибок.|  
|KeyNotFound|Integer (перечисление)|При UseDefaultConfiguration `False`, значение, указывающее, как обрабатывать ошибки отсутствия ключа. Возможными значениями являются `IgnoreError` (0), `ReportAndContinue` (1) и `ReportAndStop` (2). Значение по умолчанию этого свойства — `ReportAndContinue` (1).|  
|NullKeyConvertedToUnknown|Integer (перечисление)|При UseDefaultConfiguration `False`, значение, указывающее, как обрабатывать ключи null преобразован в значение Unknown. Возможными значениями являются `IgnoreError` (0), `ReportAndContinue` (1) и `ReportAndStop` (2). Значение по умолчанию этого свойства — `IgnoreError` (0).|  
|NullKeyNotAllowed|Integer (перечисление)|При UseDefaultConfiguration `False`, значение, указывающее, как обрабатывать запрещенные значения NULL. Возможными значениями являются `IgnoreError` (0), `ReportAndContinue` (1) и `ReportAndStop` (2). Значение по умолчанию этого свойства — `ReportAndContinue` (1).|  
|ProcessType|Integer (перечисление)|Тип обработки секций, используемый преобразованием. Допустимые значения — `ProcessAdd` (1) (добавочное), `ProcessFull` (0) и `ProcessUpdate` (2).|  
|UseDefaultConfiguration|Логическое значение|Значение, указывающее, используется ли преобразованием конфигурация ошибок по умолчанию. Если это свойство имеет `False`, преобразование использует значения пользовательских свойств обработки ошибок, перечисленных в этой таблице, включая KeyDuplicate, KeyErrorAction и т. д.|  
  
 Ввод и входные столбцы назначения «Обработка секций» не обладают пользовательскими свойствами.  
  
 Дополнительные сведения см. в статье [Partition Processing Destination](partition-processing-destination.md).  
  
## <a name="see-also"></a>См. также  
 [Common Properties](../common-properties.md)  
  
  