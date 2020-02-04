---
title: Предотвращение использования недопустимых запросов | Документы Майкрософт
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-exception-handling
ms.topic: reference
helpviewer_keywords:
- invalid requests [Reporting Services]
- exceptions [Reporting Services], invalid requests
- valid requests [Reporting Services]
ms.assetid: 4a4a2d97-4c10-43a9-8298-ef5a820ea549
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 219fc1883f395e56f1fd73af32e95ea066df28b7
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "62992217"
---
# <a name="preventing-invalid-requests"></a>Предотвращение недопустимых запросов
  Возникновение некоторых типов исключений можно предотвратить, проведя анализ потока работы приложения и убедившись в том, что все запросы, направляемые на сервер отчетов, являются допустимыми. Например, в приложениях, предоставляющих пользователям возможность добавить или обновить имя отчета, источник данных или другие параметры сервера отчетов, необходимо проверять текст, вводимый пользователем. Перед отправкой запроса на сервер отчетов следует всегда проверять, нет ли в нем зарезервированных символов. Чтобы предупредить пользователя о том, что он не выполнил необходимых условий для отправки запросов на сервер отчетов, используйте в коде условные операторы **if** или другие логические конструкции.  
  
 В следующем упрощенном примере на языке C# при попытке создать отчет с именем, содержащим символ косой черты (/), пользователи получают понятное сообщение об ошибке.  
  
```  
// C#  
private void PublishReport()  
{  
   int index;  
   string reservedChar;  
   string message;  
  
   // Check the text value of the name text box for "/",  
   // a reserved character  
   index = nameTextBox.Text.IndexOf(@"/");  
  
   if ( index != -1) // The text contains the character  
   {  
      reservedChar = nameTextBox.Text.Substring(index, 1);  
      // Build a user-friendly error message  
      message = "The name of the report cannot contain the reserved character " +  
         "\"" + reservedChar + "\". " +  
         "Please enter a valid name for the report. " +  
         "For more information about reserved characters, " +  
         "see the help documentation";  
  
      MessageBox.Show(message, "Invalid Input Error");  
   }  
   else // Publish the report  
   {  
      Byte[] definition = null;  
      Warning[] warnings = {};  
      string name = nameTextBox.Text;  
  
      FileStream stream = File.OpenRead("MyReport.rdl");  
      definition = new Byte[stream.Length];  
      stream.Read(definition, 0, (int) stream.Length);  
      stream.Close();  
      // Create report with user-defined name  
      rs.CreateCatalogItem("Report", name, "/Samples", false, definition, null, out warnings);  
      MessageBox.Show("Report: {0} created successfully", name);  
   }  
}  
```  
  
 Дополнительные сведения о типах ошибок, которые могут быть устранены до отправки запросов на сервер отчетов, см. в разделе [Таблица ошибок SoapException](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/soapexception-errors-table.md). Дополнительные сведения об усовершенствовании предыдущего примера с помощью блоков try и catch см. в разделе [Использование блоков Try-Catch](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-try-and-catch-blocks.md).  
  
## <a name="see-also"></a>См. также:  
 [Введение в обработку исключений в службах Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Класс SoapException в службах Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  
