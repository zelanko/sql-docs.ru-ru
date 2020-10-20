---
description: Пользовательские свойства назначения «Обработка секций»
title: Пользовательские свойства назначения "Обработка секций" | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3eac4413-0c90-4b06-8f7e-d0d72f4d869d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a4575b22bc7321322fbb51acdabded7a7039473d
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92195346"
---
# <a name="partition-processing-destination-custom-properties"></a>Пользовательские свойства назначения «Обработка секций»

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Назначение «Обработка секций» обладает как пользовательскими свойствами, так и свойствами, общими для всех компонентов потока данных.  
  
 В следующей таблице описаны пользовательские свойства назначения «Обработка секций». Все свойства доступны для чтения и записи.  
  
|Свойство|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|ASConnectionString|Строка|Строка подключения к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или проекту служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|KeyDuplicate|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение **False**, оно показывает, как обрабатывать ошибки повторения ключа. Возможные значения: **IgnoreError** (0), **ReportAndContinue** (1) и **ReportAndStop** (2). Значением по умолчанию для этого свойства является **IgnoreError** (0).|  
|KeyErrorAction|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение **False**, оно показывает, как обрабатывать ошибки ключа. Возможные значения: **ConvertToUnknown** (0) и **DiscardRecord** (1). Значением по умолчанию для этого свойства является **ConvertToUnknown** (0).|  
|KeyErrorLimit|Целое число|Если свойство UseDefaultConfiguration имеет значение **False**, значит, включено максимально разрешенное количество ошибок ключа.|  
|KeyErrorLimitAction|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение **False**, оно устанавливает действие при достижении предела **KeyErrorLimit** . Возможные значения: **StopLogging** (1) и **StopProcessing** (0). Значением по умолчанию для этого свойства является **StopProcessing** (0).|  
|KeyErrorLogFile|Строка|Если свойство UseDefaultConfiguration имеет значение **False**, оно представляет собой путь и имя файла журнала ошибок.|  
|KeyNotFound|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение **False**, оно показывает, как обрабатывать ошибки отсутствующего ключа. Возможные значения: **IgnoreError** (0), **ReportAndContinue** (1) и **ReportAndStop** (2). Значение этого свойства по умолчанию равно **ReportAndContinue** (1).|  
|NullKeyConvertedToUnknown|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение **False**, оно показывает, как обрабатывать ключи NULL, преобразованные в значение Unknown. Возможные значения: **IgnoreError** (0), **ReportAndContinue** (1) и **ReportAndStop** (2). Значением по умолчанию для этого свойства является **IgnoreError** (0).|  
|NullKeyNotAllowed|Integer (перечисление)|Если свойство UseDefaultConfiguration имеет значение **False**, оно показывает, как обрабатывать запрещенные значения NULL. Возможные значения: **IgnoreError** (0), **ReportAndContinue** (1) и **ReportAndStop** (2). Значение этого свойства по умолчанию равно **ReportAndContinue** (1).|  
|ProcessType|Integer (перечисление)|Тип обработки секций, используемый преобразованием. Возможные значения: **ProcessAdd** (1) (добавочное), **ProcessFull** (0) и **ProcessUpdate** (2).|  
|UseDefaultConfiguration|Логическое значение|Значение, указывающее, используется ли преобразованием конфигурация ошибок по умолчанию. Если это свойство принимает значение **False**, то преобразование использует значения настраиваемых свойств обработки ошибок, приведенных в этой таблице, в том числе KeyDuplicate, KeyErrorAction и др.|  
  
 Ввод и входные столбцы назначения «Обработка секций» не обладают пользовательскими свойствами.  
  
 Дополнительные сведения см. в статье [Partition Processing Destination](../../integration-services/data-flow/partition-processing-destination.md).  
  
## <a name="see-also"></a>См. также  
 [Общие свойства](./set-the-properties-of-a-data-flow-component.md)  
  
