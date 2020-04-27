---
title: Пользовательские свойства назначения "Обработка измерений" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9700f663-53f2-49b6-b1ef-92c7b752d6a1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b63e508f87b9766507c541a7ed81e42466bbd1e8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62827367"
---
# <a name="dimension-processing-destination-custom-properies"></a>Пользовательские свойства назначения «Обработка измерений»
  Назначение «Обработка измерений» обладает как пользовательскими свойствами, так и свойствами, общими для всех компонентов потока данных.  
  
 В следующей таблице описаны пользовательские свойства назначения «Обработка измерений». Все свойства доступны для чтения и записи.  
  
|Свойство|Тип данных|Description|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|Строка соединения с экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или с проектом служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|KeyDuplicate|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет `False`значение, оно указывает, как обрабатывались ошибки повторяющихся ключей. Допустимые значения: `IgnoreError` (0), `ReportAndContinue` (1) и `ReportAndStop` (2). По умолчанию это свойство имеет значение `IgnoreError` (0).|  
|KeyErrorAction|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет `False`значение, оно указывает, как обрабатывается ошибка ключа. Допустимые значения — `ConvertToUnknown` (0) и `DiscardRecord` (1). По умолчанию это свойство имеет значение `ConvertToUnknown` (0).|  
|KeyErrorLimit|Целое число|Если свойство UseDefaultConfiguration имеет `False`значение, то верхний предел ошибок ключа включен.|  
|KeyErrorLimitAction|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет `False`значение, оно указывает действие, которое необходимо выполнить при `KeyErrorLimit` достижении. Возможные значения: `StopLogging` (1) и `StopProcessing` (0). По умолчанию это свойство имеет значение `StopProcessing` (0).|  
|KeyErrorLogFile|String|Если свойство UseDefaultConfiguration имеет `False`значение, то путь и имя файла журнала ошибок.|  
|KeyNotFound|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет `False`значение, оно указывает, как обрабатывались ошибки с отсутствующим ключом. Допустимые значения: `IgnoreError` (0), `ReportAndContinue` (1) и `ReportAndStop` (2). По умолчанию это свойство имеет значение `IgnoreError` (0).|  
|NullKeyConvertedToUnknown|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет `False`значение, оно указывает, как обрабатывались ключи null, преобразованные в неизвестное значение. Допустимые значения: `IgnoreError` (0), `ReportAndContinue` (1) и `ReportAndStop` (2). По умолчанию это свойство имеет значение `IgnoreError` (0).|  
|NullKeyNotAllowed|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет `False`значение, то оно указывает, как обработано запрещенные значения NULL. Допустимые значения: `IgnoreError` (0), `ReportAndContinue` (1) и `ReportAndStop` (2). По умолчанию это свойство имеет значение `IgnoreError` (0).|  
|ProcessType|Integer (перечисление)|Тип обработки измерений, используемый преобразованием. Допустимые значения — `ProcessAdd` (1) (добавочное), `ProcessFull` (0) и `ProcessUpdate` (2).|  
|UseDefaultConfiguration|Логическое|Значение, указывающее, используется ли преобразованием конфигурация ошибок по умолчанию. Если это свойство принимает значение `False`, в преобразование включаются сведения об обработке ошибок.|  
  
 Ввод и входные столбцы назначения «Обработка измерения» не обладают пользовательскими свойствами.  
  
 Дополнительные сведения см. в разделе [Dimension Processing Destination](dimension-processing-destination.md).  
  
## <a name="see-also"></a>См. также:  
 [Общие свойства](../common-properties.md)  
  
  
