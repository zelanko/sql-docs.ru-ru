---
title: Пользовательские свойства назначения "Обработка секций" | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3eac4413-0c90-4b06-8f7e-d0d72f4d869d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0f2fc4b5407d1a538696de30f62cef2c779bfa86
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47823362"
---
# <a name="partition-processing-destination-custom-properties"></a>Пользовательские свойства назначения «Обработка секций»
  Назначение «Обработка секций» обладает как пользовательскими свойствами, так и свойствами, общими для всех компонентов потока данных.  
  
 В следующей таблице описаны пользовательские свойства назначения «Обработка секций». Все свойства доступны для чтения и записи.  
  
|Свойство|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|Строка подключения к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или проекту служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|KeyDuplicate|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение **False**, оно показывает, как обрабатывать ошибки повторения ключа. Возможные значения: **IgnoreError** (0), **ReportAndContinue** (1) и **ReportAndStop** (2). Значением по умолчанию для этого свойства является **IgnoreError** (0).|  
|KeyErrorAction|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение **False**, оно показывает, как обрабатывать ошибки ключа. Возможные значения: **ConvertToUnknown** (0) и **DiscardRecord** (1). Значением по умолчанию для этого свойства является **ConvertToUnknown** (0).|  
|KeyErrorLimit|Целочисленный|Если свойство UseDefaultConfiguration имеет значение **False**, значит, включено максимально разрешенное количество ошибок ключа.|  
|KeyErrorLimitAction|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение **False**, оно устанавливает действие при достижении предела **KeyErrorLimit** . Возможные значения: **StopLogging** (1) и **StopProcessing** (0). Значением по умолчанию для этого свойства является **StopProcessing** (0).|  
|KeyErrorLogFile|String|Если свойство UseDefaultConfiguration имеет значение **False**, оно представляет собой путь и имя файла журнала ошибок.|  
|KeyNotFound|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение **False**, оно показывает, как обрабатывать ошибки отсутствующего ключа. Возможные значения: **IgnoreError** (0), **ReportAndContinue** (1) и **ReportAndStop** (2). Значение этого свойства по умолчанию равно **ReportAndContinue** (1).|  
|NullKeyConvertedToUnknown|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение **False**, оно показывает, как обрабатывать ключи NULL, преобразованные в значение Unknown. Возможные значения: **IgnoreError** (0), **ReportAndContinue** (1) и **ReportAndStop** (2). Значением по умолчанию для этого свойства является **IgnoreError** (0).|  
|NullKeyNotAllowed|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение **False**, оно показывает, как обрабатывать запрещенные значения NULL. Возможные значения: **IgnoreError** (0), **ReportAndContinue** (1) и **ReportAndStop** (2). Значение этого свойства по умолчанию равно **ReportAndContinue** (1).|  
|ProcessType|Integer (перечисление)|Тип обработки секций, используемый преобразованием. Возможные значения: **ProcessAdd** (1) (добавочное), **ProcessFull** (0) и **ProcessUpdate** (2).|  
|UseDefaultConfiguration|Логическое значение|Значение, указывающее, используется ли преобразованием конфигурация ошибок по умолчанию. Если это свойство принимает значение **False**, то преобразование использует значения настраиваемых свойств обработки ошибок, приведенных в этой таблице, в том числе KeyDuplicate, KeyErrorAction и др.|  
  
 Ввод и входные столбцы назначения «Обработка секций» не обладают пользовательскими свойствами.  
  
 Дополнительные сведения см. в статье [Partition Processing Destination](../../integration-services/data-flow/partition-processing-destination.md).  
  
## <a name="see-also"></a>См. также:  
 [Common Properties](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
