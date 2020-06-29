---
title: Пользовательские свойства назначения "Обработка секций" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3eac4413-0c90-4b06-8f7e-d0d72f4d869d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 04d5f9a669fbccc798698914c919e63d90e04591
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85431601"
---
# <a name="partition-processing-destination-custom-properties"></a>Пользовательские свойства назначения «Обработка секций»
  Назначение «Обработка секций» обладает как пользовательскими свойствами, так и свойствами, общими для всех компонентов потока данных.  
  
 В следующей таблице описаны пользовательские свойства назначения «Обработка секций». Все свойства доступны для чтения и записи.  
  
|Свойство|Тип данных|Description|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|Строка подключения к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или проекту служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|KeyDuplicate|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет `False` значение, оно указывает, как обрабатывались ошибки повторяющихся ключей. Допустимые значения: `IgnoreError` (0), `ReportAndContinue` (1) и `ReportAndStop` (2). По умолчанию это свойство имеет значение `IgnoreError` (0).|  
|KeyErrorAction|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет `False` значение, оно указывает, как обрабатывались ошибки ключа. Допустимые значения — `ConvertToUnknown` (0) и `DiscardRecord` (1). По умолчанию это свойство имеет значение `ConvertToUnknown` (0).|  
|KeyErrorLimit|Целое число|Если свойство UseDefaultConfiguration имеет значение `False` , то верхний предел разрешенных ошибок ключа.|  
|KeyErrorLimitAction|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет `False` значение, оно указывает действие, которое необходимо выполнить при `KeyErrorLimit` достижении. Возможные значения: `StopLogging` (1) и `StopProcessing` (0). По умолчанию это свойство имеет значение `StopProcessing` (0).|  
|KeyErrorLogFile|String|Если свойство UseDefaultConfiguration имеет значение `False` , то путь и имя файла журнала ошибок.|  
|KeyNotFound|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет `False` значение, оно указывает, как обрабатывались ошибки с отсутствующим ключом. Допустимые значения: `IgnoreError` (0), `ReportAndContinue` (1) и `ReportAndStop` (2). Значение по умолчанию этого свойства равно `ReportAndContinue` (1).|  
|NullKeyConvertedToUnknown|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет `False` значение, оно указывает, как обрабатывались ключи null, преобразованные в неизвестное значение. Допустимые значения: `IgnoreError` (0), `ReportAndContinue` (1) и `ReportAndStop` (2). По умолчанию это свойство имеет значение `IgnoreError` (0).|  
|NullKeyNotAllowed|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет `False` значение, то оно указывает, как обработано запрещенные значения NULL. Допустимые значения: `IgnoreError` (0), `ReportAndContinue` (1) и `ReportAndStop` (2). Значение по умолчанию этого свойства равно `ReportAndContinue` (1).|  
|ProcessType|Integer (перечисление)|Тип обработки секций, используемый преобразованием. Допустимые значения — `ProcessAdd` (1) (добавочное), `ProcessFull` (0) и `ProcessUpdate` (2).|  
|UseDefaultConfiguration|Логическое|Значение, указывающее, используется ли преобразованием конфигурация ошибок по умолчанию. Если это свойство имеет значение `False` , то преобразование использует значения пользовательских свойств обработки ошибок, перечисленных в этой таблице, включая KeyDuplicate, KeyErrorAction и т. д.|  
  
 Ввод и входные столбцы назначения «Обработка секций» не обладают пользовательскими свойствами.  
  
 Дополнительные сведения см. в статье [Partition Processing Destination](partition-processing-destination.md).  
  
## <a name="see-also"></a>См. также:  
 [Общие свойства](../common-properties.md)  
  
  
