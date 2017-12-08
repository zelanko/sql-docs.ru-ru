---
title: "Обработка ошибок в API TOM (Analysis Services AMO-TOM) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ec44daa0-a90e-42ad-b70d-6a7a7a4e4b7b
caps.latest.revision: "4"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 30d824c54359a7f7db0d57f7a4a7922329a0e89b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="handling-errors-in-the-tom-api-analysis-services-amo-tom"></a>Обработка ошибок в API TOM (Analysis Services AMO-TOM)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

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
