---
title: Обработка ошибок в API TOM (Analysis Services AMO-TOM) | Документы Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ec44daa0-a90e-42ad-b70d-6a7a7a4e4b7b
caps.latest.revision: 4
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d5b023664cb70997b9aee688178a5c72eb2c06e0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="handling-errors-in-the-tom-api-analysis-services-amo-tom"></a>Обработка ошибок в API TOM (Analysis Services AMO-TOM)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
Распространенной практикой для управляемых библиотек, как объекты управления Analysis Services (AMO) табличной модели объектов (TOM) заключается в использовании исключений как механизм для создания отчетов условия ошибки для пользователя.  

При обнаружении ошибки в TOM объектов AMO, помимо создания несколько стандартных исключений .NET таких как **ArgumentException** и **InvalidOperationException**, TOM также можно создать несколько TOM конкретных исключений.  

TOM исключения наследуются от [класс AmoException](http://msdn.microsoft.com/library/microsoft.analysisservices.amoexception.aspx), охватывающие оба исключения конкретного TOM и AMO. 

Для демонстрации обработки исключений в том, давайте рассмотрим один из наиболее распространенных исключения, которые является [OperationException класса](http://msdn.microsoft.com/library/microsoft.analysisservices.operationexception.aspx).

**OperationException** возникает, когда пользователь инициирует операцию на сервере служб Analysis Services и серверу не удается выполнить операцию, был недопустимым, действие, либо из-за другой ошибки внутренними или внешними. 

Созданное исключение ** OperationException ** объект будет содержать список ошибок XMLA, возвращенные сервером. 

Обратите внимание, что сервер не допускает изменения, которые являются недопустимыми. В этом случае необходимо восстановить **модель** дерева обратно в последнее удачное состояние с помощью [UndoLocalChanges метод](http://msdn.microsoft.com/library/microsoft.analysisservices.tabular.model.undolocalchanges.aspx)исправьте модели и отправить повторно. 

## <a name="code-example-handle-exceptions"></a>Пример кода: обработки исключений 
 
```
 try 
 { 
  // Change the Model, for example create a table. 
  // … 
   model.saveChanges(); 
 } 
  catch(operationException ex) 
 { 
  foreach(XmlaError err in ex.Results.OfType<XmlaError>().cast<XmlaError>()) 
  { 
   Console.WriteLine(“Error returned from the server:” + err.Messsage ); 
  } 
 } 
```

## <a name="next-steps"></a>Следующие шаги

Ниже перечислены другие соответствующие исключения.

- [Класс TomInternalException](http://msdn.microsoft.com/library/microsoft.analysisservices.tabular.tominternalexception.aspx)
- [Класс TomValidationException](http://msdn.microsoft.com/library/microsoft.analysisservices.tabular.tomvalidationexception.aspx)
- [Класс JsonSerializationException](http://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_JsonSerializationException.htm)
